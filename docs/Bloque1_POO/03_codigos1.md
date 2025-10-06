# Genericidad y contenedores

## Definiciones y ejemplos ilustrativos

### Colecciones

```java
import java.util.*;  // Importamos las colecciones y las interfaces necesarias

public class EjemploColecciones {
    public static void main(String[] args) {
        // ------------------ Uso de la Interfaz Set y SortedSet ------------------
        
        // Set no permite elementos duplicados
        Set<String> conjuntoNombres = new HashSet<>();
        conjuntoNombres.add("María");
        conjuntoNombres.add("Juan");
        conjuntoNombres.add("Ana");
        conjuntoNombres.add("Pedro");

        System.out.println("Conjunto de nombres (Set): " + conjuntoNombres);

        // SortedSet mantiene los elementos ordenados
        SortedSet<String> conjuntoOrdenado = new TreeSet<>(conjuntoNombres);
        System.out.println("Conjunto ordenado (SortedSet): " + conjuntoOrdenado);

        // ------------------ Uso de la Interfaz Iterator ------------------

        // Iterador para recorrer el conjunto de nombres
        Iterator<String> iterador = conjuntoNombres.iterator();
        System.out.println("Recorriendo el conjunto con Iterator:");
        while (iterador.hasNext()) {
            String nombre = iterador.next();
            System.out.println(nombre);
        }

        // ------------------ Uso de la Interfaz Comparator ------------------

        // Comparator para ordenar alfabéticamente de forma inversa
        Comparator<String> comparadorInverso = new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o2.compareTo(o1);  // Orden inverso
            }
        };

        // Aplicamos el comparador inverso al SortedSet
        SortedSet<String> conjuntoOrdenadoInverso = new TreeSet<>(comparadorInverso);
        conjuntoOrdenadoInverso.addAll(conjuntoNombres);
        System.out.println("Conjunto ordenado inversamente (SortedSet con Comparator): " + conjuntoOrdenadoInverso);

        // ------------------ Uso de la Interfaz List y ListIterator ------------------

        // Lista de números (permite duplicados y tiene un orden específico)
        List<Integer> listaNumeros = new ArrayList<>();
        listaNumeros.add(10);
        listaNumeros.add(20);
        listaNumeros.add(30);
        listaNumeros.add(40);

        System.out.println("Lista de números (List): " + listaNumeros);

        // Uso de ListIterator para recorrer la lista en ambas direcciones
        ListIterator<Integer> listIterator = listaNumeros.listIterator();
        System.out.println("Recorriendo la lista de números hacia adelante con ListIterator:");
        while (listIterator.hasNext()) {
            System.out.println(listIterator.next());
        }

        // Recorrido hacia atrás
        System.out.println("Recorriendo la lista de números hacia atrás con ListIterator:");
        while (listIterator.hasPrevious()) {
            System.out.println(listIterator.previous());
        }

        // ------------------ Uso de la Interfaz Map y SortedMap ------------------

        // Mapa para almacenar pares clave-valor (ID de empleado y su nombre)
        //Map<Integer, String> mapaEmpleados = new HashMap<>();
        // HashMap no garantiza orden de inserción
        Map<Integer, String> mapaEmpleados = new LinkedHashMap<>();
        // LinkedHashMap sí garantiza orden de inserción
        mapaEmpleados.put(103, "Juan");
        mapaEmpleados.put(102, "María");
        mapaEmpleados.put(101, "Pedro");

        System.out.println("Mapa de empleados (Map):");
        for (Map.Entry<Integer, String> entrada : mapaEmpleados.entrySet()) {
            System.out.println("ID: " + entrada.getKey() + ", Nombre: " + entrada.getValue());
        }

        // SortedMap para mantener las claves ordenadas
        SortedMap<Integer, String> mapaEmpleadosOrdenado = new TreeMap<>(mapaEmpleados);
        System.out.println("Mapa de empleados ordenado por clave (SortedMap):");
        for (Map.Entry<Integer, String> entrada : mapaEmpleadosOrdenado.entrySet()) {
            System.out.println("ID: " + entrada.getKey() + ", Nombre: " + entrada.getValue());
        }
    }
}
```

