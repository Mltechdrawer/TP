# Modularidad, Herencia y Reusabilidad

## Definiciones y ejemplos ilustrativos

### Sobrecarga de métodos

```java
//Sin sobrecarga
import java.util.Scanner;

public class SinSobrecarga {
    // Método para mostrar información con solo el nombre
    public void mostrarDatosNombre(String nombre) {
        System.out.println("Nombre: " + nombre);
    }

    // Método para mostrar información con nombre y edad
    public void mostrarDatosNombreYEdad(String nombre, int edad) {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        SinSobrecarga ejemplo = new SinSobrecarga();

        System.out.print("Introduce tu nombre: ");
        String nombre = scanner.nextLine();

        System.out.print("Introduce tu edad (o deja en blanco si no quieres ingresar la edad): ");
        String edadInput = scanner.nextLine();

        if (!edadInput.isEmpty()) {
            int edad = Integer.parseInt(edadInput);
            ejemplo.mostrarDatosNombreYEdad(nombre, edad);
        } else {
            ejemplo.mostrarDatosNombre(nombre);
        }
    }
}
```
---

```java
//Con sobrecarga
import java.util.Scanner;

public class ConSobrecarga {
    // Método sobrecargado para mostrar solo el nombre
    public void mostrarDatos(String nombre) {
        System.out.println("Nombre: " + nombre);
    }

    // Método sobrecargado para mostrar el nombre y la edad
    public void mostrarDatos(String nombre, int edad) {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ConSobrecarga ejemplo = new ConSobrecarga();

        System.out.print("Introduce tu nombre: ");
        String nombre = scanner.nextLine();

        System.out.print("Introduce tu edad (o deja en blanco si no quieres ingresar la edad): ");
        String edadInput = scanner.nextLine();

        if (!edadInput.isEmpty()) {
            int edad = Integer.parseInt(edadInput);
            ejemplo.mostrarDatos(nombre, edad); // Llama al método con dos parámetros
        } else {
            ejemplo.mostrarDatos(nombre); // Llama al método con un parámetro
        }
    }
}

```
---

```java
//Sin sobrecarga
public class CalculoAreaSinSobrecarga {

    // Método para calcular el área de un triángulo
    public double calcularAreaTriangulo(double base, double altura) {
        return (base * altura) / 2;
    }

    // Método para calcular el área de un rectángulo
    public double calcularAreaRectangulo(double longitud, double ancho) {
        return longitud * ancho;
    }

    // Método para calcular el área de un óvalo
    public double calcularAreaOvalo(double ejeMayor, double ejeMenor) {
        return Math.PI * (ejeMayor / 2) * (ejeMenor / 2);
    }

    // Método para calcular el área de un pentágono regular
    public double calcularAreaPentagono(double lado, double apotema) {
        return (5 * lado * apotema) / 2;
    }

    public static void main(String[] args) {
        CalculoAreaSinSobrecarga calculo = new CalculoAreaSinSobrecarga();

        // Calcular el área de un triángulo
        double areaTriangulo = calculo.calcularAreaTriangulo(5, 10);
        System.out.println("Área del triángulo: " + areaTriangulo);

        // Calcular el área de un rectángulo
        double areaRectangulo = calculo.calcularAreaRectangulo(8, 4);
        System.out.println("Área del rectángulo: " + areaRectangulo);
        
        // Calcular el área de un óvalo
        double areaOvalo = calculo.calcularAreaOvalo(10, 6);
        System.out.println("Área del óvalo: " + areaOvalo);

        // Calcular el área de un pentágono
        double areaPentagono = calculo.calcularAreaPentagono(6, 4);
        System.out.println("Área del pentágono: " + areaPentagono);
    }
}

```
---

