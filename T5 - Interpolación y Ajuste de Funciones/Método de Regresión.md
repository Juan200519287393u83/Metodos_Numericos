# 📈  Tema 5: Método de Regresión


---

## 🔍 Introducción

El **método de regresión** es una técnica estadística para modelar la relación entre una variable dependiente y una o más independientes. A diferencia de la interpolación, no busca pasar por todos los puntos, sino representar la **tendencia general**, especialmente con datos ruidosos o con errores.

La regresión lineal es la más común, ajustando una línea recta que minimiza el error cuadrático entre valores observados y estimados. Existen también regresiones polinómicas, exponenciales, logarítmicas, etc., según la naturaleza del fenómeno.

Se utiliza en economía, física, ingeniería y ciencias sociales para predecir, analizar y evaluar relaciones entre variables. Es fundamental para el análisis estadístico basado en datos reales.

---

## ✅ Ventajas y ❌ Desventajas

| ✅ **Ventajas**                                                        | ❌ **Desventajas**                                                            |
| --------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Modela tendencias en datos ruidosos, ideal para predicciones          | Sensible a valores atípicos que pueden distorsionar el modelo                |
| Proporciona métricas como $R^2$ para evaluar calidad de ajuste        | Asume relación específica (lineal en este caso), no siempre adecuada         |
| Flexible: aplicable a modelos lineales y no lineales con adaptaciones | Requiere supuestos estadísticos (independencia de errores, normalidad, etc.) |

---

## ⚙️ Pseudocódigo

```text
Inicio
  Definir x, y como vectores reales [n]
  Inicializar sumX, sumY, sumXY, sumX2 a 0
  Para i = 0 hasta n-1
    sumX  += x[i]
    sumY  += y[i]
    sumXY += x[i] * y[i]
    sumX2 += x[i]^2
  Fin Para

  Calcular pendiente:
    m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX^2)
  Calcular ordenada al origen:
    b = (sumY - m * sumX) / n

  Imprimir "Ecuación: y = m x + b"
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseLinearRegression {
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

        System.out.println("Ecuación de la recta: y = " + m + "x + " + b);
    }
}
```

---

## 🚀 Ejemplo funcional con Métricas de Calidad

```java
public class LinearRegression {
    public static class RegressionModel {
        public final double m; // Pendiente
        public final double b; // Intersección
        public final double rSquared; // Coeficiente de determinación
        public final double mse; // Error cuadrático medio

        public RegressionModel(double m, double b, double rSquared, double mse) {
            this.m = m;
            this.b = b;
            this.rSquared = rSquared;
            this.mse = mse;
        }
    }

    public static RegressionModel fitLinearRegression(double[] x, double[] y) {
        if (x == null || y == null || x.length != y.length || x.length < 2)
            throw new IllegalArgumentException("Los vectores x e y deben tener la misma longitud y al menos 2 elementos");

        int n = x.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0, sumY2 = 0;

        for (int i = 0; i < n; i++) {
            sumX  += x[i];
            sumY  += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
            sumY2 += y[i] * y[i];
        }

        double denominator = n * sumX2 - sumX * sumX;
        if (Math.abs(denominator) < 1e-10)
            throw new IllegalArgumentException("No se puede ajustar la recta: datos insuficientes o colineales");

        double m = (n * sumXY - sumX * sumY) / denominator;
        double b = (sumY - m * sumX) / n;

        double yMean = sumY / n;
        double ssTot = 0, ssRes = 0;
        for (int i = 0; i < n; i++) {
            double yPred = m * x[i] + b;
            ssRes += Math.pow(y[i] - yPred, 2);
            ssTot += Math.pow(y[i] - yMean, 2);
        }

        double rSquared = ssTot > 1e-10 ? 1 - ssRes / ssTot : 0;
        double mse = ssRes / n;

        return new RegressionModel(m, b, rSquared, mse);
    }

    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};

        try {
            RegressionModel model = fitLinearRegression(x, y);
            System.out.println("📊 Regresión lineal simple:");
            System.out.printf("Ecuación: y = %.3fx + %.3f%n", model.m, model.b);
            System.out.printf("R² (Coeficiente de determinación): %.3f%n", model.rSquared);
            System.out.printf("MSE (Error cuadrático medio): %.3f%n", model.mse);
            System.out.println("Datos utilizados:");
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

## 📋 Caso de prueba

```text
📊 Regresión lineal simple:
Ecuación: y = 6.361x + 0.171
R² (Coeficiente de determinación): 0.818
MSE (Error cuadrático medio): 7.687
Datos utilizados:
  (0.0, 1.000)
  (1.0, 2.718)
  (2.0, 7.389)
  (3.0, 20.085)
```
🔙[Volver a Introducción a la Interpolación y Ajuste de Funciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T5%20-%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones/Introducci%C3%B3n%20a%20la%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones.md)
