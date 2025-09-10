# Tema · Repaso de Programación Orientada a Objetos

La **Programación Orientada a Objetos (POO)** es un paradigma de programación que organiza el software en torno a entidades llamadas *objetos*, los cuales agrupan datos y comportamientos relacionados. Este enfoque resulta fundamental en la ingeniería del software moderna y sirve como base para muchos lenguajes de programación actuales, como Java, C++ o Python.

---

## 1. Principios básicos de la POO

### Abstracción
La abstracción consiste en identificar las características esenciales de una entidad del mundo real y representarlas en un modelo computacional.  
Ejemplo: una clase `Coche` que abstrae atributos como `color` y `velocidad`, y métodos como `acelerar()` o `frenar()`.
[👉 Ejecutar en Binder](https://mybinder.org/v2/gh/Mltechdrawer/TP-Java-Examples/main?urlpath=%2Fdoc%2Ftree%2FEjemploAbstraccion.ipynb)


### Encapsulación
La encapsulación protege el acceso directo a los datos internos de un objeto, controlándolo mediante métodos definidos. Esto mejora la seguridad y reduce la dependencia entre módulos.  
Ejemplo: atributos privados con métodos *getters* y *setters*.

### Herencia
La herencia permite que una clase (subclase) herede atributos y métodos de otra (superclase). Facilita la reutilización de código y la creación de jerarquías lógicas.  
Ejemplo: `Vehiculo` como superclase, y `Coche` y `Moto` como subclases.

### Polimorfismo
El polimorfismo permite que un mismo método tenga comportamientos distintos según el contexto o la clase que lo implemente.  
Ejemplo: el método `mover()` puede estar implementado de forma distinta en `Coche`, `Avion` o `Barco`.

---

## 2. Objetos y clases

- **Clase**: Es la plantilla que define las propiedades (atributos) y comportamientos (métodos).  
- **Objeto**: Es una instancia concreta de una clase, que posee valores específicos para sus atributos.  

Ejemplo en pseudocódigo:

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

## 3. Ventajas de la POO

- **Modularidad**: el código se organiza en componentes independientes.  
- **Reutilización**: se puede extender y adaptar código existente sin reescribirlo.  
- **Mantenibilidad**: facilita la lectura, depuración y evolución del software.  
- **Escalabilidad**: permite modelar sistemas complejos con jerarquías de clases y objetos.

---

## 4. POO en la práctica

En la actualidad, la POO se integra con otros paradigmas. Lenguajes como **Java** siguen una orientación a objetos estricta, mientras que **Python** o **C#** permiten combinarla con enfoques funcionales y procedimentales.  
El repaso de estos conceptos es crucial para afrontar los siguientes temas del bloque, donde se profundizará en aspectos avanzados como modularidad, herencia compleja, genericidad y el uso de contenedores.

---

## 5. Conclusión

La Programación Orientada a Objetos constituye una base sólida para el desarrollo de software moderno. Sus principios permiten construir sistemas más claros, mantenibles y robustos, y son fundamentales para abordar los contenidos más avanzados de la asignatura.
