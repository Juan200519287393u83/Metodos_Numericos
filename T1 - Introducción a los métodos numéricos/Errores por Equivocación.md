### 🔙 [← Regresar a T1 - Introducción a los Métodos Numéricos](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T1%20-%20Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20num%C3%A9ricos/Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20n%C3%BAmericos.md)

# ⚠️ Tema 1: Errores por Equivocación

---

### ❓ ¿Qué es?

Los **errores por equivocación** o **errores humanos** ocurren durante la formulación, programación o ejecución de un método numérico. Pueden ser errores al ingresar datos, escribir fórmulas incorrectas, seleccionar mal un método o interpretar erróneamente resultados.

Aunque no son inherentes a los métodos numéricos, su impacto puede ser crítico. Por ello, es fundamental validar resultados, revisar código y verificar entradas y salidas para minimizarlos.

---

### ✅ Ventajas y ❌ Desventajas

| ✅ **Ventajas**                                             | ❌ **Desventajas**                                             |
| ---------------------------------------------------------- | ------------------------------------------------------------- |
| Promueven mejores prácticas como validación y verificación | Son impredecibles y dependen del factor humano                |
| Previenen problemas mayores mediante revisiones rigurosas  | Requieren tiempo extra para depuración y corrección           |
| Mejoran la calidad del código y resultados                 | Pueden impactar significativamente si no se detectan a tiempo |

---

### 📝 Pseudocódigo

```text
Inicio
  Definir areaCorrecta como real
  Definir areaConError como real
  areaCorrecta = π * (5^2)
  areaConError = π * (10^2)
  Imprimir "Área correcta: ", areaCorrecta
  Imprimir "Área con error: ", areaConError
  Imprimir "Diferencia por equivocación: ", abs(areaCorrecta - areaConError)
Fin
```

---

### 💻 Código base en Java

```java
public class CodigoBaseEquivocacion {
    public static void main(String[] args) {
        double areaCorrecta = Math.PI * Math.pow(5, 2);
        double areaConError = Math.PI * Math.pow(10, 2);

        System.out.println("Área correcta: " + areaCorrecta);
        System.out.println("Área con error: " + areaConError);
        System.out.println("Diferencia por equivocación: " + Math.abs(areaCorrecta - areaConError));
    }
}
```

---

### 🛠 Ejemplo funcional en Java

```java
public class ErrorEquivocacion {
    public static void main(String[] args) {
        double radio = 5.0;
        double areaIncorrecta = Math.PI * radio * 2;
        double areaCorrecta = Math.PI * Math.pow(radio, 2);
        double diferencia = Math.abs(areaCorrecta - areaIncorrecta);

        System.out.printf("Área incorrecta: %.3f%n", areaIncorrecta);
        System.out.printf("Área correcta: %.3f%n", areaCorrecta);
        System.out.printf("Diferencia por equivocación: %.3f%n", diferencia);
    }
}
```

---

### 📋 Caso de prueba:

```text
Área incorrecta: 31.416
Área correcta: 78.540
Diferencia por equivocación: 47.124
```
