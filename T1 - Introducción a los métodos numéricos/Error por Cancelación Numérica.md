
## Tema 1: Error por Cancelación Numérica

# ¿Qué es?

La cancelación numérica ocurre cuando se restan dos números que son muy cercanos entre sí, lo que provoca una pérdida significativa de cifras significativas. Esta pérdida de precisión puede resultar en errores notables en cálculos posteriores, especialmente cuando los resultados intermedios se utilizan como base para otras operaciones.

Este tipo de error es muy común en ciertos algoritmos y fórmulas, por lo que se recomienda reescribir las expresiones algebraicas o utilizar formulaciones alternativas para evitar cancelaciones. Identificar y prevenir cancelaciones numéricas es clave para diseñar algoritmos estables y confiables.

---

### Ventajas y Desventajas de Identificar Cancelación Numérica

**Ventajas:**
- Permite detectar pérdidas significativas de precisión en cálculos matemáticos.
- Ayuda a rediseñar algoritmos para evitar errores graves en resultados.
- Mejora la confiabilidad y estabilidad de las soluciones numéricas.

**Desventajas:**
- Puede requerir reformulaciones matemáticas más complejas.
- Aumenta el costo computacional en algunos casos al buscar alternativas estables.
- No siempre es fácil de detectar en cálculos largos o algoritmos extensos.

---

## Desarrollo

### Pseudocódigo

```text
Inicio
  Definir a como real
  Definir b como real
  Definir resultado como real
  a = 1.0000001
  b = 1.0000000
  resultado = a - b
  Imprimir "Resultado esperado: 0.0000001"
  Imprimir "Resultado real: ", resultado
  Imprimir "Error por cancelación: ", abs(0.0000001 - resultado)
Fin
```

---

### Código base en Java

```java
public class CodigoBaseCancelacion {
    public static void main(String[] args) {
        double a = 1.0000001;
        double b = 1.0000000;
        double resultado = a - b;

        System.out.println("Resultado esperado: 0.0000001");
        System.out.println("Resultado real: " + resultado);
        System.out.println("Error por cancelación: " + Math.abs(0.0000001 - resultado));
    }
}
```

---

### Ejemplo funcional en Java

```java
public class CancelacionNumerica {
    public static void main(String[] args) {
        double a = 1.0000001;
        double b = 1.0000000;

        double resultado = a - b;
        double esperado = 0.0000001;

        System.out.printf("Resultado calculado: %.7f%n", resultado);
        System.out.printf("Resultado esperado: %.7f%n", esperado);
        System.out.println("Error por cancelación: " + Math.abs(esperado - resultado));
    }
}
```

---

### Caso de prueba:

```text
Resultado calculado: 0.0000001
Resultado esperado: 0.0000001
Error por cancelación: 1.3552527156068805E-15
```
### [<- Regresar a T1 - Introducción a los Métodos Numéricos](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T1%20-%20Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20num%C3%A9ricos/Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20n%C3%BAmericos.md)
