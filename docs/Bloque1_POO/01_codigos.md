# Tema · Repaso de Programación Orientada a Objetos

**Ejemplos de código** 

---

<!-- Botón/iframe para ejecutar --> 
<iframe frameBorder="0" width="100%" height="520" src="https://onecompiler.com/embed/java"></iframe>

### Velocidad de ejecución

## Java

```java
public class VelocidadJava {
    public static void main(String[] args) {
        long startTime = System.nanoTime();

        int suma = 0;
        for (int i = 0; i < 1000000; i++) {
            suma += i;
        }

        long endTime = System.nanoTime();
        System.out.println("Tiempo de ejecución en Java: " + (endTime - startTime) + " nanosegundos.");
    }
}
// Java. Valores aproximados a: 3927653 nanosegundos (unos 4 milisegundos)
```
---
```python
import time

start_time = time.time()

suma = 0
for i in range(1000000):
    suma += i

end_time = time.time()
print("Tiempo de ejecución en Python:", (end_time - start_time), "segundos")

// Python. Valores aproximados a: 0.13556790351867676 segundos (unos 135 milisegundos)
```

### Abstracción

---
```java
// Clase abstracta que define el comportamiento de un Vehiculo
abstract class Vehiculo {
    // Método abstracto: las subclases deben implementar cómo encender el vehículo
    public abstract void encender();

    // Método abstracto: las subclases deben implementar cómo apagar el vehículo
    public abstract void apagar();

    // Método común que puede ser usado por todas las subclases
    public void mostrarTipo() {
        System.out.println("Este es un vehículo.");
    }
}

// Clase concreta que extiende de la clase abstracta Vehiculo
class Coche extends Vehiculo {
    // Implementación del método encender
    public void encender() {
        System.out.println("El coche está encendido.");
    }

    // Implementación del método apagar
    public void apagar() {
        System.out.println("El coche está apagado.");
    }
}

// Clase principal que usa la abstracción
public class Main {  
    public static void main(String[] args) {
        // Creamos un objeto de tipo Coche
        Coche miCoche = new Coche();
        
        // Usamos los métodos abstractos implementados
        miCoche.encender();
        miCoche.mostrarTipo();
        miCoche.apagar();

        // Intentar crear un objeto de la clase abstracta (esto va a generar un error de compilación)
        Vehiculo miVehiculo = new Vehiculo();  // <-- Esto genera un error
    }
}
```
---
### Encapsulamiento
---
```java
class Circulo {
    // Al ser private solo los métodos de esta clase pueden acceder a ellos
    private String color;
    private int radio;
    private int x, y;

    // El constructor permite crear objetos círculo con valores iniciales para sus atributos 
    public Circulo(String color, int radio, int x, int y) {
        this.color = color;
        this.radio = radio;
        this.x = x;
        this.y = y;
    }
    // Métodos que pueden alterar  los atributos de forma controlada
        public void cambiarTamano(int nuevoRadio) {
        this.radio = nuevoRadio;
    }

    public void cambiarPosicion(int nuevaX, int nuevaY) {
        this.x = nuevaX;
        this.y = nuevaY;
    }
    // Encapsula la representación del objeto
    public void mostrar() {
        System.out.println("Círculo de color " + color + ", radio " + radio +
                           ", en la posición (" + x + ", " + y + ")");
    }
}
// Clase principal. Ejemplo de uso de encapsulamiento.
public class Main {
    public static void main(String[] args) {
        Circulo circulo1 = new Circulo("Rojo", 50, 100, 100);
        Circulo circulo2 = new Circulo("Verde", 30, 200, 150);
        Circulo circulo3 = new Circulo("Azul", 70, 300, 250);

        circulo1.mostrar();
        circulo2.mostrar();
        circulo3.mostrar();
        // Solo llama a los métodos públicos, no le interesa como se realizan
        circulo1.cambiarTamano(80);
        circulo1.cambiarPosicion(150, 200);

        circulo1.mostrar();
    }
}

```
---
### Herencia
---
```java
class Animal {
    private final String nombre;
    Animal(String nombre) { this.nombre = nombre; }
    public void sonar() { System.out.println(nombre + ": hace un sonido genérico"); }
    public String getNombre() { return nombre; }
}

class Perro extends Animal {
    Perro(String nombre) { super(nombre); }
    // Anotación de un método, que indica que se sobreescribe
    @Override public void sonar() { System.out.println(getNombre() + ": ¡guau!"); }
    public void traerPelota() { System.out.println(getNombre() + " trae la pelota"); }
}

public class Main { // ← Asegúrate de que el archivo se llame Main.java
    public static void main(String[] args) {
        Animal a = new Animal("Animal");
        Animal p = new Perro("Toby");
        a.sonar();
        p.sonar();
        if (p instanceof Perro) ((Perro) p).traerPelota();
    }
}
```
---
### Polimorfismo
---
```java
// Superclase/abstracción
abstract class Figura {
    private final String nombre;
    Figura(String nombre) { this.nombre = nombre; }

    public String getNombre() { return nombre; }

    // Método polimórfico: cada subclase lo implementa a su manera
    public abstract double area();

    // Comportamiento común que también puede sobrescribirse
    public void dibujar() {
        System.out.println("Dibujando " + nombre + " genérico");
    }
}

// Subclase 1: Circulo
class Circulo extends Figura {
    private final double radio;
    Circulo(double radio) {
        super("círculo");
        this.radio = radio;
    }
    @Override public double area() { return Math.PI * radio * radio; }
    @Override public void dibujar() { System.out.println("Dibujando un círculo"); }
}

// Subclase 2: Rectangulo
class Rectangulo extends Figura {
    private final double ancho, alto;
    Rectangulo(double ancho, double alto) {
        super("rectángulo");
        this.ancho = ancho; this.alto = alto;
    }
    @Override public double area() { return ancho * alto; }
    // Usa el dibujar() heredado si no lo sobrescribes
}

public class Main {
    public static void main(String[] args) {
        // Polimorfismo: misma referencia (Figura), distintos objetos concretos
        Figura[] figuras = { new Circulo(2.0), new Rectangulo(3.0, 4.0) };

        for (Figura f : figuras) {
            f.dibujar();                              // despacho dinámico
            System.out.printf("Área de %s: %.2f%n", 
                              f.getNombre(), f.area()); // llama al override adecuado
        }

        // Otra muestra de polimorfismo en un método que recibe la superclase
        procesar(new Circulo(5.0));
        procesar(new Rectangulo(2.0, 6.0));
    }

    static void procesar(Figura f) {
        System.out.println("Procesando " + f.getClass().getSimpleName()
                           + " con área " + f.area());
    }
}
```
---
### Clases y objetos
---
```java
class Persona {
    String nombre;
    int edad;

    void saludar() {
        System.out.println("Hola, me llamo " + nombre);
    }
}

// Creación de un objeto
Persona p1 = new Persona();
p1.nombre = "Ana";
p1.edad = 25;
p1.saludar();
```
---

