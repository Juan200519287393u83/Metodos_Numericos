### 🔙 [← Regresar a T1 - Introducción a los Métodos Numéricos](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T1%20-%20Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20num%C3%A9ricos/Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20n%C3%BAmericos.md)

# 📊 Tema 1: Tipos de Errores Numéricos

## ⚠️ Error Numérico Total

---

### ❓ ¿Qué es?

El **Error Numérico Total** es la diferencia global entre el valor exacto (teórico) y el valor aproximado obtenido en un cálculo numérico. Incluye distintos tipos de errores:

* Redondeo
* Truncamiento
* Errores del modelo
* Cancelación
* Incertidumbre en datos de entrada

> Comprender este error es crucial para evaluar la precisión y confiabilidad de los métodos numéricos aplicados.

---

### ✅ Ventajas y ❌ Desventajas

| ✅ **Ventajas**                            | ❌ **Desventajas**                                              |
| ----------------------------------------- | -------------------------------------------------------------- |
| Evaluación integral de la precisión total | Difícil desglose de errores individuales                       |
| Facilita la toma de decisiones informadas | Requiere conocer valores exactos o muy precisos                |
| Identifica fuentes principales de error   | Puede aumentar costos computacionales                          |
| Aplicable a cualquier método numérico     | Difícil estimación en problemas reales con múltiples variables |

---

### 📝 Pseudocódigo para calcular el Error Numérico Total

```java
Inicio
  Definir real, aproximado, errorTotal como reales

  real = sqrt(2)
  aproximado = 1.414
  errorTotal = abs(real - aproximado)

  Imprimir "Valor real: ", real
  Imprimir "Valor aproximado: ", aproximado
  Imprimir "Error numérico total: ", errorTotal
Fin
```

---

### 💻 Código Base en Java

```java
public class ErrorNumerico {
    public static void main(String[] args) {
        double real = Math.sqrt(2);
        double aproximado = 1.414;
        double errorTotal = Math.abs(real - aproximado);

        System.out.println("Valor real: " + real);
        System.out.println("Valor aproximado: " + aproximado);
        System.out.println("Error numérico total: " + errorTotal);
    }
}
```

---

### 🛠 Ejemplo Completo con Salida Formateada

```java
public class ErrorTotal {
    public static void main(String[] args) {
        double valorReal = Math.sqrt(2);
        double valorAproximado = 1.4142;

        double error = Math.abs(valorReal - valorAproximado);

        System.out.printf("Valor real: %.4f%n", valorReal);
        System.out.printf("Valor aproximado: %.4f%n", valorAproximado);
        System.out.printf("Error numérico total: %.6f%n", error);
    }
}
```

---

### 📋 Salida Esperada

```
Valor real: 1.4142  
Valor aproximado: 1.4142  
Error numérico total: 0.000014
