# Genericidad y Contenedores

## Introducción a los contenedores

Los **contenedores** o colecciones son objetos que almacenan otros objetos.  
Se utilizan para:  

- Almacenar, recuperar y manipular datos.  
- Transmitir datos entre métodos.  
- Representar grupos naturales de elementos (ejemplo: lista de contactos, conjunto de objetos gráficos, carpeta de correos).  

Ejemplo clásico: los **vectores**.  
A partir de **Java 2**, la biblioteca `java.util` proporciona un marco unificado para manejar colecciones.  

---

## Genericidad en Java

Desde la versión **Java 5**, las clases e interfaces de contenedores son **genéricas**.  
Esto implica que al definir un contenedor se especifica qué tipo de dato almacenará.

Formato:  
```
NombreClase<T>
```
donde `T` representa el tipo de dato a almacenar.

Características: 

- Solo admite **clases** (no tipos primitivos).    
- Evita conversiones innecesarias con `Object`.    
- Aporta seguridad de tipos en tiempo de compilación.  

---

**[Colecciones](03_colecciones_genericidad.md)**

**[Ejemplos rápidos](03_colecciones_ejemplosrapidos.md)**

---

## Tipos de contenedores

### List
Una **List** es una colección ordenada que permite elementos duplicados y acceso posicional mediante índices.  
Implementaciones comunes: **ArrayList** (rápido acceso por índice, coste alto en inserciones intermedias) y **LinkedList** (eficiente en inserciones/borrados, acceso más lento por índice).

<details>
<summary> List </summary>
<p><strong>Registro de asistencia en clase</strong> → los alumnos se almacenan en el orden en que se pasan lista, y puede haber nombres repetidos.</p>
<p><strong>Historial de navegación en un navegador</strong> → se guardan URLs en orden de visita, pudiendo repetirlas.</p>
<p><strong>Lista de tareas pendientes (To-Do)</strong> → se añaden nuevas tareas y se accede rápido por posición (ej: “la tercera tarea”).</p>
</details>
---

