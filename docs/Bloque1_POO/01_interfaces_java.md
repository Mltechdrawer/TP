# Tipos de interfaces

## 1. Interfaz “normal” (o estándar)

- Una interfaz que declara uno o más métodos abstractos que deben implementarse en clases que la implementan.
- Por ejemplo:

```java
interface Vehiculo {
    void arrancar();
    void parar();
}
```

- Permite definir un contrato amplio para que distintas clases sigan.
- Desde Java 8 puede incluir también métodos `default`, `static`, y desde Java 9 métodos `private`.

---

## 2. Interfaz funcional

- Es una interfaz que tiene un único método abstracto (aunque puede tener múltiples métodos `default` o `static`).
- Este tipo de interfaz es la base para utilizar expresiones lambda en Java.
- Debe o puede llevar la anotación `@FunctionalInterface` para asegurar que cumple la regla de un solo método abstracto.
- Ejemplos en la biblioteca de Java:  
  - `Runnable` (método `run()`),  
  - `Comparator<T>`,  
  - `Function<T,R>`,  
  - `Consumer<T>`.

---

## 3. Interfaz marcador (Marker Interface)

- Es una interfaz que no declara métodos ni constantes (o lo hace muy poco), y sirve principalmente para etiquetar o marcar que una clase tiene una determinada propiedad o comportamiento.
- Ejemplos: `Serializable`, `Cloneable`.
- Su uso es para que el sistema (o frameworks) verifiquen si un objeto implementa esa interfaz y actúen de forma distinta.

---

## 4. Subinterfaces / Interfaces anidadas

- Una interfaz puede extender otras interfaces (múltiples).
- También es posible declarar interfaces dentro de otras clases o interfaces (interfaces anidadas o interfaces miembro).
- Esto permite organizar más finamente los contratos, agrupar funcionalidades, o especializar comportamientos.

---

