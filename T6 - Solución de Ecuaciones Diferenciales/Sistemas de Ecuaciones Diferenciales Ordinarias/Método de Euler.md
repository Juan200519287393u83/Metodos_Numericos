<div align="center">

#  🧮 Tema 6: Método de Euler

</div>

---

## 🔍 Introducción

El **método de Euler** es uno de los algoritmos más simples y fundamentales para la resolución numérica de ecuaciones diferenciales ordinarias (EDO). Se basa en aproximar la curva solución mediante segmentos de recta tangente, utilizando la derivada en un punto para predecir el siguiente valor de la función.

Aunque elemental, permite comprender conceptos básicos de análisis numérico aplicado a EDOs. Su principal ventaja es la facilidad de implementación, ideal para enseñanza y aprendizaje inicial. Sin embargo, usa una única evaluación de la derivada por paso, lo que limita su precisión, sobre todo en intervalos grandes o funciones complejas.

A pesar de sus limitaciones, es la base para desarrollar métodos más avanzados y se utiliza para ilustrar principios o como paso inicial en métodos multietapa.

---

## ⚖️ Ventajas y Desventajas

| Ventajas                                                    | Desventajas                                                      |
| ----------------------------------------------------------- | ---------------------------------------------------------------- |
| - Muy sencillo de implementar y entender.                   | - Baja precisión (error de orden $O(h)$).                        |
| - Solo una evaluación de la derivada por paso (ligero).     | - Puede ser inestable en ecuaciones rígidas o derivadas grandes. |
| - Útil para fines educativos y base para métodos avanzados. | - Acumula errores rápidamente en integraciones a largo plazo.    |

---

## 📝 Pseudocódigo

```text
Inicio
  Función f(x, y)
    Retornar -2 * x * y
  Fin Función

  Definir a, b, h, n, i
  Definir vectores x[n+1], y[n+1]

  a = 0.0; b = 1.0; h = 0.2; n = 5; y[0] = 1.0

  Para i = 0 hasta n
    x[i] = a + i * h
  Fin Para

  Para i = 0 hasta n-1
    y[i+1] = y[i] + h * f(x[i], y[i])
  Fin Para

  Para i = 0 hasta n
    Imprimir "x = ", x[i], ", y = ", y[i]
  Fin Para
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseEulerMethod {
    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static void main(String[] args) {
        double a = 0.0, b = 1.0, h = 0.2;
        int n = 5;
        double[] x = new double[n + 1];
        double[] y = new double[n + 1];
        y[0] = 1.0;

        for (int i = 0; i <= n; i++) x[i] = a + i * h;

        for (int i = 0; i < n; i++) y[i + 1] = y[i] + h * f(x[i], y[i]);

        for (int i = 0; i <= n; i++) System.out.println("x = " + x[i] + ", y = " + y[i]);
    }
}
```

---

## 🚀 Ejemplo funcional en Java

```java
public class EulerMethod {
    public static class SolutionPoint {
        public final double x, y;
        public SolutionPoint(double x, double y) {
            this.x = x; this.y = y;
        }
    }

    public static SolutionPoint[] solveEuler(double a, double b, double h, double y0) {
        if (a >= b || h <= 0) throw new IllegalArgumentException("El intervalo debe ser a < b y h positivo");

        int n = (int) Math.ceil((b - a) / h);
        if (n < 1) throw new IllegalArgumentException("Paso h demasiado grande para el intervalo");

        double[] x = new double[n + 1], y = new double[n + 1];
        SolutionPoint[] solution = new SolutionPoint[n + 1];

        for (int i = 0; i <= n; i++) {
            x[i] = a + i * h;
            if (i == n && Math.abs(x[i] - b) > 1e-10) x[i] = b;
        }

        y[0] = y0;
        for (int i = 0; i < n; i++) y[i + 1] = y[i] + h * f(x[i], y[i]);
        for (int i = 0; i <= n; i++) solution[i] = new SolutionPoint(x[i], y[i]);

        return solution;
    }

    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static void main(String[] args) {
        double a = 0.0, b = 1.0, h = 0.2, y0 = 1.0;

        try {
            SolutionPoint[] solution = solveEuler(a, b, h, y0);
            System.out.println("Método de Euler:");
            System.out.println("Ecuación diferencial: dy/dx = -2xy");
            System.out.printf("Condición inicial: y(%.1f) = %.3f%n", a, y0);
            System.out.printf("Intervalo: [%.1f, %.1f], h = %.1f%n", a, b, h);
            System.out.println("Resultados:");
            for (SolutionPoint p : solution) {
                System.out.printf("x = %.1f, y = %.3f%n", p.x, p.y);
            }
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

---

## 📊 Caso de prueba

```text
Método de Euler:
Ecuación diferencial: dy/dx = -2xy
Condición inicial: y(0.0) = 1.000
Intervalo: [0.0, 1.0], h = 0.2
Resultados:
x = 0.0, y = 1.000
x = 0.2, y = 1.000
x = 0.4, y = 0.960
x = 0.6, y = 0.846
x = 0.8, y = 0.677
x = 1.0, y = 0.488
```

---

<div align="center">

[⬅ Regresar a T6 - Sistemas de Ecuaciones Diferenciales Ordinarias](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T6%20-%20Soluci%C3%B3n%20de%20Ecuaciones%20Diferenciales/Sistemas%20de%20Ecuaciones%20Diferenciales%20Ordinarias/Introducci%C3%B3n%20a%20los%20SIstemas%20de%20Ecuaciones%20Diferenciales%20Ordinarias.md)

</div>
