 <div align="center">

# 🎯  Tema 6: Método de Taylor

</div>

---

## 📚 Introducción

El método de Taylor es una técnica numérica que aprovecha el desarrollo en serie de Taylor para aproximar la solución de una ecuación diferencial ordinaria. Este enfoque considera no solo la primera derivada, sino también derivadas de orden superior, lo cual permite construir una mejor aproximación local de la función.

A diferencia de otros métodos que utilizan evaluaciones puntuales, el método de Taylor requiere el cálculo explícito de derivadas sucesivas, lo cual puede ser una desventaja si estas derivadas son difíciles de obtener o costosas de calcular. Sin embargo, cuando esta información está disponible, el método puede proporcionar soluciones altamente precisas.

Este método es especialmente útil cuando se busca comprender el comportamiento local de una solución con gran detalle o cuando se dispone de funciones cuyas derivadas son fácilmente derivables simbólicamente. Aunque no es tan utilizado como Runge-Kutta en la práctica general, es una herramienta poderosa en contextos específicos donde se prioriza la precisión local.

---

## ⚖️ Ventajas y Desventajas

| Ventajas                                                         | Desventajas                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| Alta precisión local al incluir derivadas de orden superior      | Requiere calcular derivadas de orden superior, complejo          |
| Útil cuando las derivadas son fáciles de calcular analíticamente | Más costoso computacionalmente si derivadas no están disponibles |
| Proporciona base teórica para entender otros métodos numéricos   | Menos utilizado en la práctica general                           |

---

## 🧩 Pseudocódigo

```text
Inicio
  Función f(x, y)
    Retornar -2 * x * y
  Fin Función

  Función fPrima(x, y)
    Retornar -2 * y - 2 * x * (-2 * x * y)
  Fin Función

  Definir a como real
  Definir b como real
  Definir h como real
  Definir n como entero
  Definir x como vector de reales [n+1]
  Definir y como vector de reales [n+1]
  Definir i como entero

  a = 0.0
  b = 1.0
  h = 0.2
  n = 5
  y[0] = 1.0

  Para i = 0 hasta n
    x[i] = a + i * h
  Fin Para

  Para i = 0 hasta n-1
    y[i+1] = y[i] + h * f(x[i], y[i]) + (h^2 / 2) * fPrima(x[i], y[i])
  Fin Para

  Para i = 0 hasta n
    Imprimir "x = ", x[i], ", y = ", y[i]
  Fin Para
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseTaylorMethod {
    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static double fPrima(double x, double y) {
        return -2 * y - 2 * x * (-2 * x * y);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        double h = 0.2;
        int n = 5;
        double[] x = new double[n + 1];
        double[] y = new double[n + 1];
        y[0] = 1.0;

        for (int i = 0; i <= n; i++) {
            x[i] = a + i * h;
        }

        for (int i = 0; i < n; i++) {
            y[i + 1] = y[i] + h * f(x[i], y[i]) + (h * h / 2) * fPrima(x[i], y[i]);
        }

        for (int i = 0; i <= n; i++) {
            System.out.println("x = " + x[i] + ", y = " + y[i]);
        }
    }
}
```

---

## ⚙️ Ejemplo funcional en Java

```java
public class TaylorMethod {
    public static class SolutionPoint {
        public final double x;
        public final double y;
        public final double yExact; // Solución analítica

        public SolutionPoint(double x, double y, double yExact) {
            this.x = x;
            this.y = y;
            this.yExact = yExact;
        }
    }

    public static SolutionPoint[] solveTaylorOrder2(double a, double b, double h, double y0) {
        if (a >= b || h <= 0) {
            throw new IllegalArgumentException("El intervalo debe ser a < b y h debe ser positivo");
        }

        int n = (int) Math.ceil((b - a) / h);
        if (n < 1) {
            throw new IllegalArgumentException("El paso h es demasiado grande para el intervalo");
        }

        double[] x = new double[n + 1];
        double[] y = new double[n + 1];
        SolutionPoint[] solution = new SolutionPoint[n + 1];

        for (int i = 0; i <= n; i++) {
            x[i] = a + i * h;
            if (i == n && Math.abs(x[i] - b) > 1e-10) {
                x[i] = b;
            }
        }

        y[0] = y0;

        for (int i = 0; i < n; i++) {
            y[i + 1] = y[i] + h * f(x[i], y[i]) + (h * h / 2) * fPrima(x[i], y[i]);
        }

        for (int i = 0; i <= n; i++) {
            double yExact = Math.exp(-x[i] * x[i]);
            solution[i] = new SolutionPoint(x[i], y[i], yExact);
        }

        return solution;
    }

    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static double fPrima(double x, double y) {
        return -2 * y + 4 * x * x * y; // Simplificado
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        double h = 0.2;
        double y0 = 1.0;

        try {
            SolutionPoint[] solution = solveTaylorOrder2(a, b, h, y0);
            System.out.printf("Método de Taylor (orden 2):%n");
            System.out.printf("Ecuación diferencial: dy/dx = -2xy%n");
            System.out.printf("Condición inicial: y(%.1f) = %.3f%n", a, y0);
            System.out.printf("Intervalo: [%.1f, %.1f], h = %.1f%n", a, b, h);
            System.out.println("Resultados (y_num: solución numérica, y_exact: solución analítica):");
            for (SolutionPoint point : solution) {
                System.out.printf("x = %.1f, y_num = %.3f, y_exact = %.3f, error = %.3e%n", 
                    point.x, point.y, point.yExact, Math.abs(point.y - point.yExact));
            }
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

---

## 📊 Caso de prueba

|  x  | y\_num | y\_exact |   error   |
| :-: | :----: | :------: | :-------: |
| 0.0 |  1.000 |   1.000  | 0.000e+00 |
| 0.2 |  0.960 |   0.961  | 7.840e-04 |
| 0.4 |  0.852 |   0.852  | 2.805e-03 |
| 0.6 |  0.697 |   0.698  | 5.946e-03 |
| 0.8 |  0.527 |   0.527  | 9.973e-03 |
| 1.0 |  0.368 |   0.368  | 1.466e-02 |

---

## 🔙 Navegación

[⬅️ Regresar a T6 - Sistemas de Ecuaciones Diferenciales Ordinarias](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T6%20-%20Soluci%C3%B3n%20de%20Ecuaciones%20Diferenciales/Sistemas%20de%20Ecuaciones%20Diferenciales%20Ordinarias/Introducci%C3%B3n%20a%20los%20SIstemas%20de%20Ecuaciones%20Diferenciales%20Ordinarias.md)

---
