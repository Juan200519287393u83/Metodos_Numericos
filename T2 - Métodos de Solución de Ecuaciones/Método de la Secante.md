# ⚡ Tema 2: Método de la Secante

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> 🔁 **Tipo:** Método iterativo abierto  
> 🎯 **Propósito:** Aproximar raíces de funciones sin necesidad de derivadas

---

## 🧠 ¿Qué es el Método de la Secante?

El **método de la secante** es una técnica numérica que permite encontrar una raíz de una función continua sin necesidad de calcular derivadas. A partir de dos puntos iniciales \( x_0 \) y \( x_1 \), el método traza una línea recta (secante) entre los puntos \( (x_0, f(x_0)) \) y \( (x_1, f(x_1)) \), y encuentra la intersección de esta línea con el eje \( x \):

```

x₂ = x₁ - f(x₁) \* (x₁ - x₀) / (f(x₁) - f(x₀))

````

Este nuevo punto se convierte en una mejor aproximación a la raíz. El proceso se repite utilizando los dos valores más recientes.

---

## ⚖️ Ventajas y Desventajas

| ✅ Ventajas                                                                 | ⚠️ Desventajas                                                                     |
|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| No requiere derivadas (a diferencia de Newton-Raphson).                     | La convergencia no está garantizada.                                               |
| Puede ser más rápido que métodos como bisección y regla falsa.              | Menos estable: puede divergir en funciones mal condicionadas o elecciones pobres.  |
| Simple de implementar.                                                      | Sensible a los valores iniciales y la forma de la función.                         |

---

## 🧮 Pseudocódigo

```text
Inicio
  Función f(x) → x^3 - x - 2

  Inicializar: x0 = 1.0, x1 = 2.0, tolerancia = 0.001, maxIter = 100
  iteracion = 0

  Mientras iteracion < maxIter:
    fx0 = f(x0)
    fx1 = f(x1)
    x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0)
    Mostrar iteración, x2, f(x2)

    Si |f(x2)| < tolerancia → Retornar x2 como raíz

    x0 = x1
    x1 = x2
    iteracion++
  Fin Mientras

  Mostrar: "Máximo de iteraciones alcanzado"
Fin
````

---

## 💻 Código base en Java

```java
public class CodigoBaseSecante {
    public static double f(double x) {
        return Math.pow(x, 3) - x - 2;
    }

    public static void main(String[] args) {
        double x0 = 1.0;
        double x1 = 2.0;
        double tolerancia = 0.001;
        int maxIteraciones = 100;
        int iteracion = 0;

        while (iteracion < maxIteraciones) {
            double fx0 = f(x0);
            double fx1 = f(x1);
            double x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
            System.out.println("Iteración " + iteracion + ": x = " + x2 + ", f(x) = " + f(x2));

            if (Math.abs(f(x2)) < tolerancia) {
                System.out.println("Raíz encontrada: " + x2);
                return;
            }

            x0 = x1;
            x1 = x2;
            iteracion++;
        }

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class SecantMethod {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static void main(String[] args) {
        double x0 = 1.0;
        double x1 = 2.0;
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double fx0 = f(x0);
            double fx1 = f(x1);
            double x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", iteracion, x2, f(x2));

            if (Math.abs(f(x2)) < tolerancia) {
                System.out.printf("Raíz encontrada: %.3f%n", x2);
                return;
            }

            x0 = x1;
            x1 = x2;
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
