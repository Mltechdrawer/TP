# Modularidad, Herencia y Reusabilidad

## Definiciones y ejemplos ilustrativos

### Atributos de clase

```java
public class Contador {
    private static int numInstancias = 0; // Atributo de clase

    public Contador() {
        numInstancias++; // Incrementar contador en cada nueva instancia
    }

    // Método de clase para obtener el número de instancias creadas
    public static int getNumInstancias() {
        return numInstancias;
    }

    public static void main(String[] args) {
        new Contador(); // Primera instancia
        new Contador(); // Segunda instancia

        System.out.println("Número de instancias creadas: " + Contador.getNumInstancias());
        // Output: Número de instancias creadas: 2
    }
}
```
---

### Métodos de clase

```java
public class Calculadora {
    // Método de clase para calcular el cuadrado de un número
    // No es necesario acceder ni modificar los atributos de una instancia específica
    // No es necesario crear un objeto
    public static int calcularCuadrado(int numero) {
        return numero * numero;
    }

    public static void main(String[] args) {
        int resultado = Calculadora.calcularCuadrado(5);
        System.out.println("El cuadrado de 5 es: " + resultado);
        // Output: El cuadrado de 5 es: 25
    }
}
```
---
### Constantes

```java
public class Constantes {
    public static final double PI = 3.141592653589793;

    public static void main(String[] args) {
        System.out.println("Valor de PI: " + Constantes.PI);
    }
}
```
---

### Singleton

```java
// Singleton1.java
// Ejemplo de Singleton listo para ejecutarse en un único fichero con "Run" de VS Code.

public class Singleton1 {

    // Instancia única (volatile para doble comprobación segura en multihilo)
    private static volatile Singleton1 instancia;

    // Constructor privado: evita instanciación externa
    private Singleton1() {
        System.out.println("Inicializando configuración...");
    }

    // Punto de acceso global con double-checked locking (seguro desde Java 5+)
    public static Singleton1 getInstance() {
        if (instancia == null) {
            synchronized (Singleton1.class) {
                if (instancia == null) {
                    instancia = new Singleton1();
                }
            }
        }
        return instancia;
    }

    public void mostrarMensaje() {
        System.out.println("¡Hola desde el Singleton!");
    }

    // Método main en el MISMO fichero/clase para ejecutarlo directamente
    public static void main(String[] args) {
        Singleton1 c1 = Singleton1.getInstance();
        Singleton1 c2 = Singleton1.getInstance();

        c1.mostrarMensaje();

        // Verificación: ambas referencias apuntan al mismo objeto
        System.out.println("¿Es la misma instancia? " + (c1 == c2));
    }
}

```


```java
public class Singleton2 {
    private static Singleton2 instanciaUnica;

    // Constructor privado para evitar la creación de nuevas instancias
    private Singleton2() {}

    // Método de clase para obtener la instancia única
    public static Singleton2 obtenerInstancia() {
        if (instanciaUnica == null) {
            instanciaUnica = new Singleton2();
        }
        return instanciaUnica;
    }

    public void mostrarMensaje() {
        System.out.println("Esta es la única instancia de Singleton.");
    }

    public static void main(String[] args) {
        Singleton2 instancia = Singleton2.obtenerInstancia();
        instancia.mostrarMensaje();
    }
}

```
---