# Colecciones ejemplos rápidos

## List

### Permite elementos duplicados y mantiene el orden de inserción

```java

List<String> nombres = new ArrayList<>();
nombres.add("María");
nombres.add("Juan");
nombres.add("María"); // permitido

System.out.println(nombres); // [María, Juan, María]

```
---
## Set

### No permite duplicados

```java

Set<String> dniSet = new HashSet<>();
dniSet.add("123A");
dniSet.add("123A");
dniSet.add("456B");

System.out.println(dniSet); // [123A, 456B]

```
---

## SortedSet

```java

import java.util.*;

SortedSet<Integer> numeros = new TreeSet<>();
numeros.add(5);
numeros.add(1);
numeros.add(3);

System.out.println(numeros); // [1, 3, 5]

```
---

## Queue

### Representa una cola (FIFO): el primero en entrar es el primero en salir.

```java

import java.util.*;

Queue<String> cola = new LinkedList<>();
cola.add("Ana");
cola.add("Luis");
cola.add("Marta");

System.out.println(cola.poll()); // Ana
System.out.println(cola.peek()); // Luis

```
---

## Deque

### No permite duplicados

```java

import java.util.*;

Deque<String> deque = new ArrayDeque<>();
deque.addFirst("inicio");
deque.addLast("fin");

System.out.println(deque.removeLast());  // fin
System.out.println(deque.removeFirst()); // inicio

```
---
## Map

### Asocia: clave → valor

```java

Map<String, Integer> edades = new HashMap<>();
edades.put("Ana", 25);
edades.put("Luis", 30);
edades.put("Ana", 27); // sobrescribe el valor anterior

System.out.println(edades); // {Luis=30, Ana=27}

```
---
## SortedMap

### Asocia clave → valor, pero ordenado por clave

```java

import java.util.*;

SortedMap<String, Integer> edades = new TreeMap<>();
edades.put("Luis", 30);
edades.put("Ana", 27);
edades.put("Carlos", 25);

System.out.println(edades); // {Ana=27, Carlos=25, Luis=30}

```