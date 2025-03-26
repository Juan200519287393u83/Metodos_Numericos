
# 🧮 Tema 2: Método de Bisección

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> 🧠 **Nivel:** Principiante  
> 💡 **Aplicación:** Encontrar raíces de funciones continuas

---

## 🧩 ¿En qué consiste?

El **método de bisección** es una técnica numérica utilizada para encontrar raíces de una función cuando no se puede determinar la solución de manera exacta. Se basa en dividir iterativamente un intervalo en dos partes y detectar en cuál subintervalo ocurre un **cambio de signo** en la función, lo que indica la presencia de una raíz.

🔎 Este método se fundamenta en el **Teorema del Valor Intermedio** y garantiza convergencia si la función es continua en el intervalo y hay cambio de signo en los extremos.

✅ Aunque es más lento que otros métodos, es **muy seguro**, lo que lo convierte en una excelente herramienta inicial o de verificación.

---

## ⚖️ Ventajas y Desventajas

| ✅ Ventajas                                                                 | ⚠️ Desventajas                                                               |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------|
| Garantiza convergencia si hay cambio de signo en el intervalo.             | Convergencia lenta frente a otros métodos como Newton-Raphson.              |
| Fácil de implementar.                                                      | Requiere que el intervalo inicial contenga una raíz.                        |
| No necesita derivadas.                                                     | Solo encuentra una raíz por ejecución.                                      |

---

## 📋 Pseudocódigo

```java
Inicio
  Función f(x) -> Retornar x^3 - x - 2

  Inicializar: a = 1.0, b = 2.0, tolerancia = 0.001, maxIter = 100
  Calcular: fa = f(a), fb = f(b)

  Si fa * fb >= 0 → Error: No hay cambio de signo

  Mientras iteración < maxIter:
    p = (a + b) / 2
    fp = f(p)
    Si |fp| < tolerancia o |b - a| < tolerancia:
        Retornar p como raíz aproximada
    Si fa * fp < 0:
        b = p
    Sino:
        a = p
  FinMientras
Fin
````

---

## 🧪 Código base en Java

```java
public class CodigoBaseBiseccion {
    public static double f(double x) {
        return Math.pow(x, 3) - x - 2;
    }

    public static void main(String[] args) {
        double a = 1.0, b = 2.0, tolerancia = 0.001;
        int maxIter = 100;
        double fa = f(a), fb = f(b);

        if (fa * fb >= 0) {
            System.out.println("No se cumple el criterio para aplicar bisección");
            return;
        }

        for (int i = 0; i < maxIter; i++) {
            double p = (a + b) / 2;
            double fp = f(p);

            System.out.printf("Iteración %d: x = %.3f, f(x) = %.3f%n", i, p, fp);

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

        System.out.println("Máximo de iteraciones alcanzado");
    }
}
```

---

## ✅ Ejecución esperada

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
✅ Raíz encontrada: 1.522
```

---

## 🔗 Navegación

[🔙 Regresar a T2 - Introducción a los Métodos de Solución de Ecuaciones](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T2%20-%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones/Introducci%C3%B3n%20a%20los%20M%C3%A9todos%20de%20Soluci%C3%B3n%20de%20Ecuaciones.md)
