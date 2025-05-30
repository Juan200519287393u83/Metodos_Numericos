#  📌 Tema 4: Método de Simpson 3/8

## 🧠 Introducción

El **método de Simpson 3/8** es una variante del método de Simpson diseñado para integraciones donde el número de subintervalos es múltiplo de tres. A diferencia del método 1/3, este método utiliza polinomios de tercer grado (cúbicos) para aproximar la función, lo que puede ofrecer una mejor adaptación a la curva en ciertos casos.

Este método divide el intervalo en tres partes iguales y aplica una fórmula que asigna pesos distintos a los valores de la función en los puntos extremos y en los puntos interiores.

Aunque su uso no es tan extendido como el método 1/3, resulta especialmente útil cuando el número de subintervalos no permite aplicar el método 1/3 o cuando se busca una mayor precisión en segmentos específicos.

La exactitud del método 3/8 es comparable al método 1/3 y en ocasiones puede superar su precisión, dependiendo de la función y del tamaño de los subintervalos.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                  | 🔴 Desventajas                                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| Emplea polinomios cúbicos, lo que puede mejorar la exactitud | Requiere que el número de subintervalos sea múltiplo de tres                   |
| Es útil cuando el método 1/3 no se puede aplicar             | Puede ser más complejo de implementar que el método 1/3                        |
| Proporciona una alternativa para casos particulares          | La precisión disminuye en funciones con discontinuidades o variaciones bruscas |

---

## ⚙️ Pseudocódigo

```plaintext
Inicio
  Función f(x)
    Retornar exp(x)
  Fin Función

  Definir a, b como reales
  Definir n como entero
  Definir h, suma, x, integral como reales
  Definir i como entero

  a = 0.0
  b = 1.0
  n = 3

  Si n mod 3 != 0
    Imprimir "El número de subintervalos debe ser múltiplo de 3"
    Retornar
  Fin Si

  h = (b - a) / n
  suma = f(a) + f(b)

  Para i = 1 hasta n - 1
    x = a + i * h
    Si i mod 3 = 0
      suma = suma + 2 * f(x)
    Sino
      suma = suma + 3 * f(x)
    Fin Si
  Fin Para

  integral = (3 * h / 8) * suma
  Imprimir "Valor aproximado de la integral: ", integral
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseSimpsonThreeEighths {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 3;

        if (n % 3 != 0) {
            System.out.println("El número de subintervalos debe ser múltiplo de 3");
            return;
        }

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            if (i % 3 == 0) {
                suma += 2 * f(x);
            } else {
                suma += 3 * f(x);
            }
        }

        double integral = (3 * h / 8) * suma;
        System.out.println("Valor aproximado de la integral: " + integral);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class SimpsonThreeEighths {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 3;

        if (n % 3 != 0) {
            System.out.println("El número de subintervalos debe ser múltiplo de 3");
            return;
        }

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            if (i % 3 == 0) {
                suma += 2 * f(x);
            } else {
                suma += 3 * f(x);
            }
        }

        double integral = (3 * h / 8) * suma;
        System.out.printf("Valor aproximado de la integral: %.3f%n", integral);
    }
}
```

---

## 🧪 Resultado esperado
```
Valor aproximado de la integral: 1.718
```
### 🔙 [ Volver al índice del Tema 4 - Diferenciación e Integración Numérica](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T4%20-%20Diferenciaci%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica/Introducci%C3%B3n%20a%20la%20DIferenciai%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica.md)