```java
//Con sobrecarga
public class CalculoAreaSobrecarga {

    //  javac -encoding UTF-8 CalculoAreaSobrecarga.java

    // Método para calcular el área de un triángulo
    public double calcularArea(double basetriangulo, double altura) {
        return (basetriangulo * altura) / 2;
    }

    // Método para calcular el área de un rectángulo
    public double calcularArea(double longitud, double ancho) {
           return longitud * ancho;
        }

    // Método para calcular el área de un óvalo
    public double calcularArea(double ejeMayor, double ejeMenor, boolean esOvalo) {
        if (esOvalo) {
            return Math.PI * (ejeMayor / 2) * (ejeMenor / 2);
        }
        return 0;
    }

    // Método para calcular el área de un pentágono regular
    public double calcularArea(double lado, int numeroLados, double apotema) {
        if (numeroLados == 5) {
            return (5 * lado * apotema) / 2;
        }
        return 0;
    }

    public static void main(String[] args) {
        CalculoAreaSobrecarga calculo = new CalculoAreaSobrecarga();

        // Calcular el área de un triángulo
        double areaTriangulo = calculo.calcularArea(5, 10);
        System.out.println("Area del triángulo: " + areaTriangulo);

        // Calcular el área de un rectángulo
        double areaRectangulo = calculo.calcularArea(8, 4);
        System.out.println("Area del rectángulo: " + areaRectangulo);

        // Calcular el área de un óvalo
        double areaOvalo = calculo.calcularArea(10, 6, true);
        System.out.println("Area del óvalo: " + areaOvalo);

        // Calcular el área de un pentágono
        double areaPentagono = calculo.calcularArea(6, 5, 4);
        System.out.println("Area del pentágono: " + areaPentagono);
    }
}

```
---

```java
public class SistemaDeCerraduras {

    // Método para abrir una cerradura con una llave estándar
    public void abrir(String llave) {
        if (llave.equals("llaveEstandar")) {
            System.out.println("La cerradura se ha abierto con la llave estándar.");
        } else {
            System.out.println("Llave incorrecta. No se puede abrir la cerradura.");
        }
    }

    // Método sobrecargado para abrir una cerradura con una tarjeta magnética
    public void abrir(int codigoTarjeta) {
        if (codigoTarjeta == 1234) {
            System.out.println("La cerradura se ha abierto con la tarjeta magnética.");
        } else {
            System.out.println("Código de tarjeta incorrecto. No se puede abrir la cerradura.");
        }
    }

    // Método sobrecargado para abrir una cerradura con la llave maestra
    public void abrir(boolean esLlaveMaestra) {
        if (esLlaveMaestra) {
            System.out.println("La cerradura se ha abierto con la llave maestra.");
        } else {
            System.out.println("No tienes acceso con esta llave.");
        }
    }

    public static void main(String[] args) {
        SistemaDeCerraduras cerradura = new SistemaDeCerraduras();

        // Abrir la cerradura con una llave estándar
        cerradura.abrir("llaveEstandar"); // La cerradura se ha abierto con la llave estándar.

        // Abrir la cerradura con una tarjeta magnética
        cerradura.abrir(1234); // La cerradura se ha abierto con la tarjeta magnética.

        // Abrir la cerradura con la llave maestra
        cerradura.abrir(true); // La cerradura se ha abierto con la llave maestra.
    }
}

```
---

```java
import java.util.Scanner;

public class SistemaDeCerradurasElije {

    // Método para abrir una cerradura con una llave estándar
    public void abrir(String llave) {
        if (llave.equals("llaveEstandar")) {
            System.out.println("La cerradura se ha abierto con la llave estándar.");
        } else {
            System.out.println("Llave incorrecta. No se puede abrir la cerradura.");
        }
    }

    // Método sobrecargado para abrir una cerradura con una tarjeta magnética
    public void abrir(int codigoTarjeta) {
        if (codigoTarjeta == 1234) {
            System.out.println("La cerradura se ha abierto con la tarjeta magnética.");
        } else {
            System.out.println("Código de tarjeta incorrecto. No se puede abrir la cerradura.");
        }
    }

    // Método sobrecargado para abrir una cerradura con la llave maestra
    public void abrir(boolean esLlaveMaestra) {
        if (esLlaveMaestra) {
            System.out.println("La cerradura se ha abierto con la llave maestra.");
        } else {
            System.out.println("No tienes acceso con esta llave.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        SistemaDeCerradurasElije cerradura = new SistemaDeCerradurasElije();

        // Pedir al usuario que seleccione el tipo de cerradura a abrir
        System.out.println("Seleccione el tipo de cerradura que desea abrir:");
        System.out.println("1. Cerradura con llave estándar");
        System.out.println("2. Cerradura con tarjeta magnética");
        System.out.println("3. Cerradura con llave maestra");

        int opcion = scanner.nextInt();
        scanner.nextLine(); // Limpiar el buffer

        switch (opcion) {
            case 1:
                System.out.print("Ingrese la llave estándar: ");
                String llave = scanner.nextLine();
                cerradura.abrir(llave);
                break;

            case 2:
                System.out.print("Ingrese el código de la tarjeta magnética: ");
                int codigoTarjeta = scanner.nextInt();
                cerradura.abrir(codigoTarjeta);
                break;

            case 3:
                System.out.print("¿Tiene la llave maestra? (true/false): ");
                boolean esLlaveMaestra = scanner.nextBoolean();
                cerradura.abrir(esLlaveMaestra);
                break;

            default:
                System.out.println("Opción no válida. Por favor, seleccione una opción correcta.");
                break;
        }

        scanner.close();
    }
}

```
---

