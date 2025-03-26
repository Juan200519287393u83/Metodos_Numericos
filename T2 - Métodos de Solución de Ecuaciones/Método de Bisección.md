# 🧮 Tema 2: Método de Bisección

> 📌 **Categoría:** Métodos de Solución de Ecuaciones  
> 🧠 **Nivel:** Principiante  
> 💡 **Aplicación:** Encontrar raíces de funciones continuas

---

## 🧩 ¿En qué consiste?

El **método de bisección** es una técnica numérica clásica utilizada para aproximar raíces de funciones continuas cuando no se puede resolver la ecuación de forma exacta.

🔍 Se basa en **dividir un intervalo en dos mitades** e identificar en cuál de ellas ocurre un **cambio de signo** de la función. Este cambio garantiza que hay al menos una raíz en ese subintervalo.

💡 Es ideal para comenzar con métodos numéricos porque:
- No requiere derivadas ni conocimientos avanzados.
- Es **seguro** y **convergente**, aunque **lento**.

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
  Función f(x) -> Retorna x^3 - x - 2

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
