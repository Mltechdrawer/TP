# Operaciones sobre colecciones en Java

## List (Listas)

Una lista es una colección **ordenada** que permite **elementos duplicados** y acceso por **índice**.

**Operaciones estándar**  
- `add(E e)`: añade un elemento al final de la lista.  
- `get(int index)`: devuelve el elemento en una posición específica (por índice).  
- `set(int index, E e)`: reemplaza el elemento en la posición dada.  
- `remove(int index)`: elimina el elemento en la posición especificada.  
- `size()`: devuelve el número de elementos en la lista.  
- `isEmpty()`: verifica si la lista está vacía.  
- `contains(Object o)`: verifica si la lista contiene un elemento específico.  
- `indexOf(Object o)`: devuelve el índice de la primera aparición de un elemento (o `-1` si no se encuentra).  
- `lastIndexOf(Object o)`: devuelve el índice de la última aparición de un elemento.  
- `clear()`: elimina todos los elementos de la lista.

**Operaciones opcionales**  
- `add(int index, E e)`: inserta un elemento en una posición específica.  
- `remove(Object o)`: elimina la primera ocurrencia de un elemento si está presente.  
- `subList(int fromIndex, int toIndex)`: devuelve una vista de la lista entre dos índices.  
- `iterator()`: devuelve un iterador sobre los elementos de la lista.


## Set (Conjuntos)

Un conjunto es una colección que **no permite duplicados** y **no garantiza** el orden de los elementos.

**Operaciones estándar**  
- `add(E e)`: añade un elemento al conjunto si no está presente.  
- `contains(Object o)`: verifica si el conjunto contiene un elemento.  
- `remove(Object o)`: elimina un elemento si está presente.  
- `size()`: devuelve el número de elementos en el conjunto.  
- `isEmpty()`: verifica si el conjunto está vacío.  
- `iterator()`: devuelve un iterador sobre los elementos del conjunto.

**Operaciones opcionales**  
- `addAll(Collection<? extends E> c)`: añade todos los elementos de la colección dada al conjunto, si no están presentes.  
- `removeAll(Collection<?> c)`: elimina todos los elementos presentes en la colección dada.  
- `retainAll(Collection<?> c)`: conserva solo los elementos que están en el conjunto y en la colección dada.  
- `clear()`: elimina todos los elementos del conjunto.


## Map (Mapas)

Un mapa es una colección que **asocia claves a valores**. No permite **claves duplicadas**.

**Operaciones estándar**  
- `put(K key, V value)`: añade una asociación clave-valor al mapa.  
- `get(Object key)`: devuelve el valor asociado con la clave especificada.  
- `remove(Object key)`: elimina la asociación de la clave especificada.  
- `containsKey(Object key)`: verifica si el mapa contiene una clave especificada.  
- `containsValue(Object value)`: verifica si el mapa contiene un valor especificado.  
- `size()`: devuelve el número de asociaciones clave-valor en el mapa.  
- `isEmpty()`: verifica si el mapa está vacío.  
- `clear()`: elimina todas las asociaciones del mapa.

**Operaciones opcionales**  
- `putIfAbsent(K key, V value)`: añade la asociación si la clave no está ya presente en el mapa.  
- `putAll(Map<? extends K, ? extends V> m)`: copia todas las asociaciones del mapa especificado a este mapa.  
- `replace(K key, V value)`: reemplaza el valor asociado a la clave especificada si está presente.  
- `entrySet()`: devuelve una vista de conjunto de las asociaciones clave-valor del mapa.  
- `keySet()`: devuelve una vista de conjunto de las claves contenidas en este mapa.  
- `values()`: devuelve una colección de los valores contenidos en el mapa.


## Queue (Colas)

Una cola es una colección que opera con el principio **FIFO** (*First-In, First-Out*).

**Operaciones estándar**  
- `offer(E e)`: inserta un elemento en la cola; devuelve `false` si no puede ser insertado.  
- `poll()`: devuelve y elimina el primer elemento de la cola. Devuelve `null` si está vacía.  
- `peek()`: devuelve pero no elimina el primer elemento de la cola. Devuelve `null` si está vacía.  
- `isEmpty()`: verifica si la cola está vacía.  
- `size()`: devuelve el número de elementos en la cola.

**Operaciones opcionales**  
- `add(E e)`: añade un elemento a la cola. Lanza una excepción si no puede ser añadido.  
- `remove()`: devuelve y elimina el primer elemento. Lanza una excepción si la cola está vacía.  
- `element()`: devuelve pero no elimina el primer elemento. Lanza una excepción si la cola está vacía.


## Deque (Deques)

Un *deque* (*Double Ended Queue*) es una cola que permite añadir y eliminar elementos desde **ambos extremos**.

**Operaciones estándar**  
- `addFirst(E e)`: inserta un elemento al inicio del deque.  
- `addLast(E e)`: inserta un elemento al final del deque.  
- `removeFirst()`: elimina y devuelve el primer elemento del deque.  
- `removeLast()`: elimina y devuelve el último elemento del deque.  
- `getFirst()`: devuelve pero no elimina el primer elemento. Lanza excepción si está vacío.  
- `getLast()`: devuelve pero no elimina el último elemento. Lanza excepción si está vacío.

**Operaciones opcionales**  
- `offerFirst(E e)`: intenta añadir un elemento al principio sin lanzar excepciones.  
- `offerLast(E e)`: intenta añadir un elemento al final sin lanzar excepciones.  
- `pollFirst()`: devuelve y elimina el primer elemento, o `null` si el deque está vacío.  
- `pollLast()`: devuelve y elimina el último elemento, o `null` si el deque está vacío.  
- `peekFirst()`: devuelve pero no elimina el primer elemento, o `null` si el deque está vacío.  
- `peekLast()`: devuelve pero no elimina el último elemento, o `null` si el deque está vacío.  
- `push(E e)`: inserta un elemento al frente (equivalente a `addFirst()`).  
- `pop()`: elimina y devuelve el primer elemento (equivalente a `removeFirst()`).