### This

```java
// Clase principal Persona
public class Persona {
    private String nombre;
    private int edad;

    // 1. Diferenciar entre variables de instancia y parámetros del método o constructor
    // Se usa this.nombre para diferenciar entre la variable de instancia nombre y el parámetro 
    //del constructor con el mismo nombre.
    
    public Persona(String nombre) {
        this.nombre = nombre; // 'this.nombre' se refiere a la variable de instancia
    }

    // Constructor adicional para el encadenamiento de constructores
    public Persona(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Método para mostrar los datos de la persona
    public void mostrar() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    // 2. Llamar a otros constructores de la misma clase (Constructor Chaining)
    // Se usa this("Nombre por defecto", 0) en el constructor Persona() para llamar 
    // al constructor que toma dos parámetros, evitando duplicar código.
    
    public Persona() {
        this("Nombre por defecto", 0); // Llama al constructor que toma dos parámetros
    }

    // 3. Pasar el objeto actual como argumento a otro método o constructor
    // El método mostrarUtilidades() utiliza this para pasar la referencia 
    // del objeto actual al método imprimir de la clase Utilidades.

    public void mostrarUtilidades() {
        Utilidades.imprimir(this); // Pasar el objeto actual al método 'imprimir'
    }

    // 4. Devolver la referencia actual de un método (Method Chaining)
    // Los métodos setNombre y setEdad devuelven this, lo que permite encadenar las 
    //llamadas de métodos en una sola línea (persona1.setNombre("Carlos").setEdad(25);).
    
    public Persona setNombre(String nombre) {
        this.nombre = nombre;
        return this; // Devuelve la referencia actual para encadenar
    }

    public Persona setEdad(int edad) {
        this.edad = edad;
        return this; // Devuelve la referencia actual para encadenar
    }

    // Getters para acceder a las variables privadas
    public String getNombre() {
        return nombre;
    }

    public int getEdad() {
        return edad;
    }

    public static void main(String[] args) {
        // 1. Diferenciar entre variables de instancia y parámetros
        Persona persona1 = new Persona("Juan");
        persona1.mostrar(); // Output: Nombre: Juan, Edad: 0

        // 2. Llamar a otros constructores de la misma clase (Constructor Chaining)
        Persona persona2 = new Persona();
        persona2.mostrar(); // Output: Nombre: Nombre por defecto, Edad: 0

        // 3. Pasar el objeto actual como argumento a otro método o constructor
        persona1.mostrarUtilidades(); // Output: Utilidades - Nombre: Juan, Edad: 0

        // 4. Devolver la referencia actual de un método (Method Chaining)
        persona1.setNombre("Carlos").setEdad(25); // Encadenamiento de métodos
        persona1.mostrar(); // Output: Nombre: Carlos, Edad: 25
    }
}

// Clase auxiliar para el ejemplo 3
class Utilidades {
    public static void imprimir(Persona persona) {
        // Utilizamos los getters para acceder a los atributos privados
        System.out.println("Utilidades - Nombre: " + persona.getNombre() + ", Edad: " + persona.getEdad());
    }
}
```
---

```java
public class PersonaChain {
    private String nombre;
    private int edad;

    // Constructor 1: Constructor sin parámetros
    public PersonaChain() {
        this("Nombre por defecto", 0); // Llama al constructor con dos parámetros
        System.out.println("Constructor sin parámetros llamado");
    }

    // Constructor 2: Constructor con un parámetro
    public PersonaChain(String nombre) {
        this(nombre, 0); // Llama al constructor con dos parámetros
        System.out.println("Constructor con un parámetro llamado");
    }

    // Constructor 3: Constructor con dos parámetros
    public PersonaChain(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
        System.out.println("Constructor con dos parámetros llamado");
    }

    // Método para mostrar los detalles de la persona
    public void mostrarDetalles() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    public static void main(String[] args) {
        // Crear un objeto usando el constructor sin parámetros
        PersonaChain persona1 = new PersonaChain();
        persona1.mostrarDetalles(); // Output: Nombre por defecto, Edad: 0

        // Crear un objeto usando el constructor con un parámetro
        PersonaChain persona2 = new PersonaChain("Juan");
        persona2.mostrarDetalles(); // Output: Nombre: Juan, Edad: 0

        // Crear un objeto usando el constructor con dos parámetros
        PersonaChain persona3 = new PersonaChain("Carlos", 25);
        persona3.mostrarDetalles(); // Output: Nombre: Carlos, Edad: 25
    }
}
```
---