---

### List

```java
// Una lista es una colección ordenada que permite 
// elementos duplicados

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class EjemploLista {
    public static void main(String[] args) {
        List<String> lista = new ArrayList<>();
        Scanner sc = new Scanner(System.in);

        // Añadir elementos a la lista
        System.out.println("Introduce 3 nombres:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre " + (i + 1) + ": ");
            lista.add(sc.nextLine());
        }

        // Mostrar los elementos de la lista
        System.out.println("Los nombres introducidos son:");
        for (String nombre : lista) {
            System.out.println(nombre);
        }

        sc.close();
    }
}

```
---

### Set

```java
// Un conjunto es una colección que no permite 
// elementos duplicados

import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class EjemploConjunto {
    public static void main(String[] args) {
        Set<String> conjunto = new HashSet<>();
        Scanner sc = new Scanner(System.in);

        // Añadir elementos al conjunto
        System.out.println("Introduce 3 nombres (los duplicados se ignorarán):");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre " + (i + 1) + ": ");
            conjunto.add(sc.nextLine());
        }

        // Mostrar los elementos del conjunto
        System.out.println("Los nombres introducidos son:");
        for (String nombre : conjunto) {
            System.out.println(nombre);
        }

        sc.close();
    }
}
```

---

### Map

```java
// Un mapa es una estructura de datos que asocia 
// claves a valores

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class EjemploMapa {
    public static void main(String[] args) {
        Map<String, Integer> mapa = new HashMap<>();
        Scanner sc = new Scanner(System.in);

        // Añadir elementos al mapa
        System.out.println("Introduce 3 nombres y sus edades:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre: ");
            String nombre = sc.nextLine();
            System.out.print("Edad: ");
            int edad = sc.nextInt();
            sc.nextLine(); // Consumir el salto de línea
            mapa.put(nombre, edad);
        }

        // Mostrar los elementos del mapa
        System.out.println("Los nombres y sus edades son:");
        for (Map.Entry<String, Integer> entrada : mapa.entrySet()) {
            System.out.println(entrada.getKey() + " tiene " + entrada.getValue() + " años.");
        }

        sc.close();
    }
}

```

---

### Queue

```java
// Una cola es una estructura de datos FIFO.

import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class EjemploCola {
    public static void main(String[] args) {
        Queue<String> cola = new LinkedList<>();
        Scanner sc = new Scanner(System.in);

        // Añadir elementos a la cola
        System.out.println("Introduce 3 nombres:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre " + (i + 1) + ": ");
            cola.offer(sc.nextLine());
        }

        // Mostrar y quitar elementos de la cola
        System.out.println("Atendiendo a los nombres en la cola:");
        while (!cola.isEmpty()) {
            System.out.println("Atendiendo a: " + cola.poll());
        }

        sc.close();
    }
}

```

---

### Deque

```java
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.Scanner;

public class EjemploDeque {
    public static void main(String[] args) {
        Deque<String> deque = new ArrayDeque<>();
        Scanner sc = new Scanner(System.in);

        // Añadir elementos al principio y al final del deque
        System.out.println("Introduce 3 nombres para añadir al principio:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre " + (i + 1) + ": ");
            deque.addFirst(sc.nextLine());
        }

        System.out.println("Introduce 3 nombres para añadir al final:");
        for (int i = 0; i < 3; i++) {
            System.out.print("Nombre " + (i + 1) + ": ");
            deque.addLast(sc.nextLine());
        }

        // Mostrar y quitar elementos del deque desde ambos extremos
        System.out.println("Eliminando del principio:");
        while (!deque.isEmpty()) {
            System.out.println("Eliminado: " + deque.pollFirst());
        }

        sc.close();
    }
}
```

---

