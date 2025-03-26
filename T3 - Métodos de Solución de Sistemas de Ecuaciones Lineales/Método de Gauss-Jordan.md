# 📌 Tema 3: Método de Gauss-Jordan

## 🧠 ¿Qué es el Método de Gauss-Jordan?

El **método de Gauss-Jordan** es una mejora del método de eliminación de Gauss. A diferencia de este último, no solo busca convertir la matriz aumentada del sistema en una forma escalonada, sino que la lleva a su **forma reducida por filas**, donde los elementos fuera de la diagonal principal también son eliminados. El objetivo final es convertir la matriz de coeficientes en una **matriz identidad**, lo cual permite obtener las soluciones directamente.

Este enfoque evita el paso de sustitución regresiva y permite:

* Resolver sistemas de ecuaciones de manera más directa.
* Invertir matrices fácilmente.
* Detectar si un sistema no tiene solución o tiene infinitas soluciones con claridad.

> 🧠 Aunque es muy útil para entender la teoría de los sistemas lineales, su alto coste computacional lo hace poco adecuado para problemas de gran tamaño.

---

## 🟢 Pros y 🔴 Contras

| 🟢 Ventajas                                                                             | 🔴 Desventajas                                                         |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Calcula la solución sin pasos adicionales como la sustitución regresiva.                | Requiere más operaciones que la eliminación gaussiana.                 |
| Ideal para invertir matrices o reutilizar una misma matriz de coeficientes.             | Puede presentar errores numéricos en sistemas mal condicionados.       |
| Permite detectar fácilmente si el sistema es incompatible o tiene soluciones infinitas. | Generalmente no incluye pivoteo, lo cual puede afectar su estabilidad. |

---

## ⚙️ Pseudocódigo

```plaintext
Inicio
  Definir n, A[n][n], b[n], x[n]
  Inicializar matriz A y vector b con los valores del sistema

  Para cada fila k de 0 a n-1:
    Si el pivote A[k][k] es cero:
      Mostrar error y terminar
    Normalizar la fila k dividiendo por el pivote
    Aplicar eliminación a todas las demás filas para anular la columna k

  Al finalizar, el vector b contiene las soluciones
  Mostrar el resultado
Fin
```

---

## 💡 Código Java - Base

```java
public class CodigoBaseGaussJordan {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {{3, 2, -1}, {2, -2, 4}, {-1, 0.5, -1}};
        double[] b = {1, -2, 0};
        double[] x = new double[n];

        for (int k = 0; k < n; k++) {
            if (A[k][k] == 0) {
                System.out.println("Pivote nulo, no se puede resolver");
                return;
            }

            double factor = A[k][k];
            for (int j = 0; j < n; j++) {
                A[k][j] /= factor;
            }
            b[k] /= factor;

            for (int i = 0; i < n; i++) {
                if (i != k) {
                    factor = A[i][k];
                    for (int j = 0; j < n; j++) {
                        A[i][j] -= factor * A[k][j];
                    }
                    b[i] -= factor * b[k];
                }
            }
        }

        for (int i = 0; i < n; i++) {
            x[i] = b[i];
        }

        System.out.println("Solución:");
        for (int i = 0; i < n; i++) {
            System.out.printf("x%d = %.3f%n", i, x[i]);
        }
    }
}
```

---

## 🧪 Ejemplo resuelto

```java
public class GaussJordan {
    public static void main(String[] args) {
        int n = 3;
        double[][] A = {{3, 2, -1}, {2, -2, 4}, {-1, 0.5, -1}};
        double[] b = {1, -2, 0};
        double[] x = new double[n];

        for (int k = 0; k < n; k++) {
            if (A[k][k] == 0) {
                System.out.println("Pivote nulo, no se puede resolver");
                return;
            }

            double factor = A[k][k];
            for (int j = 0; j < n; j++) {
                A[k][j] /= factor;
            }
            b[k] /= factor;

            for (int i = 0; i < n; i++) {
                if (i != k) {
                    factor = A[i][k];
                    for (int j = 0; j < n; j++) {
                        A[i][j] -= factor * A[k][j];
                    }
                    b[i] -= factor * b[k];
                }
            }
        }

        for (int i = 0; i < n; i++) {
            x[i] = b[i];
        }

        System.out.println("Solución:");
        for (int i = 0; i < n; i++) {
            System.out.printf("x%d = %.3f%n", i, x[i]);
        }
    }
}
```

---

## 🔎 Resultado esperado

```
Entrada:
A = [[3, 2, -1], [2, -2, 4], [-1, 0.5, -1]]
b = [1, -2, 0]

Salida:
x0 = 0.429
x1 = 0.143
x2 = -0.429
```

### 🔙 [← Volver al índice del Tema 3 - Métodos para resolver sistemas de ecuaciones lineales](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T3%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Sistemas%20de%20Ecuaciones%20Lineales.md)