### Estado de los objetos

```java
public class PersonaEstado {
    private String nombre; // Atributo que define parte del estado
    private int edad;      // Atributo que define parte del estado

    // Constructor para inicializar el estado del objeto
    public PersonaEstado(String nombre, int edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    // Método que modifica el estado del objeto
    public void cumplirAños() {
        this.edad++; // Cambia el estado al incrementar la edad
    }

    // Método para mostrar el estado actual del objeto
    public void mostrarEstado() {
        System.out.println("Nombre: " + nombre + ", Edad: " + edad);
    }

    public static void main(String[] args) {
        PersonaEstado persona = new PersonaEstado("Juan", 25); // Estado inicial
        persona.mostrarEstado(); // Output: Nombre: Juan, Edad: 25

        persona.cumplirAños(); // Cambia el estado
        persona.mostrarEstado(); // Output: Nombre: Juan, Edad: 26
    }
}

```
---

```java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

// Clase que representa un Producto
class Producto {
    private String nombre;
    private double precio;
    private int cantidad;

    public Producto(String nombre, double precio, int cantidad) {
        this.nombre = nombre;
        this.precio = precio;
        this.cantidad = cantidad;
    }

    public String getNombre() {
        return nombre;
    }

    public double getPrecio() {
        return precio;
    }

    public int getCantidad() {
        return cantidad;
    }

    public double calcularTotal() {
        return precio * cantidad;
    }

    @Override
    public String toString() {
        return nombre + " - Cantidad: " + cantidad + ", Precio Unitario: $" + precio + ", Total: $" + calcularTotal();
    }
}

// Clase que representa un Cliente
class Cliente {
    private String nombre;
    private String email;

    public Cliente(String nombre, String email) {
        this.nombre = nombre;
        this.email = email;
    }

    public String getNombre() {
        return nombre;
    }

    public String getEmail() {
        return email;
    }

    @Override
    public String toString() {
        return "Cliente: " + nombre + " (Email: " + email + ")";
    }
}

// Clase que representa un Pedido de Compra
class Pedido {
    private Cliente cliente;
    private List<Producto> productos;
    private Date fechaPedido;
    private String estado; // Ejemplos de estado: "Pendiente", "Enviando", "Entregado"

    public Pedido(Cliente cliente) {
        this.cliente = cliente;
        this.productos = new ArrayList<>();
        this.fechaPedido = new Date();
        this.estado = "Pendiente";
    }

    // Método para agregar un producto al pedido
    public void agregarProducto(Producto producto) {
        productos.add(producto);
    }

    // Método para calcular el total del pedido
    public double calcularTotalPedido() {
        double total = 0;
        for (Producto producto : productos) {
            total += producto.calcularTotal();
        }
        return total;
    }

    // Método para mostrar el estado completo del pedido
    public void mostrarEstado() {
        System.out.println("---- Estado del Pedido ----");
        System.out.println(cliente); // Llama al método toString() de Cliente
        System.out.println("Fecha del Pedido: " + fechaPedido);
        System.out.println("Estado del Pedido: " + estado);
        System.out.println("Productos en el pedido:");
        for (Producto producto : productos) {
            System.out.println("  " + producto); // Llama al método toString() de Producto
        }
        System.out.println("Total del Pedido: $" + calcularTotalPedido());
        System.out.println("----------------------------");
    }

    // Método para actualizar el estado del pedido
    public void actualizarEstado(String nuevoEstado) {
        this.estado = nuevoEstado;
    }
}

// Clase principal para probar el estado de un objeto complejo
public class SistemaPedidos {
    public static void main(String[] args) {
        // Crear un cliente
        Cliente cliente = new Cliente("Juan Pérez", "juan.perez@example.com");

        // Crear un pedido para el cliente
        Pedido pedido = new Pedido(cliente);

        // Agregar productos al pedido
        pedido.agregarProducto(new Producto("Laptop", 1200.00, 1));
        pedido.agregarProducto(new Producto("Mouse", 25.50, 2));
        pedido.agregarProducto(new Producto("Teclado", 45.99, 1));

        // Mostrar el estado completo del pedido
        pedido.mostrarEstado();

        // Actualizar el estado del pedido y mostrarlo de nuevo
        pedido.actualizarEstado("Enviando");
        System.out.println("\nEstado del pedido actualizado:");
        pedido.mostrarEstado();
    }
}

```
---

