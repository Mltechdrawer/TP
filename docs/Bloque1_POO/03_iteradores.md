# Iteradores

## Motivación y objetivo

Los iteradores permiten recorrer los elementos de una colección de manera uniforme y segura, sin necesidad de conocer los detalles de su estructura interna. Constituyen una abstracción que separa la lógica de acceso de la implementación del contenedor.

Frente al uso de bucles indexados, los iteradores reducen errores, simplifican el código y permiten recorrer cualquier colección de forma homogénea.

## Conceptos básicos: Iterable e Iterator

En Java, la interfaz `Iterable<T>` define el contrato que permite recorrer los elementos de una colección. Contiene un único método:

```java
Iterator<T> iterator();
```

El objeto que devuelve este método es una instancia de una clase que implementa la interfaz `Iterator<E>`, que define los métodos necesarios para recorrer una colección:

```java
boolean hasNext();
E next();
void remove();
```

- **Iterable** representa algo que se puede recorrer.  
- **Iterator** representa el mecanismo que permite recorrerlo.

La colección implementa `Iterable`, y a través de su método `iterator()` produce un `Iterator` que gestiona la secuencia de acceso a los elementos.

## Formas de iterar colecciones

En Java existen distintas formas de iterar una colección:

### Usando Iterator

Es la forma más explícita de recorrer una colección. Se obtiene un objeto `Iterator` y se usan sus métodos `hasNext()` y `next()`:

```java
Iterator<String> it = lista.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

### Usando bucle for tradicional

Se puede usar el `Iterator` dentro de un bucle for clásico, inicializando, comprobando la condición y avanzando manualmente.

### Usando for-each (enhanced for)

El bucle `for-each` permite recorrer cualquier objeto que implemente `Iterable` de forma más legible:

```java
for (String elemento : lista) {
    System.out.println(elemento);
}
```

Es la forma más común y legible de iterar cuando no se necesita eliminar o modificar elementos durante la iteración.

### Cuándo usar cada forma

- **for-each:** preferible por claridad cuando no se requiere eliminar elementos.  
- **Iterator:** cuando se va a eliminar o modificar elementos de la colección durante el recorrido.  
- **for tradicional:** útil en casos concretos donde se necesita un control más detallado.

## Casos particulares de colecciones

### List y Set

Las listas (`List`) mantienen el orden de inserción y permiten elementos duplicados. Su iteración respeta ese orden.  
Los conjuntos (`Set`) no garantizan un orden determinado (salvo en implementaciones específicas como `LinkedHashSet` o `TreeSet`).

### Map

Los mapas no implementan `Iterable` directamente, pero ofrecen vistas iterables a través de sus métodos:

- `keySet()` — devuelve un conjunto con las claves.  
- `values()` — devuelve una colección con los valores.  
- `entrySet()` — devuelve un conjunto de pares clave-valor (`Map.Entry<K,V>`).

Estas vistas permiten recorrer las entradas del mapa usando `for-each` o `Iterator`.

### ListIterator

Para listas, Java ofrece una interfaz más avanzada: `ListIterator<E>`.  
Permite recorrer en ambos sentidos, insertar o eliminar elementos y conocer la posición actual en la lista.

## Eliminación segura durante la iteración

Modificar una colección mientras se recorre con un `Iterator` requiere cuidado. Si se usa directamente un método del contenedor (por ejemplo, `list.remove()`), puede producirse una excepción `ConcurrentModificationException`.

Para eliminar elementos de forma segura, se debe usar el método `remove()` del propio iterador, que elimina el último elemento devuelto por `next()`:

```java
Iterator<String> it = lista.iterator();
while (it.hasNext()) {
    String elemento = it.next();
    if (elemento.isEmpty()) {
        it.remove();
    }
}
```

## Buenas prácticas y recomendaciones

- Usar **for-each** cuando solo se necesita leer los elementos.  
- Usar **Iterator** si se van a eliminar elementos durante el recorrido.  
- Evitar modificar la colección directamente mientras se itera sobre ella.  
- Mantener los bucles cortos y claros.  
- Elegir la forma de iteración más adecuada según el tipo de colección y la operación deseada.

## Iterables personalizados

Cualquier clase puede implementar la interfaz `Iterable<T>` para permitir que sus instancias sean recorridas mediante un `for-each`.

Esto resulta útil cuando se desea que los usuarios de una clase puedan iterar sobre sus elementos internos de forma natural.

```java
class Contenedor implements Iterable<Elemento> {
    private List<Elemento> elementos;

    public Iterator<Elemento> iterator() {
        return elementos.iterator();
    }
}
```

Un `Iterable` debe proporcionar iteradores independientes (cada llamada a `iterator()` debería devolver un nuevo objeto) y, si es posible, definir un orden de recorrido coherente.

---

# Resumen conceptual: Iterable, Iterator, Comparable y Comparator

| Elemento | Tipo de interfaz | Qué representa | Dónde se implementa | Método(s) principal(es) | Propósito | Ejemplo de uso |
|-----------|------------------|----------------|----------------------|--------------------------|------------|----------------|
| **`Iterable<T>`** | De capacidad / cualidad | La colección **puede ser recorrida** | En las clases de colección (`List`, `Set`, `Queue`, etc.) | `iterator()` | Producir un iterador que recorra sus elementos | `lista.iterator()` devuelve un `Iterator` |
| **`Iterator<E>`** | De comportamiento funcional | El objeto **que realiza el recorrido** sobre los elementos | En clases internas de las colecciones | `hasNext()`, `next()`, `remove()` | Recorrer una colección elemento a elemento | `it.hasNext()` / `it.next()` |
| **`Comparable<T>`** | De comportamiento funcional | El objeto **sabe compararse consigo mismo** | En la propia clase del objeto | `compareTo(T o)` | Definir el **orden natural** de los objetos | `Collections.sort(lista)` usa `compareTo()` |
| **`Comparator<T>`** | De comportamiento funcional externo | Un objeto **que compara dos instancias** | Fuera de la clase (otra clase o expresión lambda) | `compare(T o1, T o2)` | Definir **órdenes alternativos** sin modificar la clase | `Collections.sort(lista, comparador)` |

## En resumen conceptual

- **`Iterable`** define una **capacidad**: la de poder ser recorrido.  
- **`Iterator`** define un **comportamiento**: cómo se realiza ese recorrido.  
- **`Comparable`** define un **comportamiento interno**: cómo un objeto se compara consigo mismo.  
- **`Comparator`** define un **comportamiento externo**: cómo comparar objetos según un criterio distinto.

---