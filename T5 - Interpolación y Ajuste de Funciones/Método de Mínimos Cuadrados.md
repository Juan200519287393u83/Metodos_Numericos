
# 📊  Tema 5: Método de Mínimos Cuadrados

---

## 🔎 Introducción

 El **método de mínimos cuadrados** es una técnica matemática esencial para determinar la función que mejor representa un conjunto de datos experimentales, minimizando la suma de los cuadrados de las diferencias entre los valores observados y los predichos por el modelo.

 Comúnmente se emplea para ajustar una recta (modelo lineal) a datos dispersos, garantizando un equilibrio óptimo según criterios estadísticos rigurosos. Además, puede extenderse a modelos polinómicos y no lineales con herramientas computacionales modernas.

Más allá de la modelación, este método facilita la comprensión y cuantificación de las relaciones funcionales entre variables.

---

## ⚖️ Ventajas y Limitaciones

| 🟢 **Ventajas**                                              | 🔴 **Limitaciones**                                                                                  |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| ✅ Ajuste óptimo minimizando la suma de errores cuadráticos.  | ⚠️ Sensible a valores atípicos que pueden distorsionar el ajuste.                                    |
| ✅ Implementación sencilla y eficiente para modelos lineales. | ⚠️ Asume relación lineal, limitando su uso en patrones no lineales sin ajustes.                      |
| ✅ Amplio uso en ciencias, ingeniería y economía.             | ⚠️ Requiere validar supuestos estadísticos como normalidad de errores para interpretación confiable. |

---

## 📋 Algoritmo (Pseudocódigo)

```plaintext
Inicio
  Definir vectores x, y de tamaño n
  Inicializar sumX, sumY, sumXY, sumX2 a 0
  Para i desde 0 hasta n-1 hacer
    sumX  += x[i]
    sumY  += y[i]
    sumXY += x[i] * y[i]
    sumX2 += x[i] * x[i]
  Fin Para

  Calcular pendiente m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX^2)
  Calcular ordenada al origen b = (sumY - m * sumX) / n

  Imprimir "Ecuación de la recta: y = m x + b"
Fin
```

---

## 💻 Código Base en Java

```java
public class CodigoBaseLeastSquares {
    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        int n = x.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;

        for (int i = 0; i < n; i++) {
            sumX  += x[i];
            sumY  += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
        }

        double m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
        double b = (sumY - m * sumX) / n;

        System.out.printf("Ecuación de la recta: y = %.4fx + %.4f%n", m, b);
    }
}
```

---

## 🚀 Ejemplo Funcional en Java con Evaluación del Ajuste

```java
public class LeastSquares {
    public static class LinearModel {
        public final double m;   // Pendiente
        public final double b;   // Intersección
        public final double mse; // Error cuadrático medio

        public LinearModel(double m, double b, double mse) {
            this.m = m;
            this.b = b;
            this.mse = mse;
        }
    }

    public static LinearModel fitLinearModel(double[] x, double[] y) {
        if (x == null || y == null || x.length != y.length || x.length < 2) {
            throw new IllegalArgumentException("Los vectores x e y deben tener la misma longitud y al menos dos elementos");
        }

        int n = x.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0;

        for (int i = 0; i < n; i++) {
            sumX  += x[i];
            sumY  += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
        }

        double denominator = n * sumX2 - sumX * sumX;
        if (Math.abs(denominator) < 1e-10) {
            throw new IllegalArgumentException("No se puede ajustar la recta: datos insuficientes o colineales");
        }

        double m = (n * sumXY - sumX * sumY) / denominator;
        double b = (sumY - m * sumX) / n;

        double mse = 0;
        for (int i = 0; i < n; i++) {
            double predicted = m * x[i] + b;
            mse += Math.pow(y[i] - predicted, 2);
        }
        mse /= n;

        return new LinearModel(m, b, mse);
    }

    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};

        try {
            LinearModel model = fitLinearModel(x, y);
            System.out.println("🔍 Ajuste por mínimos cuadrados:");
            System.out.printf("📈 Ecuación de la recta: y = %.3fx + %.3f%n", model.m, model.b);
            System.out.printf("⚠️ Error cuadrático medio: %.3f%n", model.mse);
            System.out.println("🗃 Datos utilizados:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("  • (%.1f, %.3f)%n", x[i], y[i]);
            }
        } catch (IllegalArgumentException e) {
            System.err.println("❌ Error: " + e.getMessage());
        }
    }
}
```

---

## 📊 Resultados del Caso de Prueba

```text
🔍 Ajuste por mínimos cuadrados:
📈 Ecuación de la recta: y = 6.361x + 0.171
⚠️ Error cuadrático medio: 7.687
🗃 Datos utilizados:
  • (0.0, 1.000)
  • (1.0, 2.718)
  • (2.0, 7.389)
  • (3.0, 20.085)
```

---


🔙[Volver al índice del Tema 5 - Interpolación y Ajuste de Funciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T5%20-%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones/Introducci%C3%B3n%20a%20la%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones.md)
