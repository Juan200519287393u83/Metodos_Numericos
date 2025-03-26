# ⚠️ Tema 1: Incertidumbre en los Datos

---

### ❓ ¿Qué es?

En numerosos problemas prácticos, los valores de entrada no se conocen con total exactitud. Esta imprecisión puede originarse por limitaciones en los instrumentos de medición, ruido en las pruebas experimentales, redondeos o estimaciones aproximadas. Por lo tanto, aun empleando un método numérico preciso, los resultados pueden verse afectados por errores inherentes a los datos iniciales.

Esta incertidumbre puede propagarse y generar desviaciones considerables en el resultado final, especialmente en problemas donde pequeñas variaciones afectan mucho el resultado (problemas mal condicionados). Por eso, se recomienda realizar análisis de sensibilidad y estimaciones para evaluar su impacto.

---

### ✅ Ventejas y ❌ Deventajas 

| ✅ **Ventejas**                                         | ❌ **Deventajas**                                              |
| -------------------------------------------------------- | --------------------------------------------------------------- |
| Permite abordar problemas con datos que no son exactos   | Introduce incertidumbre que complica la interpretación          |
| Facilita la evaluación de posibles rangos de resultados  | Requiere técnicas adicionales para evaluar y controlar errores  |
| Apoya la toma de decisiones considerando las variaciones | Puede incrementar la carga computacional por análisis múltiples |

---

### 📝 Pseudocódigo

```text
Inicio
  Definir valorMedido como real
  Definir margenError como real
  Definir limiteInferior como real
  Definir limiteSuperior como real
  valorMedido = 9.81
  margenError = 0.05
  limiteInferior = valorMedido - margenError
  limiteSuperior = valorMedido + margenError
  Imprimir "Valor medido: ", valorMedido
  Imprimir "Intervalo de incertidumbre: [", limiteInferior, ", ", limiteSuperior, "]"
Fin
```

---

### 💻 Código base en Java

```java
public class CodigoBaseIncertidumbre {
    public static void main(String[] args) {
        double valorMedido = 9.81;
        double margenError = 0.05;
        double limiteInferior = valorMedido - margenError;
        double limiteSuperior = valorMedido + margenError;

        System.out.println("Valor medido: " + valorMedido);
        System.out.println("Intervalo de incertidumbre: [" + limiteInferior + ", " + limiteSuperior + "]");
    }
}
```

---

### 🛠 Ejemplo funcional en Java

```java
public class IncertidumbreDatos {
    public static void main(String[] args) {
        double medicion = 100.0;
        double tolerancia = 2.5;
        double limiteInferior = medicion - tolerancia;
        double limiteSuperior = medicion + tolerancia;

        System.out.printf("Medición: %.3f%n", medicion);
        System.out.printf("Intervalo estimado: [%.3f, %.3f]%n", limiteInferior, limiteSuperior);
        System.out.printf("Incertidumbre: ±%.3f%n", tolerancia);
    }
}
```

---

### 📋 Resultado esperado:

```text
Medición: 100.000
Intervalo estimado: [97.500, 102.500]
Incertidumbre: ±2.500
```
