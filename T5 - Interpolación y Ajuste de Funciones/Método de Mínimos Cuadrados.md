# 📌 Tema 5: Método de Correlación

---

## 🧠 Introducción

El **método de correlación** cuantifica la fuerza y dirección de la relación lineal entre dos variables numéricas. A diferencia de la regresión, que predice una variable a partir de otra, la correlación simplemente evalúa el grado de asociación entre ambas, sin asumir causalidad.

El coeficiente de correlación más reconocido es el de **Pearson**, que oscila entre \$-1\$ y \$1\$:

* Cercano a **1**: indica una fuerte correlación positiva (ambas variables aumentan simultáneamente).
* Cercano a **-1**: indica una fuerte correlación negativa (una variable crece mientras la otra decrece).
* Cercano a **0**: sugiere ausencia o débil relación lineal.

Esta medida es esencial en el análisis exploratorio de datos para detectar patrones y relaciones, recordando siempre que **correlación no implica causalidad**.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                              | 🔴 Desventajas                                               |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| Fácil cálculo e interpretación                           | Mide únicamente relaciones lineales                          |
| Útil en análisis exploratorios                           | Sensible a valores atípicos                                  |
| Ampliamente utilizado en estadística y ciencias sociales | No establece causalidad, riesgo de interpretaciones erróneas |

---

## ⚙️ Pseudocódigo

```plaintext
Inicio
  Definir x, y vectores de reales [n]
  Inicializar sumX, sumY, sumXY, sumX2, sumY2 = 0

  Para i = 0 hasta n-1
    sumX  += x[i]
    sumY  += y[i]
    sumXY += x[i] * y[i]
    sumX2 += x[i]^2
    sumY2 += y[i]^2
  Fin Para

  r = (n * sumXY - sumX * sumY) / sqrt( (n * sumX2 - sumX^2) * (n * sumY2 - sumY^2) )

  Imprimir "Coeficiente de correlación: ", r
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseCorrelation {
    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};
        int n = x.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0, sumY2 = 0;

        for (int i = 0; i < n; i++) {
            sumX  += x[i];
            sumY  += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
            sumY2 += y[i] * y[i];
        }

        double r = (n * sumXY - sumX * sumY) / 
                   Math.sqrt((n * sumX2 - sumX * sumX) * (n * sumY2 - sumY * sumY));

        System.out.println("Coeficiente de correlación: " + r);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class Correlation {
    public static double calculatePearsonCorrelation(double[] x, double[] y) {
        if (x == null || y == null || x.length != y.length || x.length < 2) {
            throw new IllegalArgumentException("Los vectores x e y deben tener la misma longitud y al menos 2 elementos");
        }

        int n = x.length;
        double sumX = 0, sumY = 0, sumXY = 0, sumX2 = 0, sumY2 = 0;

        for (int i = 0; i < n; i++) {
            sumX  += x[i];
            sumY  += y[i];
            sumXY += x[i] * y[i];
            sumX2 += x[i] * x[i];
            sumY2 += y[i] * y[i];
        }

        double denominator = Math.sqrt((n * sumX2 - sumX * sumX) * (n * sumY2 - sumY * sumY));
        if (Math.abs(denominator) < 1e-10) {
            throw new IllegalArgumentException("No se puede calcular la correlación: varianza cero o datos constantes");
        }

        return (n * sumXY - sumX * sumY) / denominator;
    }

    public static void main(String[] args) {
        double[] x = {0, 1, 2, 3};
        double[] y = {1, 2.718, 7.389, 20.085};

        try {
            double r = calculatePearsonCorrelation(x, y);
            System.out.println("Análisis de correlación (Pearson):");
            System.out.printf("Coeficiente de correlación: %.3f%n", r);
            System.out.printf("Interpretación: %s%n", interpretCorrelation(r));
            System.out.println("Datos analizados:");
            for (int i = 0; i < x.length; i++) {
                System.out.printf("(%.1f, %.3f)%n", x[i], y[i]);
            }
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    private static String interpretCorrelation(double r) {
        if (r > 0.7) return "Fuerte correlación positiva";
        if (r > 0.3) return "Correlación positiva moderada";
        if (r > -0.3) return "Correlación débil o inexistente";
        if (r > -0.7) return "Correlación negativa moderada";
        return "Fuerte correlación negativa";
    }
}
```

---

## 🧪 Caso de prueba

```text
Análisis de correlación (Pearson):
Coeficiente de correlación: 0.904
Interpretación: Fuerte correlación positiva
Datos analizados:
(0.0, 1.000)
(1.0, 2.718)
(2.0, 7.389)
(3.0, 20.085)
```

---

### 🔙 [Volver al índice del Tema 5 - Interpolación y Ajuste de Funciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T5%20-%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones/Introducci%C3%B3n%20a%20la%20Interpolaci%C3%B3n%20y%20Ajuste%20de%20Funciones.md)
