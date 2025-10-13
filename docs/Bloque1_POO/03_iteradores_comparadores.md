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