### Inicializar objetos con-sin constructores

```java
// VehiculoSinConstructor.java
public class VehiculoSinConstructor {
    // Atributos del vehículo
    String marca;
    String modelo;
    int año;
    double precio;

    // Método para mostrar los detalles del vehículo
    public void mostrarDetalles() {
        System.out.println("Marca: " + marca);
        System.out.println("Modelo: " + modelo);
        System.out.println("Año: " + año);
        System.out.println("Precio: $" + precio);
    }

    public static void main(String[] args) {
        // Creación e inicialización del objeto sin un constructor
        VehiculoSinConstructor vehiculo = new VehiculoSinConstructor();

        // Inicialización manual de los atributos
        vehiculo.marca = "Toyota";
        vehiculo.modelo = "Corolla";
        vehiculo.año = 2020;
        vehiculo.precio = 18000;

        // Mostrar los detalles del vehículo
        vehiculo.mostrarDetalles();
    }
}
```
---

```java
// VehiculoConConstructor.java
public class VehiculoConConstructor {
    // Atributos del vehículo
    private String marca;
    private String modelo;
    private int año;
    private double precio;

    // Constructor personalizado para inicializar los atributos
    public VehiculoConConstructor(String marca, String modelo, int año, double precio) {
        this.marca = marca;
        this.modelo = modelo;
        this.año = año;
        this.precio = precio;
    }

    // Método para mostrar los detalles del vehículo
    public void mostrarDetalles() {
        System.out.println("Marca: " + marca);
        System.out.println("Modelo: " + modelo);
        System.out.println("Año: " + año);
        System.out.println("Precio: $" + precio);
    }

    public static void main(String[] args) {
        // Creación e inicialización del objeto utilizando el constructor personalizado
        VehiculoConConstructor vehiculo = new VehiculoConConstructor("Honda", "Civic", 2021, 25000);

        // Mostrar los detalles del vehículo
        vehiculo.mostrarDetalles();
    }
}
```
---
```java
// LibroSinConstructor.java
public class LibroSinConstructor {
    // Atributos del libro
    String titulo;
    String autor;
    int paginas;
    double precio;

    // Método para mostrar los detalles del libro
    public void mostrarDetalles() {
        System.out.println("Título: " + titulo);
        System.out.println("Autor: " + autor);
        System.out.println("Páginas: " + paginas);
        System.out.println("Precio: $" + precio);
    }

    public static void main(String[] args) {
        // Creación del objeto utilizando el constructor por defecto
        LibroSinConstructor libro = new LibroSinConstructor();

        // Inicialización manual de los atributos
        libro.titulo = "Cien Años de Soledad";
        libro.autor = "Gabriel García Márquez";
        libro.paginas = 417;
        libro.precio = 19.99;

        // Mostrar los detalles del libro
        libro.mostrarDetalles();
    }
}
```
---

```java
// LibroConConstructor.java
public class LibroConConstructor {
    // Atributos del libro
    private String titulo;
    private String autor;
    private int paginas;
    private double precio;

    // Constructor personalizado para inicializar los atributos
    public LibroConConstructor(String titulo, String autor, int paginas, double precio) {
        this.titulo = titulo;
        this.autor = autor;
        this.paginas = paginas;
        this.precio = precio;
    }

    // Método para mostrar los detalles del libro
    public void mostrarDetalles() {
        System.out.println("Título: " + titulo);
        System.out.println("Autor: " + autor);
        System.out.println("Páginas: " + paginas);
        System.out.println("Precio: $" + precio);
    }

    public static void main(String[] args) {
        // Creación e inicialización del objeto utilizando el constructor personalizado
        LibroConConstructor libro = new LibroConConstructor("El Quijote", "Miguel de Cervantes", 500, 25.99);

        // Mostrar los detalles del libro
        libro.mostrarDetalles();
    }
}
```
---