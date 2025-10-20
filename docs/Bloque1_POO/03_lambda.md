# Funciones Lambda

## Introducción
Las funciones lambda fueron introducidas en Java 8 con el objetivo de simplificar el código, especialmente al trabajar con colecciones, interfaces funcionales y programación orientada a eventos.  
Una función lambda es una forma compacta de representar una implementación de una interfaz funcional (una interfaz con un único método abstracto).

**¿Qué problema resuelven?**  
Antes de Java 8, para implementar comportamientos se utilizaban clases anónimas, lo que generaba código extenso y difícil de leer. Las lambdas permiten escribir código más limpio y expresivo.

---

## Sintaxis básica
Formato general:

```java
(parámetros) -> expresión
(parámetros) -> { bloque de código }
```

Ejemplo comparativo:

**Sin lambda (clase anónima):**
```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hola mundo");
    }
};
```

**Con lambda:**
```java
Runnable r = () -> System.out.println("Hola mundo");
```
---

<details>
  <summary><strong>Runnable</strong></summary>

  <h3>Código original</h3>
  <pre><code class="language-java">
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hola mundo");
    }
};
  </code></pre>

  <h3>¿Qué es <code>Runnable</code>?</h3>
  <ul>
    <li><code>Runnable</code> <strong>no es una palabra reservada</strong> del lenguaje Java.</li>
    <li>Es una <strong>interfaz funcional</strong> que forma parte del paquete estándar <code>java.lang</code>.</li>
    <li>Una interfaz funcional es aquella que tiene <strong>un único método abstracto</strong>.</li>
    <li>En este caso, el método es:</li>
  </ul>

  <pre><code class="language-java">
void run();
  </code></pre>

  <h3>¿Qué es una interfaz funcional?</h3>
  <ul>
    <li>Es una interfaz que contiene un solo método abstracto.</li>
    <li>Puede llevar la anotación <code>@FunctionalInterface</code> (opcional, pero recomendable).</li>
    <li>Ejemplos típicos en Java: <code>Runnable</code>, <code>Comparator</code>, <code>Consumer</code>, <code>Function</code>.</li>
  </ul>

  <h3>¿Qué es una clase anónima?</h3>
  <ul>
    <li>Es una clase sin nombre que se declara e instancia en una misma expresión.</li>
    <li>En este caso, el código:</li>
  </ul>

  <pre><code class="language-java">
new Runnable() {
    public void run() {
        System.out.println("Hola mundo");
    }
}
  </code></pre>

  <p>está creando un objeto de una <strong>clase anónima</strong> que implementa la interfaz <code>Runnable</code>.</p>

  <p>Equivalente a escribir:</p>

  <pre><code class="language-java">
class MiRunnable implements Runnable {
    public void run() {
        System.out.println("Hola mundo");
    }
}

Runnable r = new MiRunnable();
  </code></pre>

  <h3>¿Quién es quién en este fragmento?</h3>
  <table>
    <tr><th>Elemento</th><th>Significado</th></tr>
    <tr><td><code>Runnable</code></td><td>Interfaz funcional de Java (no es palabra reservada).</td></tr>
    <tr><td><code>new Runnable() { ... }</code></td><td>Clase anónima que implementa esa interfaz.</td></tr>
    <tr><td><code>public void run()</code></td><td>Implementación del método abstracto de la interfaz.</td></tr>
    <tr><td><code>r</code></td><td>Variable de tipo <code>Runnable</code> que almacena el objeto creado.</td></tr>
  </table>

  <h3> ¿Por qué se puede convertir en una lambda?</h3>
  <p>Porque <code>Runnable</code> tiene un único método abstracto (<code>run()</code>), por lo que se puede expresar como una función lambda:</p>

  <pre><code class="language-java">
Runnable r = () -> System.out.println("Hola mundo");
  </code></pre>

  <p> Hace lo mismo.  
  Es más breve y legible.  
  Ideal desde Java 8.</p>

  <h3>Resumen</h3>
  <ul>
    <li><code>Runnable</code> es una interfaz funcional, no una palabra clave del lenguaje.</li>
    <li>El código original crea una <strong>clase anónima</strong> que implementa esa interfaz.</li>
    <li>Se puede simplificar usando una <strong>expresión lambda</strong>.</li>
  </ul>

</details>

---

## Interfaces funcionales
Una **interfaz funcional** es aquella que tiene **un único método abstracto**. Java incluye la anotación `@FunctionalInterface` para identificarlas.

Ejemplos comunes:
- `Runnable` → `void run()`
- `Comparator<T>` → `int compare(T a, T b)`
- `Consumer<T>` → `void accept(T t)`
- `Function<T,R>` → `R apply(T t)`

---

## Ejemplos prácticos

### a) Ordenar una lista usando `Comparator`:
```java
List<String> nombres = Arrays.asList("Ana", "Luis", "Pedro");
Collections.sort(nombres, (a, b) -> a.compareTo(b));
```

### b) Recorrer una colección con `forEach`:
```java
nombres.forEach(n -> System.out.println(n));
```

### c) Uso con contenedores y streams:
```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> pares = numeros.stream()
                             .filter(n -> n % 2 == 0)
                             .toList();
System.out.println(pares);
```

Otro ejemplo: eliminar elementos con `removeIf`:
```java
nombres.removeIf(n -> n.startsWith("P"));
```

---

## Ventajas y limitaciones

| Ventajas | Limitaciones |
|----------|--------------|
| Código más compacto y legible | Difíciles de leer si son complejas |
| Facilita la programación funcional | No reemplazan toda la POO |
| Mejora uso de colecciones y Streams | Dependen de interfaces funcionales |

---

## Resumen final
- Las lambdas son funciones anónimas introducidas en Java 8.
- Requieren interfaces funcionales para funcionar.
- Hacen el código más corto, legible y fácil de mantener.
- Son especialmente útiles en colecciones, Streams y programación funcional.
- Son clave para trabajar con contenedores modernos en Java.

