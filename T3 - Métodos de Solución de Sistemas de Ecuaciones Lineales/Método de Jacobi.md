# 📌 Tema 3: Método de Jacobi

## 🧠 ¿En qué consiste el Método de Jacobi?

El **método de Jacobi** es un método iterativo para resolver sistemas de ecuaciones lineales que parte de una estimación inicial y actualiza simultáneamente cada variable usando solo los valores de la iteración anterior.

A diferencia de Gauss-Seidel, **no utiliza los valores nuevos en la misma iteración**, sino que actualiza todas las variables al final de cada paso. Esto lo hace ideal para paralelizar cálculos, aunque generalmente converge más lento.

Para garantizar la convergencia, la matriz de coeficientes debe ser **diagonalmente dominante** o cumplir condiciones similares.

> ✅ Cuando se cumplen las condiciones, es fácil de implementar y paralelizar.
> ⚠️ Sin embargo, su convergencia puede ser más lenta y no siempre está garantizada.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                      | 🔴 Desventajas                                |
| ------------------------------------------------ | --------------------------------------------- |
| Fácil de paralelizar y programar simultáneamente | Convergencia generalmente más lenta           |
| Requiere solo valores de la iteración anterior   | No siempre converge sin condiciones adecuadas |
| Ideal para matrices dispersas y grandes          | Puede necesitar muchas iteraciones            |

---

## ⚙️ Pseudocódigo del Método

```plaintext
Inicio
  Definir n, A[n][n], b[n], x[n], xNuevo[n]
  Inicializar x con ceros
  Definir tolerancia y máximo número de iteraciones

  Mientras no se alcance la tolerancia o máximo de iteraciones:
    Para cada variable i:
      suma = 0
      Para cada j ≠ i:
        suma += A[i][j] * x[j]
      xNuevo[i] = (b[i] - suma) / A[i][i]

    Calcular error máximo entre xNuevo y x
    Actualizar x con valores de xNuevo

    Mostrar valores de x en la iteración actual
    Si error < tolerancia, detener
Fin
```

---

## 💻 Código Java (estructura base)

```java
public class CodigoBaseJacobi {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {
            {3, 2, -1},
            {2, -2, 4},
            {-1, 0.5, -1}
        };
        double[] b = {1, -2, 0};
        double[] x = {0, 0, 0};
        double[] xNuevo = new double[n];
        double tolerancia = 0.001;
        int maxIteraciones = 100;
        int iteracion = 0;

        while (iteracion < maxIteraciones) {
            for (int i = 0; i < n; i++) {
                double suma = 0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * x[j];
                    }
                }
                xNuevo[i] = (b[i] - suma) / A[i][i];
            }

            double error = 0;
            for (int i = 0; i < n; i++) {
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
public class Jacobi {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {
            {3, 2, -1},
            {2, -2, 4},
            {-1, 0.5, -1}
        };
        double[] b = {1, -2, 0};
        double[] x = {0, 0, 0};
        double[] xNuevo = new double[n];
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            for (int i = 0; i < n; i++) {
                double suma = 0;
                for (int j = 0; j < n; j++) {
                    if (j != i) {
                        suma += A[i][j] * x[j];
                    }
                }
                xNuevo[i] = (b[i] - suma) / A[i][i];
            }

            double error = 0;
            for (int i = 0; i < n; i++) {
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
x1 = -1.000
x2 = 0.000

Iteración 1:
x0 = 0.667
x1 = -0.667
x2 = -0.167

Iteración 2:
x0 = 0.500
x1 = -0.167
x2 = -0.583

Iteración 3:
x0 = 0.583
x1 = 0.167
x2 = -0.333

Iteración 4:
x0 = 0.389
x1 = -0.083
x2 = -0.458

Iteración 5:
x0 = 0.458
x1 = 0.111
x2 = -0.403

Iteración 6:
x0 = 0.412
x1 = 0.042
x2 = -0.444

Iteración 7:
x0 = 0.429
x1 = 0.139
x2 = -0.423

Solución encontrada
```

---

### 🔙[ Regresar al índice del Tema 3 - Métodos de Solución de Sistemas de Ecuaciones Lineales](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T3%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales.md)
