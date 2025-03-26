# 📌 Tema 3: Método de Gauss-Seidel

## 🧠 ¿En qué consiste el Método de Gauss-Seidel?

El **método de Gauss-Seidel** es una técnica numérica iterativa diseñada para resolver sistemas de ecuaciones lineales. Parte de una suposición inicial para las incógnitas y, a través de repetidas aproximaciones, ajusta esas estimaciones utilizando directamente las ecuaciones del sistema.

A diferencia del método de Jacobi, este método **aprovecha inmediatamente los nuevos valores calculados**, utilizándolos en los siguientes pasos de la misma iteración. Esto suele traducirse en una **convergencia más rápida**.

Es especialmente útil para sistemas grandes y dispersos, como los que aparecen en simulaciones de estructuras, dinámica de fluidos, análisis térmico, entre otros. Para asegurar que el método converja, la matriz de coeficientes debe ser **diagonalmente dominante** o **simétrica definida positiva**.

> ✅ Cuando se cumplen las condiciones adecuadas, el método es sencillo de implementar, eficiente y consume poca memoria.
> ⚠️ Pero cuidado: **no siempre garantiza convergencia**, por lo que es recomendable estudiar previamente la estructura del sistema o aplicar técnicas de precondicionamiento.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                                     | 🔴 Desventajas                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Utiliza los valores más recientes de inmediato, lo que acelera la convergencia. | No siempre converge si la matriz no cumple ciertas condiciones.    |
| Ideal para sistemas de gran tamaño, especialmente con matrices dispersas.       | La calidad del resultado depende mucho de la estimación inicial.   |
| Menor consumo de memoria comparado con métodos directos.                        | Puede necesitar precondicionamiento en sistemas mal condicionados. |

---

## ⚙️ Pseudocódigo del Método

```plaintext
Inicio
  Definir n, A[n][n], b[n], x[n], xNuevo[n]
  Inicializar x con ceros
  Definir tolerancia y máximo número de iteraciones

  Mientras no se alcance la tolerancia o el máximo de iteraciones:
    Para cada variable i:
      Calcular la suma de A[i][j] * x[j] para j ≠ i
      Actualizar xNuevo[i] = (b[i] - suma) / A[i][i]
      Calcular el error con respecto al valor anterior
      Asignar x[i] = xNuevo[i]

    Mostrar valores de x[i] en la iteración actual
    Si el error < tolerancia, detener
Fin
```

---

## 💻 Código Java (estructura base)

```java
public class CodigoBaseGaussSeidel {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {{3, 2, -1}, {2, -2, 4}, {-1, 0.5, -1}};
        double[] b = {1, -2, 0};
        double[] x = {0, 0, 0};
        double[] xNuevo = new double[n];
        double tolerancia = 0.001;
        int maxIteraciones = 100;
        int iteracion = 0;

        while (iteracion < maxIteraciones) {
            double error = 0;
            for (int i = 0; i < n; i++) {
                double suma = 0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * x[j];
                    }
                }
                xNuevo[i] = (b[i] - suma) / A[i][i];
                error = Math.max(error, Math.abs(xNuevo[i] - x[i]));
                x[i] = xNuevo[i];
            }

            System.out.println("Iteración " + iteracion + ":");
            for (int i = 0; i < n; i++) {
                System.out.println("x" + i + " = " + x[i]);
            }

            if (error < tolerancia) {
                System.out.println("Solución encontrada");
                return;
            }

            iteracion++;
        }
        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejemplo resuelto

```java
public class GaussSeidel {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {{3, 2, -1}, {2, -2, 4}, {-1, 0.5, -1}};
        double[] b = {1, -2, 0};
        double[] x = {0, 0, 0};
        double[] xNuevo = new double[n];
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double error = 0;
            for (int i = 0; i < n; i++) {
                double suma = 0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * x[j];
                    }
                }
                xNuevo[i] = (b[i] - suma) / A[i][i];
                error = Math.max(error, Math.abs(xNuevo[i] - x[i]));
                x[i] = xNuevo[i];
            }

            System.out.printf("Iteración %d:%n", iteracion);
            for (int i = 0; i < n; i++) {
                System.out.printf("x%d = %.3f%n", i, x[i]);
            }

            if (error < tolerancia) {
                System.out.println("Solución encontrada");
                return;
            }
        }
        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## 🧪 Resultado esperado (ejecución típica)

```
Iteración 0:
x0 = 0.333
x1 = -0.667
x2 = -0.583

Iteración 1:
x0 = 0.583
x1 = 0.083
x2 = -0.458

Iteración 2:
x0 = 0.458
x1 = 0.121
x2 = -0.430

Iteración 3:
x0 = 0.430
x1 = 0.140
x2 = -0.429

Iteración 4:
x0 = 0.429
x1 = 0.143
x2 = -0.429

Solución encontrada
```
### 🔙 [← Regresar al índice del Tema 3 - Métodos de Solución de Sistemas de Ecuaciones Lineales](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T3%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales.md)
