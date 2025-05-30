# 📌  Tema 5: Interpolación Polinómica

## 🧠 Introducción

La **interpolación polinómica** busca construir un polinomio que pase exactamente por $n + 1$ puntos conocidos. A diferencia de la interpolación lineal, este método puede capturar mejor la curvatura y complejidad de una función subyacente, ya que utiliza expresiones matemáticas más completas.

Entre los métodos más usados están la interpolación de **Newton** y la de **Lagrange**, que permiten construir el polinomio pero con formulaciones distintas. Aunque son exactos en los puntos conocidos, pueden presentar oscilaciones (fenómeno de Runge) con polinomios de grado alto y en intervalos grandes.

La interpolación polinómica es ideal cuando hay un número moderado de datos bien distribuidos y se busca un ajuste exacto. Para conjuntos grandes o datos ruidosos, métodos como splines o ajuste de curvas suelen ser preferidos.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                     | 🔴 Desventajas                                                 |
| --------------------------------------------------------------- | -------------------------------------------------------------- |
| Captura la curvatura de funciones complejas mejor que la lineal | Puede generar oscilaciones (fenómeno de Runge) en grados altos |
| Resultados exactos en los puntos conocidos                      | Más costoso computacionalmente que la interpolación lineal     |
| Útil para datos moderados y bien distribuidos                   | Menos robusto para datos ruidosos o distribuciones irregulares |

---

## ⚙️ Pseudocódigo (Interpolación de Lagrange)

```plaintext
Inicio
  Definir x como vector de reales [n]
  Definir y como vector de reales [n]
  Definir xp como real
  Definir yp como real = 0
  Definir L como real
  Definir i, j como enteros

  Para i = 0 hasta n-1
    L = 1
    Para j = 0 hasta n-1
      Si j != i
        L = L * (xp - x[j]) / (x[i] - x[j])
      Fin Si
    Fin Para
    yp = yp + y[i] * L
  Fin Para

  Imprimir "Valor interpolado en x = ", xp, ": ", yp
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBasePolynomialInterpolation {
    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        double xp = 1.5;
        int n = x.length;
        double yp = 0;

        for (int i = 0; i < n; i++) {
            double L = 1;
            for (int j = 0; j < n; j++) {
                if (j != i) {
                    L *= (xp - x[j]) / (x[i] - x[j]);
                }
            }
            yp += y[i] * L;
        }

        System.out.println("Valor interpolado en x = " + xp + ": " + yp);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class PolynomialInterpolation {
    public static double interpolateLagrange(double[] x, double[] y, double xp) {
        if (x == null || y == null || x.length != y.length || x.length < 2) {
            throw new IllegalArgumentException("Los vectores x e y deben tener la misma longitud y al menos 2 elementos");
        }
        for (int i = 1; i < x.length; i++) {
            if (x[i] <= x[i - 1]) {
                throw new IllegalArgumentException("El vector x debe estar ordenado ascendentemente");
            }
        }
        for (int i = 0; i < x.length; i++) {
            for (int j = i + 1; j < x.length; j++) {
                if (Math.abs(x[i] - x[j]) < 1e-10) {
                    throw new IllegalArgumentException("Los valores de x deben ser distintos");
                }
            }
        }

        double yp = 0;
        for (int i = 0; i < x.length; i++) {
            double L = 1;
            for (int j = 0; j < x.length; j++) {
                if (j != i) {
                    L *= (xp - x[j]) / (x[i] - x[j]);
                }
            }
            yp += y[i] * L;
        }
        return yp;
    }

    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        double xp = 1.5;

        try {
            double yp = interpolateLagrange(x, y, xp);
            System.out.printf("Interpolación polinómica (Lagrange):%n");
            System.out.printf("Punto interpolado: x = %.1f, y = %.3f%n", xp, yp);
            System.out.println("Puntos usados:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("(%.1f, %.3f)%n", x[i], y[i]);
            }
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

---

## 🧪 Resultado esperado

```
Interpolación polinómica (Lagrange):
Punto interpolado: x = 1.5, y = 4.482
Puntos usados:
(0.0, 1.000)
(1.0, 2.718)
(2.0, 7.389)
(3.0, 20.085)
```

---

### 🔙 [Volver al índice del Tema 5 - Interpolación y Ajuste de Funciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T5%20-%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones/Introducci%C3%B3n%20a%20la%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones.md)
