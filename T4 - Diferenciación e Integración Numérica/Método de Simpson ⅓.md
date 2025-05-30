#  📌 Tema 4: Método de Simpson 1/3

## 🧠 ¿En qué consiste el Método de Simpson 1/3?

El **método de Simpson 1/3** es una técnica de integración numérica que aproxima el valor de una integral definida usando una combinación ponderada de valores de la función evaluados en puntos igualmente espaciados.

Este método se basa en aproximar el área bajo la curva mediante parábolas (polinomios de segundo grado) en subintervalos del intervalo de integración. Para ello, se divide el intervalo en un número par de subintervalos y se aplica una fórmula específica que da más peso a los puntos medios.

Gracias a su simplicidad y precisión, es ampliamente usado en ingeniería, física y ciencias aplicadas, especialmente cuando la función es continua y suave.

> ✅ Ofrece mayor precisión que el método del trapecio para funciones suaves.
> ⚠️ Requiere un número par de subintervalos y pierde precisión ante funciones con discontinuidades o oscilaciones bruscas.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                   | 🔴 Desventajas                                            |
| ------------------------------------------------------------- | --------------------------------------------------------- |
| Mayor precisión que el método del trapecio                    | Necesita número par de subintervalos                      |
| Simple y eficiente para funciones suaves                      | No recomendado para funciones con muchas discontinuidades |
| Resultados confiables con un número moderado de subintervalos | Pierde precisión con funciones altamente oscilatorias     |

---

## ⚙️ Pseudocódigo del Método

```plaintext
Inicio
  Definir función f(x) = exp(x)

  Definir a, b como reales
  Definir n como entero (n debe ser par)
  Definir h = (b - a) / n
  Definir suma = f(a) + f(b)

  Para i desde 1 hasta n - 1:
    x = a + i * h
    Si i es par:
      suma = suma + 2 * f(x)
    Sino:
      suma = suma + 4 * f(x)
  Fin Para

  integral = (h / 3) * suma
  Imprimir integral aproximada
Fin
```

---

## 💻 Código Java (estructura base)

```java
public class CodigoBaseSimpsonOneThird {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 4;

        if (n % 2 != 0) {
            System.out.println("El número de subintervalos debe ser par");
            return;
        }

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            if (i % 2 == 0) {
                suma += 2 * f(x);
            } else {
                suma += 4 * f(x);
            }
        }

        double integral = (h / 3) * suma;
        System.out.println("Integral aproximada: " + integral);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class SimpsonOneThird {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 4;

        if (n % 2 != 0) {
            System.out.println("El número de subintervalos debe ser par");
            return;
        }

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            if (i % 2 == 0) {
                suma += 2 * f(x);
            } else {
                suma += 4 * f(x);
            }
        }

        double integral = (h / 3) * suma;
        System.out.printf("Integral aproximada: %.3f%n", integral);
    }
}
```

---

## 🧪 Resultado esperado

```
Integral aproximada: 1.718
```

---

### 🔙 [Regresar al índice del Tema 4 - Diferenciación e Integración Numérica](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T4%20-%20Diferenciaci%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica/Introducci%C3%B3n%20a%20la%20DIferenciai%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica.md)
