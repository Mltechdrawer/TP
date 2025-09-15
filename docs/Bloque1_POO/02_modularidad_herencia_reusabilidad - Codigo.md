# Modularidad, Herencia y Reusabilidad

## Introducción
En el desarrollo de software, conceptos como **modularidad**, **herencia** y **reusabilidad** son esenciales para crear programas más claros, mantenibles y escalables. Estos principios permiten organizar el código, reducir la duplicación y facilitar la evolución de los proyectos.

---

## Modularidad
La **modularidad** consiste en dividir un programa en componentes o módulos independientes, de manera que cada uno tenga una responsabilidad clara.

### Características
- Un módulo puede desarrollarse, probarse y mantenerse de forma aislada.
- Facilita localizar y corregir errores.
- Permite ampliar la funcionalidad sin afectar a todo el sistema.

### Ejemplo en Java
```java
public class Calculadora {
    public int suma(int a, int b) { return a + b; }
    public int resta(int a, int b) { return a - b; }
    public int multiplica(int a, int b) { return a * b; }
    public int divide(int a, int b) {
        if (b == 0) throw new ArithmeticException("División por cero");
        return a / b;
    }
}
```
En este caso, toda la lógica matemática se encuentra encapsulada en la clase `Calculadora`, separada de la interacción con el usuario.

---

## Herencia
La **herencia** permite definir nuevas clases basadas en otras ya existentes, reutilizando atributos y métodos y añadiendo o especializando funcionalidades.

### Conceptos clave
- **Superclase (clase base)**: clase original de la que heredan otras.
- **Subclase (clase derivada)**: clase que extiende la funcionalidad de la superclase.

### Ejemplo en Java
```java
public class Persona {
    protected String nombre;
    protected String telefono;

    public Persona(String nombre, String telefono) {
        this.nombre = nombre;
        this.telefono = telefono;
    }
}

public class Alumno extends Persona {
    private int numExpediente;

    public Alumno(String nombre, String telefono, int numExpediente) {
        super(nombre, telefono);
        this.numExpediente = numExpediente;
    }
}
```

En este ejemplo, `Alumno` hereda de `Persona`, reutilizando los atributos y añadiendo un campo propio.

---

## Polimorfismo y Clases Abstractas
El **polimorfismo** permite que una misma referencia pueda apuntar a objetos de diferentes clases, ejecutando el método correspondiente según el tipo del objeto real.

### Ejemplo de clase abstracta
```java
public abstract class FiguraGeometrica {
    protected float altura;
    public FiguraGeometrica(float altura) { this.altura = altura; }

    public abstract float areaBase();
    public abstract float perimetroBase();

    public float volumen() { return altura * areaBase(); }
}
```

Subclases como `Cubo` o `Cilindro` implementan los métodos abstractos adaptados a su forma.

---

## Interfaces
Una **interfaz** define un conjunto de métodos sin implementación. Las clases que la implementan son responsables de definir su funcionamiento.

### Ejemplo en Java
```java
interface Acuatico {
    void nadar();
}

interface Terrestre {
    void correr();
}

public class Cocodrilo implements Acuatico, Terrestre {
    public void nadar() { System.out.println("El cocodrilo nada"); }
    public void correr() { System.out.println("El cocodrilo corre"); }
}
```

Las interfaces permiten simular la herencia múltiple y promueven la flexibilidad del diseño.

---

## Reusabilidad
La **reusabilidad** consiste en emplear código existente en diferentes contextos o proyectos, evitando duplicaciones.

### Beneficios
- Reducción de errores y duplicaciones.
- Mayor rapidez en el desarrollo.
- Código más consistente y probado.

### Ejemplo de reutilización mediante herencia
```java
public class CalculadoraAvanzada extends Calculadora {
    public double potencia(double base, double exponente) {
        return Math.pow(base, exponente);
    }
}
```

Aquí `CalculadoraAvanzada` reutiliza todos los métodos de `Calculadora` y añade nuevas funcionalidades.

---

## Conclusión
- La **modularidad** favorece el orden y la claridad.  
- La **herencia** y el **polimorfismo** permiten extender y generalizar comportamientos.  
- La **reusabilidad** reduce costes y facilita el mantenimiento.  
- Las **interfaces** aportan flexibilidad para diseñar sistemas más escalables.

Estos principios son fundamentales en la **Programación Orientada a Objetos (POO)** y constituyen la base de un software robusto y adaptable.
