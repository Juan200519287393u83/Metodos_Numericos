# 📌 Tema 4: Método de Cuadratura Gaussiana

## 🧠 Introducción

La **cuadratura gaussiana** es un método avanzado para la integración numérica que destaca por su gran precisión con un número reducido de evaluaciones de la función. A diferencia de métodos clásicos como el trapecio o Simpson, que evalúan la función en puntos equidistantes, la cuadratura gaussiana selecciona estratégicamente puntos y pesos para minimizar el error de aproximación.

Este procedimiento consiste en calcular la integral como una suma ponderada de valores de la función en puntos específicos denominados "puntos de Gauss". Estos puntos, que no están distribuidos uniformemente, junto con sus pesos, se determinan a partir de los ceros de polinomios ortogonales (como los de Legendre) en un intervalo dado. Gracias a esta característica, el método logra una precisión sobresaliente usando pocos puntos.

Por su eficiencia y exactitud, la cuadratura gaussiana es ampliamente utilizada en problemas científicos y de ingeniería complejos, como simulaciones físicas, análisis de elementos finitos y cálculos numéricos avanzados. Sin embargo, requiere un conocimiento previo para obtener o calcular los puntos y pesos adecuados, lo que hace que su implementación sea más sofisticada que los métodos básicos.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                       | 🔴 Desventajas                                                    |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| Gran precisión con pocas evaluaciones                             | Es necesario contar con los puntos y pesos previamente calculados |
| Ideal para integrar funciones definidas en intervalos específicos | Más complejo de implementar y entender que métodos elementales    |
| Muy eficiente para problemas computacionales exigentes            | No es adecuado si no se dispone de puntos y pesos correctos       |

---

## ⚙️ Pseudocódigo

```plaintext
Inicio
  Función f(x)
    Retornar exp(x)
  Fin Función

  Definir a, b como reales
  Definir n como entero
  Definir puntos como vector de reales [n]
  Definir pesos como vector de reales [n]
  Definir suma, t, x, integral como reales
  Definir i como entero

  a = 0.0
  b = 1.0
  n = 3
  puntos = [-0.774596669, 0.0, 0.774596669]
  pesos = [0.555555556, 0.888888889, 0.555555556]

  suma = 0
  Para i = 0 hasta n - 1
    t = puntos[i]
    x = ((b - a) * t + (b + a)) / 2
    suma = suma + pesos[i] * f(x)
  Fin Para

  integral = ((b - a) / 2) * suma
  Imprimir "Valor aproximado de la integral: ", integral
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseGaussianQuadrature {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 3;
        double[] puntos = {-0.774596669, 0.0, 0.774596669};
        double[] pesos = {0.555555556, 0.888888889, 0.555555556};

        double suma = 0;
        for (int i = 0; i < n; i++) {
            double t = puntos[i];
            double x = ((b - a) * t + (b + a)) / 2;
            suma += pesos[i] * f(x);
        }

        double integral = ((b - a) / 2) * suma;
        System.out.println("Valor aproximado de la integral: " + integral);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class GaussianQuadrature {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 3;
        double[] puntos = {-0.774596669, 0.0, 0.774596669};
        double[] pesos = {0.555555556, 0.888888889, 0.555555556};

        double suma = 0;
        for (int i = 0; i < n; i++) {
            double t = puntos[i];
            double x = ((b - a) * t + (b + a)) / 2;
            suma += pesos[i] * f(x);
        }

        double integral = ((b - a) / 2) * suma;
        System.out.printf("Valor aproximado de la integral: %.3f%n", integral);
    }
}
```

---

## 🧪 Resultado esperado

```
Valor aproximado de la integral: 1.718
```

---

### 🔙 [Volver al índice del Tema 4 - Diferenciación e Integración Numérica](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T4%20-%20Diferenciaci%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica/Introducci%C3%B3n%20a%20la%20DIferenciai%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica.md)

