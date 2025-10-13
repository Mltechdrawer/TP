# Comparadores

## Motivación y objetivo

En muchos casos es necesario ordenar colecciones de objetos. Java proporciona mecanismos para establecer criterios de comparación entre elementos, permitiendo definir un **orden natural** o varios **órdenes personalizados** según las necesidades del programa.

Estos mecanismos se basan en dos interfaces del paquete `java.lang` y `java.util`: `Comparable` y `Comparator`.

## Conceptos básicos: Comparable y Comparator

Java ofrece dos formas principales de comparar objetos:

- **Comparable:** el propio objeto sabe cómo compararse con otros del mismo tipo. Define su **orden natural**.
- **Comparator:** un objeto externo define el criterio de comparación. Permite definir **órdenes alternativos** sin modificar la clase original.

Ambas interfaces se utilizan en colecciones ordenadas y en algoritmos de ordenación. Su uso correcto garantiza resultados coherentes y predecibles al ordenar objetos.

## Comparable

La interfaz `Comparable<T>` pertenece al paquete `java.lang` y define un único método:

```java
int compareTo(T o);
```

Este método devuelve:

- Un valor **negativo** si el objeto actual es menor que el argumento.
- **Cero** si ambos son iguales.
- Un valor **positivo** si el objeto actual es mayor.

Esta interfaz se usa cuando la propia clase define su orden natural, como ocurre en tipos integrados (`String`, `Integer`, `LocalDate`, etc.).

Al implementar `Comparable`, se debe garantizar que la relación de orden sea **total y consistente** con `equals()`. Es decir:

- Si `a.compareTo(b) == 0`, entonces `a.equals(b)` debería devolver `true`.
- La comparación debe ser **transitiva** y **simétrica**.
- No debe devolver valores arbitrarios ni basarse en restas de enteros para evitar desbordamientos.

El orden natural suele representar el sentido lógico de la entidad (por ejemplo, orden alfabético para cadenas o cronológico para fechas).

## Comparator

La interfaz `Comparator<T>` pertenece al paquete `java.util` y se utiliza para definir criterios de comparación **externos** a las clases que se desean ordenar. Define su método principal:

```java
int compare(T o1, T o2);
```

Al igual que en `Comparable`, este método devuelve un valor negativo, cero o positivo según el orden relativo de los objetos comparados.

El uso de `Comparator` permite:

- Definir varios órdenes distintos para la misma clase.
- Ordenar objetos sin modificar su código fuente.
- Reutilizar comparadores en diferentes contextos.

Desde Java 8, `Comparator` incluye **métodos estáticos y por defecto** que facilitan su uso:

- `Comparator.comparing(...)` — crea un comparador basado en una clave.
- `thenComparing(...)` — permite combinar varios criterios.
- `reversed()` — invierte el orden del comparador.
- `naturalOrder()` y `reverseOrder()` — generan comparadores estándar.
- `nullsFirst()` y `nullsLast()` — gestionan valores `null` de forma explícita.

Estos métodos favorecen un estilo de programación más declarativo y expresivo, especialmente al usarse con expresiones lambda.

## Uso en colecciones y algoritmos de ordenación

Las colecciones ordenadas y los métodos de utilidad de la API de Java utilizan comparadores para organizar sus elementos.

### Métodos de ordenación

- `Collections.sort(List<T>)` — usa el orden natural (`Comparable`).
- `Collections.sort(List<T>, Comparator<? super T>)` — usa un comparador externo.
- `List.sort(Comparator<? super T>)` — método de instancia disponible desde Java 8.

### Colecciones ordenadas

Las estructuras de datos que mantienen un orden interno (`TreeSet`, `TreeMap`) utilizan `Comparable` o `Comparator` al crearse:

- Si no se pasa un comparador, usan el orden natural (`Comparable`).
- Si se proporciona un `Comparator`, este define el orden de los elementos.

Esto permite crear colecciones flexibles, adaptadas a diferentes criterios de ordenación.

## Buenas prácticas y recomendaciones

- Implementar **Comparable** cuando exista un **orden natural lógico** y estable para la clase.  
- Usar **Comparator** cuando se requiera un orden alternativo o específico de un contexto.  
- Mantener la **consistencia entre `compareTo()` y `equals()`**.  
- Reutilizar comparadores mediante expresiones lambda o métodos de utilidad.  
- Evitar comparar números mediante restas (`a - b`), usando en su lugar `Integer.compare(a, b)` o `Double.compare(a, b)`.  
- Gestionar correctamente los posibles valores `null` con `Comparator.nullsFirst()` o `Comparator.nullsLast()`.

## Casos especiales

### Tratamiento de valores nulos

Las colecciones de Java no permiten, por defecto, comparar elementos `null`.  
Para evitar errores, se pueden usar los métodos `nullsFirst()` o `nullsLast()` al crear el comparador.

### Ordenación compuesta

Es habitual ordenar primero por un atributo y, en caso de empate, por otro.  
`Comparator.thenComparing()` permite definir este tipo de ordenaciones de forma encadenada.

### Uso con Streams

Los flujos (`Stream`) admiten comparadores en su método `sorted()`, permitiendo ordenar colecciones de manera declarativa y flexible sin modificarlas directamente.

### Tipos primitivos y envoltorios

Las clases envoltorio (`Integer`, `Double`, `Character`, etc.) implementan `Comparable` con su orden natural, por lo que se pueden usar directamente en colecciones ordenadas.

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