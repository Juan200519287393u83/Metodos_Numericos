<div align="center">

#  🎯 Tema 6: Método de Pasos Múltiples

</div>

---

## 📚 Introducción

El método de pasos múltiples es una técnica numérica utilizada para resolver ecuaciones diferenciales ordinarias que, a diferencia de los métodos de un solo paso, aprovecha la información de varios puntos anteriores para calcular el valor siguiente de la solución. Esta estrategia permite mejorar la precisión sin realizar evaluaciones adicionales de la función derivada, lo que puede traducirse en un mejor rendimiento computacional.

Entre los métodos de pasos múltiples más conocidos están los métodos de Adams-Bashforth (explícito) y Adams-Moulton (implícito). Estos métodos requieren una fase inicial de arranque, generalmente con un método de un solo paso como Runge-Kutta, para obtener los primeros valores necesarios. Una vez establecidos estos valores, el método puede avanzar reutilizando evaluaciones previas.

La principal ventaja de estos métodos es la eficiencia en términos de precisión por evaluación de función, haciéndolos ideales para integraciones numéricas a largo plazo. Sin embargo, requieren manejar múltiples condiciones iniciales y son más complejos de implementar que métodos de un solo paso.

---

## ⚖️ Ventajas y Desventajas

| Ventajas                                                          | Desventajas                                                                    |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Mayor eficiencia computacional al reutilizar evaluaciones previas | Requiere método de arranque para primeros valores                              |
| Alta precisión para ecuaciones con comportamiento suave           | Implementación más compleja que métodos de un solo paso                        |
| Ideal para integraciones numéricas de largo plazo                 | Sensible a errores acumulados si paso o condiciones iniciales no son adecuadas |

---

## 🧩 Pseudocódigo

```text
Inicio
  Función f(x, y)
    Retornar -2 * x * y
  Fin Función

  Definir a, b, h, n, x[], y[]
  a = 0.0
  b = 1.0
  h = 0.2
  n = 5
  y[0] = 1.0

  Para i = 0 hasta n
    x[i] = a + i * h
  Fin Para

  // Primer paso con Euler
  y[1] = y[0] + h * f(x[0], y[0])

  // Método Adams-Bashforth de 2 pasos
  Para i = 1 hasta n-1
    y[i+1] = y[i] + (h / 2) * (3 * f(x[i], y[i]) - f(x[i-1], y[i-1]))
  Fin Para

  Para i = 0 hasta n
    Imprimir "x = ", x[i], ", y = ", y[i]
  Fin Para
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseAdamsBashforth {
    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static void main(String[] args) {
        double a = 0.0, b = 1.0, h = 0.2;
        int n = 5;
        double[] x = new double[n + 1];
        double[] y = new double[n + 1];
        y[0] = 1.0;

        for (int i = 0; i <= n; i++) {
            x[i] = a + i * h;
        }

        // Primer paso con Euler
        y[1] = y[0] + h * f(x[0], y[0]);

        // Adams-Bashforth de 2 pasos
        for (int i = 1; i < n; i++) {
            y[i + 1] = y[i] + (h / 2) * (3 * f(x[i], y[i]) - f(x[i - 1], y[i - 1]));
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
public class AdamsBashforth {
    public static class SolutionPoint {
        public final double x;
        public final double y;

        public SolutionPoint(double x, double y) {
            this.x = x;
            this.y = y;
        }
    }

    public static SolutionPoint[] solveAdamsBashforth(double a, double b, double h, double y0) {
        if (a >= b || h <= 0) {
            throw new IllegalArgumentException("El intervalo debe ser a < b y h debe ser positivo");
        }

        int n = (int) Math.ceil((b - a) / h);
        if (n < 2) {
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
        // Primer paso con Euler
        y[1] = y[0] + h * f(x[0], y[0]);

        // Adams-Bashforth de 2 pasos
        for (int i = 1; i < n; i++) {
            y[i + 1] = y[i] + (h / 2) * (3 * f(x[i], y[i]) - f(x[i - 1], y[i - 1]));
        }

        for (int i = 0; i <= n; i++) {
            solution[i] = new SolutionPoint(x[i], y[i]);
        }

        return solution;
    }

    public static double f(double x, double y) {
        return -2 * x * y;
    }

    public static void main(String[] args) {
        double a = 0.0, b = 1.0, h = 0.2, y0 = 1.0;

        try {
            SolutionPoint[] solution = solveAdamsBashforth(a, b, h, y0);
            System.out.printf("Método de Adams-Bashforth (2 pasos):%n");
            System.out.printf("Ecuación diferencial: dy/dx = -2xy%n");
            System.out.printf("Condición inicial: y(%.1f) = %.3f%n", a, y0);
            System.out.printf("Intervalo: [%.1f, %.1f], h = %.1f%n", a, b, h);
            System.out.println("Resultados:");
            for (SolutionPoint point : solution) {
                System.out.printf("x = %.1f, y = %.3f%n", point.x, point.y);
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
Método de Adams-Bashforth (2 pasos):
Ecuación diferencial: dy/dx = -2xy
Condición inicial: y(0.0) = 1.000
Intervalo: [0.0, 1.0], h = 0.2
Resultados:
x = 0.0, y = 1.000
x = 0.2, y = 1.000
x = 0.4, y = 0.960
x = 0.6, y = 0.862
x = 0.8, y = 0.711
x = 1.0, y = 0.574
```

---

## 🔙 Navegación

[⬅️ Regresar a T6 - Solución de Ecuaciones Diferenciales](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T6%20-%20Soluci%C3%B3n%20de%20Ecuaciones%20Diferenciales/Introducci%C3%B3n%20a%20la%20Soluci%C3%B3n%20de%20Ecuaciones%20Diferenciales.md)

---
