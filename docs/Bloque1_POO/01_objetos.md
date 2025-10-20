# Tipos de objetos en Java

En Java, **los objetos no tienen “tipos propios”**, sino que **heredan su tipo de la clase, interfaz o enum que los define**.  
Lo que sí podemos clasificar son los **objetos según su origen, comportamiento o cómo se instancian**.

---

## 1. Objetos según el tipo de clase que los crea

| Tipo de clase               | Tipo de objeto resultante |
|----------------------------|----------------------------|
| **Clase concreta**         | Objeto instanciable normal. |
| **Clase abstracta**        | No se pueden crear objetos directamente. Solo objetos de subclases concretas. |
| **Clase final**            | Objeto cuya clase no puede extenderse. |
| **Clase anónima**          | Objeto de una clase sin nombre, declarada en línea. |
| **Clase interna (inner)**  | Objeto ligado a una instancia de la clase externa. |
| **Clase estática anidada** | Objeto independiente de la instancia externa. |
| **Clase local**            | Objeto creado dentro de un método. |
| **Clase sellada (sealed)** | Objeto cuya jerarquía de herencia está limitada. |
| **Enum**                   | Objeto constante, predefinido y único. |

---

## 2. Objetos según comportamiento en memoria

| Tipo de objeto            | Descripción |
|---------------------------|-------------|
| **Mutable**               | Su estado puede cambiar tras crearse. Ejemplo: `ArrayList`, `StringBuilder`. |
| **Inmutable**             | No cambia una vez creado. Ejemplo: `String`, `LocalDate`. |
| **Singleton / estático** | Solo existe una instancia en toda la aplicación. Ejemplo: `Runtime.getRuntime()`. |
| **Objeto anónimo**        | Se instancia sin nombre de clase explícita. |
| **Objeto con estado compartido (static)** | Pertenece a la clase y no a una instancia. |

---

## 3. Ejemplo de algunos tipos

### Objeto de clase concreta
```java
Coche c = new Coche();
```

### Objeto de clase anónima
```java
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hola desde clase anónima");
    }
};
```

### Objeto inmutable
```java
String nombre = "Marilola"; // no se puede modificar
```

### Singleton
```java
Runtime r = Runtime.getRuntime();
```

---

## Tabla comparativa

| Tipo de objeto             | ¿Cómo se obtiene?                                | Característica clave |
|----------------------------|--------------------------------------------------|------------------------|
| **Normal**                 | A partir de una clase concreta (`new Clase()`)   | Instanciable. |
| **De clase abstracta**     | Desde subclases concretas                        | La clase base no se instancia. |
| **Anónimo**                | Con `new Interfaz() {…}` o `new Clase() {…}`     | Sin nombre de clase. |
| **Interno / inner**        | A partir de una clase dentro de otra             | Depende de instancia externa. |
| **Enum**                   | Predefinido, instanciado automáticamente          | Constantes únicas. |
| **Inmutable**              | Clase diseñada para no modificarse               | Seguro, sin efectos laterales. |
| **Singleton**              | Patrón que permite una sola instancia            | Control global. |

---

## Conclusión

- Los **objetos no se clasifican como las clases**, sino que dependen del tipo de clase del que provienen.
- Lo que cambia es **cómo se crean, cómo viven en memoria o si pueden modificarse**.
- Por eso, tiene sentido hablar de **tipos de clases**, y **formas o categorías de objetos**.

---
