# 📌  Tema 5: Interpolación Lineal

## 🧠 Introducción

La **interpolación lineal** es una técnica sencilla y directa para estimar valores intermedios entre dos puntos conocidos, uniendo estos con una línea recta y calculando valores sobre esa línea. Asume que la función cambia de forma lineal entre los puntos, lo que facilita cálculos rápidos en intervalos pequeños.

Este método es muy útil cuando se dispone de pocos datos y se necesita una solución rápida y razonablemente precisa. Sin embargo, si la función presenta cambios no lineales, la precisión disminuye y pueden aparecer errores.

A pesar de sus limitaciones, la interpolación lineal es ampliamente utilizada como primer paso en análisis numéricos, y es la base para métodos más complejos como la interpolación polinómica o spline.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                      | 🔴 Desventajas                                           |
| ------------------------------------------------ | -------------------------------------------------------- |
| Muy fácil de implementar y eficiente             | Precisión limitada si la función no es lineal            |
| Adecuada para intervalos pequeños                | No funciona bien en intervalos grandes o cambios bruscos |
| Base para métodos de interpolación más avanzados | Puede generar errores significativos con datos pobres    |

---

## ⚙️ Pseudocódigo

```plaintext
Inicio
  Definir x como vector de reales [n]
  Definir y como vector de reales [n]
  Definir xp como real
  Definir yp como real
  Definir i como entero

  x = [0, 1, 2, 3]
  y = [1, 2.718, 7.389, 20.085]
  xp = 1.5
  n = 4

  Para i = 0 hasta n-2
    Si x[i] <= xp Y xp <= x[i+1]
      yp = y[i] + (y[i+1] - y[i]) * (xp - x[i]) / (x[i+1] - x[i])
      Imprimir "Valor interpolado en x = ", xp, ": ", yp
      Retornar
    Fin Si
  Fin Para

  Imprimir "El punto está fuera del rango de interpolación"
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseLinearInterpolation {
    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        double xp = 1.5;
        int n = x.length;

        for (int i = 0; i < n - 1; i++) {
            if (x[i] <= xp && xp <= x[i + 1]) {
                double yp = y[i] + (y[i + 1] - y[i]) * (xp - x[i]) / (x[i + 1] - x[i]);
                System.out.println("Valor interpolado en x = " + xp + ": " + yp);
                return;
            }
        }
        System.out.println("El punto está fuera del rango de interpolación");
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class LinearInterpolation {
    public static double interpolate(double[] x, double[] y, double xp) {
        if (x == null || y == null || x.length != y.length || x.length < 2) {
            throw new IllegalArgumentException("Los vectores x e y deben tener la misma longitud y al menos 2 elementos");
        }
        for (int i = 1; i < x.length; i++) {
            if (x[i] <= x[i - 1]) {
                throw new IllegalArgumentException("El vector x debe estar ordenado de forma ascendente");
            }
        }
        for (int i = 0; i < x.length - 1; i++) {
            if (x[i] <= xp && xp <= x[i + 1]) {
                double yp = y[i] + (y[i + 1] - y[i]) * (xp - x[i]) / (x[i + 1] - x[i]);
                return yp;
            }
        }
        throw new IllegalArgumentException("El punto xp está fuera del rango de interpolación");
    }

    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        double xp = 1.5;

        try {
            double yp = interpolate(x, y, xp);
            System.out.printf("Interpolación lineal:%n");
            System.out.printf("Punto interpolado: x = %.1f, y = %.3f%n", xp, yp);
            System.out.printf("Puntos utilizados: (%.1f, %.3f), (%.1f, %.3f)%n", x[1], y[1], x[2], y[2]);
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

---

## 🧪 Resultado esperado

```
Interpolación lineal:
Punto interpolado: x = 1.5, y = 5.054
Puntos utilizados: (1.0, 2.718), (2.0, 7.389)
```

---

### 🔙[Volver al índice del Tema 5 - Interpolación y Ajuste de Funciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T5%20-%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones/Introducci%C3%B3n%20a%20la%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones.md)
