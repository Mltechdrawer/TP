# Tipos de interfaces

## Interfaz “normal” (o estándar)

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

## Interfaz funcional

- Es una interfaz que tiene un único método abstracto (aunque puede tener múltiples métodos `default` o `static`).
- Este tipo de interfaz es la base para utilizar expresiones lambda en Java.
- Debe o puede llevar la anotación `@FunctionalInterface` para asegurar que cumple la regla de un solo método abstracto.
- Ejemplos en la biblioteca de Java:  
  - `Runnable` (método `run()`),  
  - `Comparator<T>`,  
  - `Function<T,R>`,  
  - `Consumer<T>`.

---

## Interfaz marcador (Marker Interface)

- Es una interfaz que no declara métodos ni constantes (o lo hace muy poco), y sirve principalmente para etiquetar o marcar que una clase tiene una determinada propiedad o comportamiento.
- Ejemplos: `Serializable`, `Cloneable`.
- Su uso es para que el sistema (o frameworks) verifiquen si un objeto implementa esa interfaz y actúen de forma distinta.

---

## Subinterfaces / Interfaces anidadas

- Una interfaz puede extender otras interfaces (múltiples).
- También es posible declarar interfaces dentro de otras clases o interfaces (interfaces anidadas o interfaces miembro).
- Esto permite organizar más finamente los contratos, agrupar funcionalidades, o especializar comportamientos.

---

| Tipo de interfaz       | Características principales                                                | Cuándo usarlo                         |
|------------------------|---------------------------------------------------------------------------|----------------------------------------|
| **Interfaz normal**    | Tiene uno o más métodos abstractos. Puede incluir métodos `default`, `static` (desde Java 8) y `private` (desde Java 9). | Cuando varias clases deben cumplir un conjunto de métodos comunes. |
| **Interfaz funcional** | Solo tiene **un método abstracto**. Puede tener métodos `default` o `static`. Se puede usar con lambdas. | Para usar expresiones lambda o referencias a métodos. |
| **Interfaz marcador**  | No declara métodos (o muy pocos). Solo sirve para **marcar o etiquetar** una clase. | Cuando necesitas indicar una propiedad especial (ej. serializable, clonable). |
| **Subinterfaz / Anidada** | Una interfaz que **extiende** otra(s), o que está declarada dentro de una clase o interfaz. | Para especializar contratos o agrupar interfaces relacionadas. |
