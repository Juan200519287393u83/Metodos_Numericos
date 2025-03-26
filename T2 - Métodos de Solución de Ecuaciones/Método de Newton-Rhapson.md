
# ⚙️ Tema 2: Método de Newton-Raphson

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> 🚀 **Nivel:** Intermedio  
> ⚡ **Aplicación:** Aproximación rápida de raíces de funciones derivables

---

## 🧠 ¿Qué es el Método de Newton-Raphson?

El **método de Newton-Raphson** es una técnica numérica ampliamente utilizada para encontrar raíces de funciones reales. A partir de una **estimación inicial**, este método mejora progresivamente la solución utilizando la derivada de la función, logrando una **rápida convergencia** cuando se aplican condiciones adecuadas.

🔍 Se basa en la fórmula:

```

xₙ₊₁ = xₙ - f(xₙ) / f'(xₙ)

````

Para que funcione correctamente, es crucial que:
- La función sea continua y derivable.
- La derivada no sea cero en la vecindad de la raíz.
- La suposición inicial esté cerca de la solución real.

Cuando estas condiciones se cumplen, el método ofrece resultados precisos en muy pocas iteraciones.

---

## ⚖️ Ventajas y Desventajas

| ✅ Ventajas                                                                       | ⚠️ Desventajas                                                                 |
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| Convergencia rápida (orden cuadrático) con una buena suposición inicial.         | Puede divergir si el punto inicial está lejos o si la derivada es muy pequeña. |
| Requiere menos iteraciones que otros métodos como la bisección.                  | Necesita el cálculo de la derivada, que puede ser complejo.                    |
| Ideal para funciones suaves, comunes en ingeniería y ciencia aplicada.           | No es apto para funciones discontinuas o no derivables.                        |

---

## 🧮 Pseudocódigo

```java
Inicio
  Función f(x) -> Retornar x^3 - x - 2
  Función fPrima(x) -> Retornar 3 * x^2 - 1

  Inicializar: x = 1.5, tolerancia = 0.001, maxIter = 100
  iteracion = 0

  Mientras iteracion < maxIter:
    fx = f(x)
    Mostrar iteración, x, fx
    Si |fx| < tolerancia → Retornar x como raíz
    x = x - fx / fPrima(x)
    iteracion++
Fin
````

---

## 💻 Código base en Java

```java
public class CodigoBaseNewtonRaphson {
    public static double f(double x) {
        return Math.pow(x, 3) - x - 2;
    }

    public static double fPrima(double x) {
        return 3 * Math.pow(x, 2) - 1;
    }

    public static void main(String[] args) {
        double x = 1.5;
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int i = 0; i < maxIteraciones; i++) {
            double fx = f(x);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", i, x, fx);

            if (Math.abs(fx) < tolerancia) {
                System.out.printf("Raíz encontrada: %.3f%n", x);
                return;
            }

            x = x - fx / fPrima(x);
        }

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejemplo funcional

```java
public class NewtonRaphsonMethod {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double fPrima(double x) {
        return 3 * x * x - 1;
    }

    public static void main(String[] args) {
        double x = 1.5;
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double fx = f(x);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", iteracion, x, fx);

            if (Math.abs(fx) < tolerancia) {
                System.out.printf("Raíz encontrada: %.3f%n", x);
                return;
            }

            x = x - fx / fPrima(x);
        }

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## 🔬 Salida esperada

```text
Iteración 0: x = 1.500, f(x) = -0.125
Iteración 1: x = 1.521, f(x) = 0.001
✅ Raíz encontrada: 1.521
```
## 🔗 Navegación

[🔙 Regresar a T2 - Introducción a los Métodos de Solución de Ecuaciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T2%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones.md)
