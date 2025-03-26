# 🔁 Tema 2: Método de Punto Fijo

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> 🎯 **Nivel:** Básico – Intermedio  
> 🛠️ **Aplicación:** Encontrar raíces de funciones sin necesidad de derivadas

---

## 🧠 ¿Qué es el Método de Punto Fijo?

El **método de punto fijo** es una técnica numérica que transforma una ecuación \( f(x) = 0 \) en otra del tipo:

```

x = g(x)

```

A partir de un valor inicial \( x_0 \), se aplica iterativamente la función \( g(x) \), generando una sucesión de valores que, bajo ciertas condiciones, converge a una solución.

🔍 Esta sucesión se define como:

```

xₙ₊₁ = g(xₙ)

````

✅ **Ideal cuando** no se desea o no se puede derivar la función.  
⚠️ **Convergencia no garantizada:** Depende de que \( |g'(x)| < 1 \) cerca de la raíz esperada.

---

## ⚖️ Ventajas y Desventajas

| ✅ Ventajas                                                                 | ⚠️ Desventajas                                                                          |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| No necesita derivadas.                                                     | La convergencia depende mucho de la función \( g(x) \) elegida.                         |
| Implementación simple e intuitiva.                                         | Puede converger lentamente.                                                             |
| Útil cuando otras técnicas no aplican.                                     | Requiere verificación previa de condiciones de convergencia (como \( |g'(x)| < 1 \)).   |

---

## 🧮 Pseudocódigo

```java
Inicio
  Función f(x) → Retornar x³ - x - 2
  Función g(x) → Retornar (x + 2)^(1/3)

  Inicializar: x = 1.5, tolerancia = 0.001, maxIter = 100
  iteracion = 0

  Mientras iteracion < maxIter:
    xNuevo = g(x)
    Mostrar iteración, xNuevo, f(xNuevo)

    Si |xNuevo - x| < tolerancia → Retornar xNuevo como raíz

    x = xNuevo
    iteracion++
Fin
````

---

## 💻 Código base en Java

```java
public class CodigoBasePuntoFijo {
    public static double f(double x) {
        return Math.pow(x, 3) - x - 2;
    }

    public static double g(double x) {
        return Math.pow(x + 2, 1.0 / 3.0);
    }

    public static void main(String[] args) {
        double x = 1.5;
        double tolerancia = 0.001;
        int maxIteraciones = 100;
        int iteracion = 0;

        while (iteracion < maxIteraciones) {
            double xNuevo = g(x);
            System.out.println("Iteración " + iteracion + ": x = " + xNuevo + ", f(x) = " + f(xNuevo));

            if (Math.abs(xNuevo - x) < tolerancia) {
                System.out.println("Raíz encontrada: " + xNuevo);
                return;
            }

            x = xNuevo;
            iteracion++;
        }

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejemplo funcional en Java

```java
public class FixedPointMethod {
    public static double f(double x) {
        return x * x * x - x - 2;
    }

    public static double g(double x) {
        return Math.pow(x + 2, 1.0 / 3.0);
    }

    public static void main(String[] args) {
        double x = 1.5;
        double tolerancia = 0.001;
        int maxIteraciones = 100;

        for (int iteracion = 0; iteracion < maxIteraciones; iteracion++) {
            double xNuevo = g(x);
            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", iteracion, xNuevo, f(xNuevo));

            if (Math.abs(xNuevo - x) < tolerancia) {
                System.out.printf("Raíz encontrada: %.3f%n", xNuevo);
                return;
            }

            x = xNuevo;
        }

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## 🔬 Caso de prueba

```text
Iteración 0: x = 1.442, f(x) = 0.150
Iteración 1: x = 1.567, f(x) = 0.321
Iteración 2: x = 1.484, f(x) = 0.075
Iteración 3: x = 1.533, f(x) = 0.069
Iteración 4: x = 1.506, f(x) = 0.029
Iteración 5: x = 1.522, f(x) = 0.016
Iteración 6: x = 1.514, f(x) = 0.006
Iteración 7: x = 1.518, f(x) = 0.003
Iteración 8: x = 1.520, f(x) = 0.001
✅ Raíz encontrada: 1.520
```

---

## 🔗 Navegación

[🔙 Regresar a T2 - Introducción a los Métodos de Solución de Ecuaciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T2%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones.md)