[List](03_codigos1.md#list)

[Operaciones List](03_operaciones.md#list-listas)

---

### Set
Un **Set** es una colección que no permite elementos duplicados y no mantiene orden posicional.  
Implementaciones comunes: **HashSet** (sin orden, alto rendimiento), **LinkedHashSet** (mantiene orden de inserción) y **TreeSet** (mantiene los elementos ordenados).

<details>
<summary> Set </summary>
<p><strong>Conjunto de emails registrados en un sistema</strong> → no deben existir duplicados, el orden no importa.</p>
<p><strong>Colección de cartas en un juego</strong> → una carta no puede estar dos veces en la mano del jugador.</p>
<p><strong>Lista de alumnos que han entregado un trabajo</strong> → se garantiza unicidad, sin importar el orden.</p>
</details>
---

[Set](03_codigos1.md#set)

[Operaciones Set](03_operaciones.md#set-conjuntos)

---
### Map
Un **Map** asocia claves únicas con valores, sin admitir claves duplicadas.  
Permite obtener vistas de claves, valores y pares clave–valor.  
Implementaciones comunes: **HashMap** (rápido, sin orden), **LinkedHashMap** (orden de inserción) y **TreeMap** (ordenado por claves).

<details>
<summary> Map </summary>
<p><strong>Diccionario español–inglés</strong> → cada palabra (clave) se asocia a una traducción (valor).</p>
<p><strong>Agenda telefónica</strong> → cada persona (clave) tiene un número de teléfono (valor).</p>
<p><strong>Notas de los alumnos en una asignatura</strong> → scada matrícula (clave) corresponde a una calificación (valor).</p>
</details>
---

[Map](03_codigos1.md#map)

[Operaciones Map](03_operaciones.md#map-mapas)

---
### Queue
Una **Queue** es una colección que sigue la semántica FIFO (primero en entrar, primero en salir).  
Se usa para gestionar elementos en orden de llegada.  
Se implementa habitualmente con **LinkedList** o con clases específicas como **PriorityQueue**.

<details>
<summary> Queue </summary>
<p><strong>Cola de impresión en una oficina</strong> → el primer documento enviado es el primero en imprimirse.</p>
<p><strong>Atención al cliente en un banco</strong> → los clientes son atendidos en el orden de llegada.</p>
<p><strong>Procesamiento de tareas en un sistema operativo</strong> → las tareas se ejecutan siguiendo la política FIFO.</p>
</details>

---

[Queue](03_codigos1.md#queue)

[Operaciones Queue](03_operaciones.md#queue-colas)

---

### Deque
Un **Deque** (Double Ended Queue) permite insertar y eliminar elementos por ambos extremos.  
Puede funcionar como **cola** (FIFO) o como **pila** (LIFO).  
Implementaciones comunes: **ArrayDeque** y **LinkedList**.

<details>
<summary> Deque </summary>
<p><strong>Navegador web con botones <i>Atrás</i> y <i>Adelante</i></strong> → permite acceder tanto al historial previo como al siguiente.</p>
<p><strong>Gestión de un buffer de mensajes</strong> → se insertan por un extremo y se eliminan por ambos, según la necesidad.</p>
<p><strong>Implementación de un algoritmo de backtracking (ej. resolver un laberinto)</strong> → puede comportarse como pila (LIFO) o como cola (FIFO).</p>
</details>

---

[Deque](03_codigos1.md#deque)

[Operaciones Deque](03_operaciones.md#deque-deques)

---


[Comparativa de colecciones en Java](#comparativa-de-colecciones-en-java)

---
## Jerarquía de Interfaces de Colecciones

### `Collection<T>`
Interfaz base para la mayoría de contenedores.   

Operaciones principales:  

- **add**, **addAll** → añadir elementos.    
- **remove**, **removeAll**, **clear** → eliminar elementos.    
- **size**, **contains**, **containsAll** → consultas de estado.    
- **iterator()** → obtener un iterador para recorrer la colección.  

### Iteradores
Los **iteradores** son objetos que permiten recorrer un contenedor.  
- Pueden acceder, eliminar o añadir elementos.    
- No se permiten modificaciones externas mientras un iterador recorre la colección.    

Métodos básicos de `Iterator<T>`:  

- `hasNext()`    
- `next()`    
- `remove()`   

---

## Interfaces derivadas de Collection

### `Set<T>` y `SortedSet<T>`

- `Set`: no admite elementos repetidos.    
- `SortedSet`: además mantiene los elementos **ordenados**.  

  - Los objetos deben implementar `Comparable<T>` o suministrar un `Comparator<T>`.    
  - Orden natural: `compareTo`.    
  - Orden alternativo: `Comparator<T>` mediante `compare(a,b)`.  

### `List<T>`
- Añade **propiedad posicional** a los elementos.    
- Operaciones típicas: `add(i,e)`, `remove(i)`, `get(i)`, `set(i,e)`.    
- Puede obtener un **ListIterator** que amplía las funcionalidades de `Iterator`.    

### `Map<K,V>` y `SortedMap<K,V>`
- Colección de pares clave-valor.    
- No admite claves repetidas.    
- Permite obtener:  
  - Conjunto de claves (`keySet()`).    
  - Colección de valores (`values()`).    
  - Conjunto de pares (`entrySet()`).    

`SortedMap<K,V>`: garantiza que las claves están ordenadas.  

---

## Implementaciones de Contenedores en Java

- **List**  
  - `LinkedList<T>` → lista doblemente enlazada.    
  - `ArrayList<T>` → vector dinámico con acceso rápido por posición.    

- **Set / SortedSet**  
  - `HashSet<T>` → basado en tabla hash (alto rendimiento).    
  - `LinkedHashSet<T>` → mantiene el orden de inserción.    
  - `TreeSet<T>` → mantiene orden natural o definido por comparador.    

- **Map / SortedMap**  
  - `HashMap<K,V>` → tabla hash.    
  - `LinkedHashMap<K,V>` → mantiene orden de inserción.    
  - `TreeMap<K,V>` → mantiene las claves ordenadas.    

---

## Requisitos de Implementación

- `equals()` debe estar correctamente redefinido para el buen funcionamiento de `contains` y `remove`.    
- `hashCode()` debe ser consistente con `equals()`.    
- `Comparable<T>` o `Comparator<T>` se requieren para contenedores ordenados (`TreeSet`, `TreeMap`).    

Reglas:  
- Si dos objetos son iguales según `equals()`, deben devolver el mismo `hashCode()`.  
- `hashCode()` se puede implementar sumando los `hashCode()` de los atributos usados en `equals()`.    

---


**[Iteradores](03_iteradores.md)**

**[Comparadores](03_comparadores.md)**

---
## Comparativa de colecciones en java
| Colección | Permite duplicados | Orden | Clave-Valor | Acceso típico | Implementaciones comunes |
|-----------|--------------------|-------|-------------|---------------|---------------------------|
| **List**  | Sí                 | Mantiene orden de inserción, acceso posicional por índice | No | Acceso rápido por índice en `ArrayList`; eficiente en inserciones/borrados con `LinkedList` | ArrayList, LinkedList |
| **Set**   | No                 | No garantiza orden (`HashSet`), orden de inserción (`LinkedHashSet`), orden natural o por comparador (`TreeSet`) | No | Búsqueda de pertenencia (`contains`) | HashSet, LinkedHashSet, TreeSet |
| **Map**   | Claves: No<br>Valores: Sí | No garantiza orden (`HashMap`), orden de inserción (`LinkedHashMap`), orden natural de claves (`TreeMap`) | Sí | Acceso rápido por clave | HashMap, LinkedHashMap, TreeMap |
| **Queue** | Sí                 | FIFO (primero en entrar, primero en salir) | No | Inserción y extracción en un extremo | LinkedList, PriorityQueue |
| **Deque** | Sí                 | FIFO o LIFO (ambos extremos) | No | Inserción y extracción en ambos extremos | ArrayDeque, LinkedList |

