# 📌 Tema 4: Método del Trapecio

## 🧠 Introducción

El **método del trapecio** es una de las técnicas más sencillas y populares en integración numérica. Consiste en aproximar el área bajo la curva de una función usando trapecios en lugar de rectángulos. Es decir, une cada par de puntos consecutivos de la función mediante una línea recta y calcula el área del trapecio formado por esta línea y el eje x.

Este método puede aplicarse tanto en un solo intervalo como dividiendo el rango total en varios subintervalos, lo que mejora la precisión — a esto se le llama método del trapecio compuesto. Aunque no es tan preciso como métodos más avanzados como Simpson, su simplicidad y facilidad de uso lo hacen ideal para muchas aplicaciones prácticas.

El error del método depende del tamaño de los subintervalos y de la curvatura de la función. Si la función es lineal o casi lineal, la aproximación es bastante exacta. Pero si presenta curvaturas pronunciadas, será necesario dividir el intervalo en muchas partes pequeñas para lograr buenos resultados. A pesar de eso, su equilibrio entre sencillez y precisión lo mantiene como un método fundamental en el análisis numérico.

---

## ⚖️ Ventajas y Desventajas

| 🟢 Ventajas                                                 | 🔴 Desventajas                                                       |
| ----------------------------------------------------------- | -------------------------------------------------------------------- |
| Muy fácil de comprender e implementar                       | Menos preciso que métodos como Simpson para funciones curvas         |
| Adecuado para funciones casi lineales o pocos subintervalos | El error aumenta con la curvatura de la función                      |
| Se puede mejorar con la versión compuesta                   | Para funciones complejas requiere subdividir en muchos subintervalos |

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
  n = 4

  h = (b - a) / n
  suma = f(a) + f(b)

  Para i = 1 hasta n-1
    x = a + i * h
    suma = suma + 2 * f(x)
  Fin Para

  integral = (h / 2) * suma
  Imprimir "Integral aproximada: ", integral
Fin
```

---

## 💻 Código base en Java

```java
public class CodigoBaseTrapezoidalRule {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 4;

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            suma += 2 * f(x);
        }

        double integral = (h / 2) * suma;
        System.out.println("Integral aproximada: " + integral);
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class TrapezoidalRule {
    public static double f(double x) {
        return Math.exp(x);
    }

    public static void main(String[] args) {
        double a = 0.0;
        double b = 1.0;
        int n = 4;

        double h = (b - a) / n;
        double suma = f(a) + f(b);

        for (int i = 1; i < n; i++) {
            double x = a + i * h;
            suma += 2 * f(x);
        }

        double integral = (h / 2) * suma;
        System.out.printf("Integral aproximada: %.3f%n", integral);
    }
}
```

---

## 🧪 Resultado esperado

```
Integral aproximada: 1.721
```

---

### 🔙 [← Volver al índice del Tema 4 - Diferenciación e Integración Numérica](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T4%20-%20Diferenciaci%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica/Introducci%C3%B3n%20a%20la%20DIferenciai%C3%B3n%20e%20Integraci%C3%B3n%20Num%C3%A9rica.md)
