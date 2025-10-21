# Programación Orientada a Eventos y Clases Anidadas

## Introducción

La **programación orientada a eventos (POE)** es un paradigma en el que la estructura del programa y su flujo de ejecución están determinados por **eventos** que ocurren en el sistema.  
A diferencia de la programación secuencial, donde las instrucciones se ejecutan de forma lineal, en la POE el programa **reacciona** a acciones externas (como la pulsación de un botón) o internas (como la finalización de un proceso).

Los eventos pueden ser generados por: 
 
- El **usuario** (clic de ratón, pulsación de teclas, etc.).  
- El **sistema operativo** (notificaciones, interrupciones).  
- El **propio programa** (mensajes internos, señales).  

Este enfoque es muy común en aplicaciones con **interfaz gráfica de usuario (GUI)**, donde el flujo no lo controla el programador, sino las acciones del usuario.

---

## Conceptos Fundamentales de la Programación Orientada a Eventos

### Eventos y fuentes de eventos
Un **evento** es una señal que indica que algo ha ocurrido.  
Una **fuente de eventos** es el componente que genera dichos eventos (por ejemplo, un botón).

### Gestores o manejadores de eventos
Un **gestor de eventos** es el código que se ejecuta cuando se produce un evento específico.  
Estos gestores suelen recibir un parámetro con información sobre el evento, como su tipo o la fuente que lo generó.

Ejemplo conceptual:
```java
boton.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Botón pulsado.");
    }
});
```

### Registro de eventos
El lenguaje debe permitir **asociar un gestor** a una fuente de eventos concreta.    
En Java esto se hace mediante métodos como `addActionListener()`.    
Es posible asociar más de un gestor al mismo evento.  

### Flujo de ejecución en un programa orientado a eventos
El flujo general sigue esta estructura:

1. **Inicialización:** se crean los objetos y se registran los eventos.    
2. **Espera y gestión:** el programa queda en un bucle interno que espera eventos y ejecuta sus gestores.    
3. **Finalización:** un evento específico puede provocar el cierre o la terminación del programa.  

---

## Arquitectura de un Programa Orientado a Eventos

El funcionamiento típico de un programa basado en eventos se puede resumir en tres fases:

1. **Inicialización:** se registran los eventos a gestionar y los componentes que los generarán.    
2. **Bucle de espera (implícito):** el programa queda a la espera de eventos en una cola.    
3. **Procesamiento:** cuando un evento llega, se ejecuta su gestor correspondiente.    

Durante la gestión de un evento, el programa no procesa otros eventos (estos quedan **encolados**).  
Esto implica que el rendimiento puede depender de la duración del código de los gestores.

Ejemplo esquemático:
```java
while (true) {
    Evento e = colaEventos.obtenerSiguiente();
    gestor = buscarGestor(e);
    gestor.ejecutar(e);
}
```

---

## Ejemplo Práctico en Java

Veamos un ejemplo con una interfaz sencilla que reacciona al pulsar un botón.

```java
import javax.swing.*;
import java.awt.event.*;

public class EjemploEvento {
    public static void main(String[] args) {
        JFrame ventana = new JFrame("Ejemplo de Evento");
        JButton boton = new JButton("Púlsame");

        boton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                System.out.println("¡Botón pulsado!");
            }
        });

        ventana.add(boton);
        ventana.setSize(200, 100);
        ventana.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        ventana.setVisible(true);
    }
}
```

Con **clase anónima**, la asociación entre evento y gestor se define en el mismo lugar.  
A partir de Java 8, puede simplificarse con una **expresión lambda**:

```java
boton.addActionListener(e -> System.out.println("¡Botón pulsado!"));
```

---

## Clases Anidadas (Nested Classes)

### Definición y tipos
Java permite definir clases dentro de otras clases. Estas se conocen como **clases anidadas**, y existen varios tipos:

| Tipo de clase | Nivel | Modificador | Dependencia | Uso típico |
|----------------|--------|-------------|--------------|------------|
| Estática | Miembro | `static` | No depende de una instancia | Estructuras internas o utilidades |
| Interna | Miembro | Sin `static` | Depende de la clase contenedora | Manipular datos del objeto externo |
| Local | Método | Sin `static` | Sí | Clases auxiliares dentro de un método |
| Anónima | Expresión | Implícito | Sí | Implementar interfaces o manejar eventos |

### Clases anidadas estáticas
Se declaran como miembros `static` dentro de otra clase.  
Ejemplo:
```java
public class Lista {
    private static class Nodo {
        Object dato;
        Nodo siguiente;
    }
}
```

### Clases internas (no estáticas)
Cada objeto de la clase interna está asociado a un objeto de la clase externa.
```java
public class Pila {
    private class Nodo {
        Object dato;
        Nodo siguiente;
        Nodo(Object o) {
            dato = o;
            siguiente = primero;
            primero = this;
        }
    }
    private Nodo primero;
    public void añade(Object ref) { new Nodo(ref); }
}
```

### Clases locales y anónimas
Una **clase local** se define dentro de un método y solo puede usarse en su ámbito.  
Las **clases anónimas** no tienen nombre y se crean directamente en una expresión `new`, muy comunes para implementar interfaces como `ActionListener`.

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Evento manejado con clase anónima");
    }
});
```

Con **funciones lambda** (Java 8+):
```java
button.addActionListener(e -> System.out.println("Evento manejado con lambda"));
```

---

## Conclusiones

- La programación orientada a eventos permite diseñar programas **reactivos** y modulares.  
- Los **gestores de eventos** encapsulan la lógica que responde a acciones del usuario o del sistema.  
- Las **clases anidadas** mejoran el **encapsulamiento** y permiten asociar el comportamiento al contexto donde se usa.  
- Las **clases anónimas** y **lambdas** simplifican la escritura del código y son herramientas clave en el desarrollo moderno en Java.


