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
// Ejemplo básico de Singleton en Java
public class Configuracion {

    // 1. Atributo estático que guarda la única instancia
    private static Configuracion instancia;

    // 2. Constructor privado → evita crear objetos desde fuera
    private Configuracion() {
        System.out.println("Inicializando configuración...");
    }

    // 3. Método público estático para obtener la instancia
    public static Configuracion getInstance() {
        if (instancia == null) {
            // Si aún no existe, se crea
            instancia = new Configuracion();
        }
        // Siempre devuelve la misma instancia
        return instancia;
    }

    // 4. Métodos de ejemplo
    public void mostrarMensaje() {
        System.out.println("Usando la misma configuración en toda la aplicación");
    }
}

// Ejemplo de uso
public class Main {
    public static void main(String[] args) {
        Configuracion c1 = Configuracion.getInstance();
        Configuracion c2 = Configuracion.getInstance();

        c1.mostrarMensaje();

        // Verificación: ambas referencias apuntan al mismo objeto
        System.out.println(c1 == c2); // true
    }
}
```


```java
public class Singleton {
    private static Singleton instanciaUnica;

    // Constructor privado para evitar la creación de nuevas instancias
    private Singleton() {}

    // Método de clase para obtener la instancia única
    public static Singleton obtenerInstancia() {
        if (instanciaUnica == null) {
            instanciaUnica = new Singleton();
        }
        return instanciaUnica;
    }

    public void mostrarMensaje() {
        System.out.println("Esta es la única instancia de Singleton.");
    }

    public static void main(String[] args) {
        Singleton instancia = Singleton.obtenerInstancia();
        instancia.mostrarMensaje();
    }
}
```
---