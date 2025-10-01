# Modularidad, Herencia y Reusabilidad

## Definiciones y ejemplos ilustrativos

### Conceptos fundamentales de la programación orientada a objetos

### Atributos y métodos de clase.

En Java, los **atributos y métodos de clase** son aquellos declarados con la palabra clave **static**.  
Los atributos de clase representan valores compartidos por todas las instancias de la clase (por ejemplo, un contador de objetos creados), mientras que los métodos de clase son funciones que se pueden invocar sin necesidad de crear un objeto (por ejemplo, Math.sqrt()).  
Se deben usar cuando la información o el comportamiento no dependen de un objeto concreto, sino de la clase en general, facilitando así recursos comunes, utilidades o constantes accesibles globalmente.

<details>
<summary>💡 Atributos de clase </summary>
<p> Se usan atributos de clase (static) cuando la información debe ser compartida entre todas las instancias o cuando el dato no pertenece a una instancia específica.</p>
</details>

 **[Atributos de clase](02_codigos4.4.md#atributos-de-clase)**

<details>
<summary>💡 Métodos de clase </summary>
<p> Se usan métodos de clase (static) cuando la funcionalidad no depende del estado de una instancia y puede ejecutarse sin necesidad de crear un objeto.</p>
</details>

 **[Atributos de clase](02_codigos4.4.md#metodos-de-clase)**


### Constantes

En Java, las **constantes** son variables cuyo valor no puede modificarse una vez asignado. Se definen con los modificadores static final, lo que significa que pertenecen a la clase (y no a instancias específicas) y que su valor es inmutable.  

<details>
<summary>💡 Constantes </summary>
<p> Por convención, los nombres de las constantes se escriben en mayúsculas y con guiones bajos para separar palabras, como PI, MAX_VALUE o DEFAULT_TIMEOUT.</p>
<p> Se utilizan para representar valores fijos y universales en el programa, mejorando la legibilidad y evitando errores asociados a la duplicación de <i>números mágicos</i> o cadenas repetidas en el código.</p>
</details>

 **[Atributos de clase](02_codigos4.4.md#constantes)**

### Patrón Singleton

El patrón **Singleton** es un **patrón de diseño creacional** que garantiza que solo exista una única instancia de una clase en todo el sistema y que, además, sea fácilmente accesible desde cualquier parte del programa.  
En Java, se implementa declarando el constructor como privado (para evitar que se creen instancias desde fuera) y proporcionando un método público y estático que devuelve siempre la misma instancia (por ejemplo, getInstance()).  
Se suele usar cuando es necesario un único punto de acceso a un recurso compartido, como un gestor de configuración, un logger, una conexión a base de datos o un manejador de hilos.

