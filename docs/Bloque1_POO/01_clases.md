# Tipos de clases en Java

## Clase concreta (Concrete Class)
Una clase “normal”, que implementa todos sus métodos y puede instanciarse directamente.

**Ejemplo:**
```java
public class Coche {
    void arrancar() {
        System.out.println("Coche arrancando");
    }
}
```

---

## Clase abstracta (Abstract Class)
Declarada con la palabra clave `abstract`. Puede contener métodos abstractos (sin cuerpo) y métodos implementados.

**Ejemplo:**
```java
public abstract class Animal {
    abstract void sonido();
    void dormir() {
        System.out.println("El animal duerme");
    }
}
```

---

## Clase final (Final Class)
Marcada con `final`, no puede ser extendida.

**Ejemplo:**
```java
public final class Utilidades {
    public static int sumar(int a, int b) {
        return a + b;
    }
}
```

---

## Clase estática anidada (Static Nested Class)
Clase declarada dentro de otra clase con `static`. No depende de una instancia exterior.

**Ejemplo:**
```java
public class Externa {
    static class Interna {
        void mostrar() {
            System.out.println("Clase estática anidada");
        }
    }
}
```

---

## Clase interna / miembro (Inner Class)
Clase definida dentro de otra clase, y depende de su instancia.

```java
public class Externa {
    class Interna {
        void saludar() {
            System.out.println("Hola desde clase interna");
        }
    }
}
```

---

## Clase local
Clase definida dentro de un método.

```java
public void metodo() {
    class Local {
        void imprimir() {
            System.out.println("Clase local en un método");
        }
    }
    Local l = new Local();
    l.imprimir();
}
```

---

## Clase anónima (Anonymous Class)
Clase sin nombre que implementa una interfaz o hereda de una clase para ser usada “en línea”.

```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hola mundo");
    }
};
```

---

## Clase POJO (Plain Old Java Object)
Clase simple usada para representar datos. Tiene variables privadas y métodos getter/setter.

```java
public class Persona {
    private String nombre;
    public String getNombre() { return nombre; }
    public void setNombre(String n) { this.nombre = n; }
}
```

---

## Clase sellada (Sealed Class) – Java 15+
Permite controlar qué clases pueden heredar de ella.

```java
public sealed class Figura permits Circulo, Cuadrado { }
public final class Circulo extends Figura { }
public final class Cuadrado extends Figura { }
```

---

## Tabla comparativa de tipos de clases

| Tipo de clase             | Características principales                                                                                      | Cuándo emplearlo                                                                 |
|---------------------------|------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| **Clase concreta**        | Implementa todos los métodos. Instanciable. | Cuando necesitas una clase funcional sin abstracción. |
| **Clase abstracta**       | Puede tener métodos abstractos y concretos. No instanciable. | Para definir una estructura base común. |
| **Clase final**           | No puede heredarse. | Cuando no debe modificarse su comportamiento. |
| **Clase estática anidada**| Clase dentro de otra con `static`. | Para agrupar clases sin depender de instancia externa. |
| **Clase interna / miembro**| Clase dentro de otra, dependiente de su instancia. | Para encapsular lógica muy ligada a la clase externa. |
| **Clase local**           | Definida dentro de un método. | Para lógica auxiliar dentro de métodos. |
| **Clase anónima**         | Clase sin nombre, creada en línea. | Para implementar comportamientos rápidos y puntuales. |
| **Clase POJO**            | Solo atributos y getters/setters. | Para representar datos o entidades. |
| **Clase sellada**         | Controla qué clases pueden heredar de ella. | Para jerarquías seguras y controladas. |

---
