# Interfaz vs clase

```java
// -------------
// 1) Interfaz
// -------------
interface RecetaSalsa {
    String getNombre();
    void preparar();
}

// --------------------------------------
// 2) Clases que implementan la interfaz
// --------------------------------------
class SalsaTomate implements RecetaSalsa {
    @Override
    public String getNombre() {
        return "Salsa de Tomate";
    }

    @Override
    public void preparar() {
        System.out.println("Preparando salsa de tomate con tomates, aceite y sal.");
    }
}

class SalsaPesto implements RecetaSalsa {
    @Override
    public String getNombre() {
        return "Salsa Pesto";
    }

    @Override
    public void preparar() {
        System.out.println("Preparando salsa pesto con albahaca, piñones y parmesano.");
    }
}

// ----------------------------
// 3) Clase base con herencia
// ----------------------------
class SalsaBase {
    protected String nombre;
    protected String[] ingredientes;

    public SalsaBase(String nombre, String[] ingredientes) {
        this.nombre = nombre;
        this.ingredientes = ingredientes;
    }

    public void mostrarIngredientes() {
        System.out.print(nombre + " lleva: ");
        for (int i = 0; i < ingredientes.length; i++) {
            System.out.print(ingredientes[i]);
            if (i < ingredientes.length - 1) System.out.print(", ");
        }
        System.out.println(".");
    }
}

// -----------------------------------
// 4) Clases que heredan de SalsaBase
// -----------------------------------
class SalsaCarbonara extends SalsaBase {
    public SalsaCarbonara() {
        //Usamos super para invocar al constructor de la clase base
        super("Salsa Carbonara", new String[]{"nata", "huevo", "queso", "panceta"});
    }
}

class SalsaBolonesa extends SalsaBase {
    public SalsaBolonesa() {
        super("Salsa Bolonesa", new String[]{"carne", "tomate", "cebolla", "zanahoria"});
    }
}

// -------------------
// 5) Clase principal
// -------------------
public class SalsasDemo {
    public static void main(String[] args) {
        // Uso de la interfaz
        RecetaSalsa r1 = new SalsaTomate();
        RecetaSalsa r2 = new SalsaPesto();

        System.out.println("=== Usando la interfaz RecetaSalsa ===");
        r1.preparar();
        r2.preparar();

        // Uso de la clase base
        SalsaBase s1 = new SalsaCarbonara();
        SalsaBase s2 = new SalsaBolonesa();

        System.out.println("\n=== Usando la clase base SalsaBase ===");
        s1.mostrarIngredientes();
        s2.mostrarIngredientes();
    }
}

```

<details>
<summary>💡 Diferencias </summary>
<p><strong>Métodos sobrescritos (en herencia o implementación)</strong> → siempre runtime (dynamic dispatch).</p>
<p><strong>Métodos estáticos, privados o finales</strong> → resueltos en compilación / no-polimórficos.</p>
<p><strong>Diferencia real:</strong> extends usa invokevirtual, implements usa invokeinterface.</p>
</details>

---

<details>
<summary>💡 extends</summary>
<p>Solo puedes <strong>extender de UNA sola clase</strong> (Java no permite herencia múltiple de clases).</p>
<p>Heredas atributos y métodos de la superclase.</p>
<p>Puedes <strong>sobrescribir (override)</strong> métodos para dar un comportamiento específico.</p>
<p>Puedes añadir nuevos atributos o métodos.</p>
<p>extends significa: <i>soy un tipo más específico de esa clase</i>.</p>
</details>

<details>
<summary>💡 implements</summary>
<p>Una interfaz define un <strong>contrato</strong> (qué métodos debe tener la clase), pero no la implementación.</p>
<p>Una clase puede <strong>implementar varias interfaces</strong> → es la forma de tener <i>herencia múltiple</i> en Java.</p>
<p>Obliga a la clase a implementar todos los métodos declarados en la interfaz (salvo que la clase sea abstracta).</p>
<p>Puedes añadir nuevos atributos o métodos.</p>
<p>implements significa: <i>cumplo el contrato de esta interfaz</i>.</p>
</details>