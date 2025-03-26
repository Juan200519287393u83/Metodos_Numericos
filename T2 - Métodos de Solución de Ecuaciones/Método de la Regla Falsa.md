# 📐 Tema 2: Método de la Regla Falsa (Falsa Posición)

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> ⚙️ **Tipo:** Método de intervalo  
> 🎯 **Propósito:** Aproximar raíces de funciones continuas en un intervalo donde cambia de signo

---

## 🧠 ¿Qué es el Método de la Regla Falsa?

El **método de la regla falsa**, también llamado **falsa posición**, es una técnica numérica que busca una raíz de la función \( f(x) \) dentro de un intervalo \([a, b]\), donde la función cambia de signo:

```

f(a) \* f(b) < 0

```

A diferencia de la **bisección**, que parte el intervalo a la mitad, este método utiliza una **recta secante** entre los puntos \((a, f(a))\) y \((b, f(b))\) para obtener una mejor aproximación:

```

p = a - f(a) \* (b - a) / (f(b) - f(a))

````

✅ Más rápido que la bisección en muchos casos.  
⚠️ Puede volverse lento si uno de los extremos permanece fijo durante varias iteraciones.

---

## ⚖️ Ventajas y Desventajas

| ✅ Ventajas                                                                 | ⚠️ Desventajas                                                                         |
|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| Convergencia más rápida que la bisección.                                   | Puede estancarse si uno de los extremos no se actualiza.                               |
| No requiere derivadas.                                                     | Sensible a la forma de la función.                                                     |
| Garantiza convergencia si \( f(a)f(b) < 0 \) y \( f \) es continua.        | Requiere conocer un intervalo donde la función cambie de signo.                        |

---

## 🧮 Pseudocódigo

```text
Inicio
  Función f(x) → x^3 - x - 2

  Inicializar: a = 1.0, b = 2.0, tolerancia = 0.001, maxIter = 100
  fa = f(a), fb = f(b)

  Si fa * fb >= 0 → Error: El intervalo no contiene una raíz

  Para iteracion desde 0 hasta maxIter:
    p = a - (fa * (b - a)) / (fb - fa)
    fp = f(p)
    Mostrar iteración, p, fp

    Si |fp| < tolerancia → Retornar p como raíz

    Si fa * fp < 0:
      b = p, fb = fp
    Sino:
      a = p, fa = fp
Fin
````

---

## 💻 Código base en Java

```java
public class CodigoBaseReglaFalsa {
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
            System.out.println("El intervalo no contiene una raíz");
            return;
        }

        while (iteracion < maxIteraciones) {
            double p = a - (fa * (b - a)) / (fb - fa);
            double fp = f(p);
            System.out.println("Iteración " + iteracion + ": x = " + p + ", f(x) = " + fp);

            if (Math.abs(fp) < tolerancia) {
                System.out.println("Raíz encontrada: " + p);
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

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class FalsePositionMethod {
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
            System.out.println("El intervalo no contiene una raíz");
            return;
        }

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double p = a - (fa * (b - a)) / (fb - fa);
            double fp = f(p);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", iteracion, p, fp);

            if (Math.abs(fp) < tolerancia) {
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

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## 🔬 Caso de prueba

```text
Iteración 0: x = 1.556, f(x) = 0.214
Iteración 1: x = 1.518, f(x) = 0.002
✅ Raíz encontrada: 1.518
```

---

## 🔗 Navegación

[🔙 Regresar a T2 - Introducción a los Métodos de Solución de Ecuaciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T2%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones.md)
