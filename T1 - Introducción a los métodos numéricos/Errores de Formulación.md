### 🔙 [← Regresar a T1 - Introducción a los Métodos Numéricos](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T1%20-%20Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20num%C3%A9ricos/Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20n%C3%BAmericos.md)

# ⚠️ Tema 1: Errores de Formulación

---

### ❓ ¿Qué es?

Los **errores de formulación** ocurren cuando el modelo matemático que representa un problema real es incorrecto o incompleto. Para simplificar problemas complejos, a menudo se hacen suposiciones o simplificaciones que alejan el modelo de la realidad, introduciendo errores que no dependen del método numérico sino de la representación inadecuada del fenómeno.

Estos errores pueden ser peligrosos porque, aunque el modelo funcione bajo ciertas condiciones, una formulación errónea puede invalidar completamente los resultados.

---

### ✅ Ventajas y ❌ Desventajas

| ✅ **Ventajas**                                                 | ❌ **Desventajas**                                       |
| -------------------------------------------------------------- | ------------------------------------------------------- |
| Permite resolver problemas complejos mediante simplificaciones | Simplificaciones pueden causar errores significativos   |
| Reduce tiempo y recursos computacionales                       | Difícil detectar modelos inadecuados sin pruebas reales |
| Facilita la comprensión y comunicación del problema            | Resultados pueden ser engañosos si suposiciones fallan  |

---

### 📝 Pseudocódigo

```text
Inicio
  Definir g como real
  Definir t como real
  Definir distanciaIdeal como real
  g = 9.81
  t = 3.0
  distanciaIdeal = 0.5 * g * t^2
  Imprimir "Distancia sin resistencia del aire: ", distanciaIdeal
  Imprimir "Nota: Se desprecia la resistencia del aire (modelo simplificado)"
Fin
```

---

### 💻 Código Base en Java

```java
public class CodigoBaseFormulacion {
    public static void main(String[] args) {
        double g = 9.81;
        double t = 3.0;
        double distanciaIdeal = 0.5 * g * t * t;

        System.out.println("Distancia sin resistencia del aire: " + distanciaIdeal);
        System.out.println("Nota: Se desprecia la resistencia del aire (modelo simplificado)");
    }
}
```

---

### 🛠 Ejemplo Funcional en Java

```java
public class ErrorFormulacion {
    public static void main(String[] args) {
        double g = 9.81;
        double tiempo = 3.0;
        double distanciaIdeal = 0.5 * g * Math.pow(tiempo, 2);
        double distanciaEsperada = 44.145; // Valor teórico para comparación

        System.out.printf("Distancia calculada (modelo ideal): %.3f metros%n", distanciaIdeal);
        System.out.printf("Distancia esperada: %.3f metros%n", distanciaEsperada);
        System.out.println("Error por formulación: " + Math.abs(distanciaEsperada - distanciaIdeal));
        System.out.println("Nota: No se considera resistencia del aire.");
    }
}
```

---

### 📋 Caso de prueba

```text
Distancia calculada (modelo ideal): 44.145 metros
Distancia esperada: 44.145 metros
Error por formulación: 0.0
Nota: No se considera resistencia del aire.
```
