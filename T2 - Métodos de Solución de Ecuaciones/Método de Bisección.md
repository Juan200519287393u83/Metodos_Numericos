
0### 🔙 [← Volver a T2 - Métodos para Resolver Ecuaciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T2%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones.md)

# Tema 2: Método de Bisección

---

## Introducción

El método de bisección es una técnica clásica y confiable para encontrar aproximaciones a las raíces de una función cuando no es posible hallar una solución exacta. La idea principal es dividir un intervalo en dos mitades iguales y determinar en cuál de ellas ocurre un cambio de signo del valor de la función, lo que indica la presencia de una raíz en ese rango. Este proceso se repite iterativamente sobre el subintervalo donde se detecta dicho cambio.

La ventaja más importante de este método es su simplicidad y la garantía de convergencia, siempre que la función sea continua en el intervalo considerado y que exista un cambio de signo entre sus extremos. Por ello, es uno de los métodos más seguros, aunque no el más rápido en términos de convergencia.

Además, no requiere cálculo de derivadas ni características avanzadas de la función, lo que lo hace ideal para quienes comienzan a estudiar métodos numéricos. Aunque su velocidad puede ser lenta, su fiabilidad lo convierte en una excelente opción para obtener una solución inicial que posteriormente puede refinarse con métodos más eficientes.

---

### Beneficios y Limitaciones

**Beneficios:**

* Asegura la convergencia si la función es continua y hay un cambio de signo en el intervalo.
* Es fácil de implementar y no demanda conocimientos avanzados de la función (por ejemplo, derivadas).
* Es una herramienta robusta para localizar raíces iniciales que se pueden mejorar con otros métodos.

**Limitaciones:**

* La tasa de convergencia es relativamente lenta comparada con otros métodos numéricos, como Newton-Raphson.
* Requiere identificar un intervalo que contenga una raíz, lo que no siempre es sencillo.
* No es adecuado para detectar múltiples raíces cercanas ya que localiza sólo una por ejecución.

---

### Pseudocódigo

```java
Inicio
  Función f(x)
    Retornar x^3 - x - 2
  Fin Función

  Definir a, b como reales
  Definir tolerancia como real
  Definir maxIteraciones, iteracion como enteros
  Definir p, fa, fb, fp como reales

  a = 1.0
  b = 2.0
  tolerancia = 0.001
  maxIteraciones = 100
  iteracion = 0

  fa = f(a)
  fb = f(b)

  Si fa * fb >= 0
    Imprimir "No se cumple el criterio para aplicar bisección"
    Retornar
  Fin Si

  Mientras iteracion < maxIteraciones
    p = (a + b) / 2
    fp = f(p)
    Imprimir "Iteración ", iteracion, ": x = ", p, ", f(x) = ", fp

    Si abs(fp) < tolerancia O abs(b - a) < tolerancia
      Imprimir "Raíz aproximada encontrada en: ", p
      Retornar
    Fin Si

    Si fa * fp < 0
      b = p
      fb = fp
    Sino
      a = p
      fa = fp
    Fin Si

    iteracion = iteracion + 1
  Fin Mientras

  Imprimir "Se alcanzó el límite de iteraciones"
Fin
```

---

### Código base en Java

```java
public class CodigoBaseBiseccion {
    public static double f(double x) {
        return Math.pow(x, 3) - x - 2;
    }

    public static void main(String[] args) {
        double a = 1.0;
        double b = 2.0;
        double tolerancia = 0.001;
        int maxIteraciones = 100;
        int iteracion = 0;

        double fa = f(a);
        double fb = f(b);

        if (fa * fb >= 0) {
            System.out.println("No se cumple el criterio para aplicar bisección");
            return;
        }

        while (iteracion < maxIteraciones) {
            double p = (a + b) / 2;
            double fp = f(p);
            System.out.println("Iteración " + iteracion + ": x = " + p + ", f(x) = " + fp);

            if (Math.abs(fp) < tolerancia || Math.abs(b - a) < tolerancia) {
                System.out.println("Raíz aproximada encontrada en: " + p);
                return;
            }

            if (fa * fp < 0) {
                b = p;
                fb = fp;
            } else {
                a = p;
                fa = fp;
            }

            iteracion++;
        }
        System.out.println("Se alcanzó el límite de iteraciones");
    }
}
```

---

### Ejemplo práctico en Java

```java
public class MetodoBiseccion {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static void main(String[] args) {
        double a = 1.0;
        double b = 2.0;
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        double fa = f(a);
        double fb = f(b);

        if (fa * fb >= 0) {
            System.out.println("No se cumple el criterio para aplicar bisección");
            return;
        }

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double p = (a + b) / 2;
            double fp = f(p);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", iteracion, p, fp);

            if (Math.abs(fp) < tolerancia || Math.abs(b - a) < tolerancia) {
                System.out.printf("Raíz encontrada: %.3f%n", p);
                return;
            }

            if (fa * fp < 0) {
                b = p;
                fb = fp;
            } else {
                a = p;
                fa = fp;
            }
        }
        System.out.println("Se alcanzó el límite de iteraciones");
    }
}
```

---

### Resultado esperado

```text
Iteración 0: x = 1.500, f(x) = -0.125
Iteración 1: x = 1.750, f(x) = 1.859
Iteración 2: x = 1.625, f(x) = 0.701
Iteración 3: x = 1.563, f(x) = 0.256
Iteración 4: x = 1.531, f(x) = 0.059
Iteración 5: x = 1.516, f(x) = -0.034
Iteración 6: x = 1.523, f(x) = 0.012
Iteración 7: x = 1.520, f(x) = -0.011
Iteración 8: x = 1.522, f(x) = 0.000
Raíz aproximada encontrada en: 1.522
```
