### 🔙 [← Regresar a T1 - Introducción a los Métodos Numéricos](https://github.com/Juan200519287393u83/Metodos_Numericos/blob/main/T1%20-%20Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20num%C3%A9ricos/Introducci%C3%B3n%20a%20los%20m%C3%A9todos%20n%C3%BAmericos.md)

# ⚠️ Tema 1: Error de Truncamiento

---

### ❓ ¿Qué es?

El **error de truncamiento** ocurre cuando se interrumpe o simplifica una operación matemática infinita o continua para poder calcularla de forma finita. Por ejemplo, al usar la serie de Taylor para aproximar funciones, se corta la serie después de un número limitado de términos, introduciendo un error al omitir los restantes.

La magnitud del error depende del número de términos usados: más términos, menor error, pero mayor costo computacional. Existe un equilibrio entre precisión y eficiencia que debe evaluarse según el problema.

---

### ✅ Ventajas y ❌ Desventajas

| ✅ **Ventajas**                                                | ❌ **Desventajas**                                                        |
| ------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Permite aproximar funciones complejas imposibles de calcular  | Introduce un error inherente que puede acumularse                        |
| Control directo del balance precisión vs. costo computacional | Requiere análisis cuidadoso para elegir número adecuado de términos      |
| Útil en aplicaciones prácticas con aproximaciones aceptables  | Puede ser costoso si se necesitan muchos términos para precisión deseada |

---

### 📝 Pseudocódigo

```text
Inicio
  Función funciónReal(x)
    Retornar exp(x)
  Fin Función

  Función aproximacionTaylor(x, n)
    Definir suma como real
    Definir i como entero
    suma = 0
    Para i = 0 hasta n
      suma = suma + (x^i) / factorial(i)
    Fin Para
    Retornar suma
  Fin Función

  Definir x como real
  Definir n como entero
  Definir real como real
  Definir aproximado como real
  x = 1.0
  n = 3
  real = funciónReal(x)
  aproximado = aproximacionTaylor(x, n)
  Imprimir "Valor real: ", real
  Imprimir "Aproximación: ", aproximado
  Imprimir "Error de truncamiento: ", abs(real - aproximado)
Fin
```

---

### 💻 Código base en Java

```java
public class CodigoBaseTruncamiento {
    public static double funcionReal(double x) {
        return Math.exp(x);
    }

    public static double aproximacionTaylor(double x, int n) {
        double suma = 0;
        for (int i = 0; i <= n; i++) {
            double factorial = 1;
            for (int j = 1; j <= i; j++) {
                factorial *= j;
            }
            suma += Math.pow(x, i) / factorial;
        }
        return suma;
    }

    public static void main(String[] args) {
        double x = 1.0;
        int n = 3;
        double real = funcionReal(x);
        double aproximado = aproximacionTaylor(x, n);

        System.out.println("Valor real: " + real);
        System.out.println("Aproximación: " + aproximado);
        System.out.println("Error de truncamiento: " + Math.abs(real - aproximado));
    }
}
```

---

### 🛠 Ejemplo funcional en Java

```java
public class ErrorTruncamiento {
    public static double taylorExp(double x, int n) {
        double suma = 1.0;
        double term = 1.0;

        for (int i = 1; i <= n; i++) {
            term *= x / i;
            suma += term;
        }

        return suma;
    }

    public static void main(String[] args) {
        double x = 1.0;
        int n = 3;
        double real = Math.exp(x);
        double aproximado = taylorExp(x, n);

        System.out.printf("Valor real: %.3f%n", real);
        System.out.printf("Aproximación (n=3): %.3f%n", aproximado);
        System.out.printf("Error de truncamiento: %.3f%n", Math.abs(real - aproximado));
    }
}
```

---

### 📋 Caso de prueba:

```text
Valor real: 2.718
Aproximación (n=3): 2.667
Error de truncamiento: 0.051
```
