# Principio de Sustitución de Liskov (LSP)
El Principio de Sustitución de Liskov (LSP) establece que una subclase debe ser sustituible por su clase base sin alterar el correcto funcionamiento del sistema. En términos más simples, si una clase hija reemplaza a su clase padre, el sistema debe seguir comportándose de manera coherente.

**Propósito:** Garantizar que las subclases respeten el comportamiento esperado de la clase base, manteniendo la compatibilidad.
**Tipo del Principio:** Herencia y polimorfismo.
# Motivación
En un sistema de membresías para un gimnasio, las clases Membresia y MembresiaPremium tienen características diferentes. Si no diseñamos correctamente la relación entre estas clases, es posible que el comportamiento esperado de Membresia no se cumpla cuando usamos una instancia de MembresiaPremium. Esto puede causar errores en el sistema.

**Problema original:**
Si MembresiaPremium tiene métodos adicionales como obtenerBeneficioAdicional() que no existen en Membresia, pero no aseguramos su uso de forma consistente, podría romperse el principio.

**Solución con LSP:**
Creamos una interfaz Beneficios que define el método obtenerBeneficioAdicional(). Esto permite que MembresiaPremium implemente esta funcionalidad adicional sin alterar la relación de herencia entre Membresia y sus clases adicionales.

# Estructura de Clases
![solid20mejor](https://github.com/user-attachments/assets/39b9ce3d-d9b6-4efa-a676-2df04f190b30)

# Ejemplo de Código
```
class Membresia {
    protected String tipo;
    protected String fechaDePago;

    public Membresia(String tipo, String fechaDePago) {
        this.tipo = tipo;
        this.fechaDePago = fechaDePago;
    }

    public void actualizarMembresia() {
        System.out.println("Actualizando membresía de tipo: " + tipo);
    }
class MembresiaComun extends Membresia {
    public MembresiaComun(String fechaDePago) {
        super("Común", fechaDePago);
    }

    @Override
    public void actualizarMembresia() {
        System.out.println("Actualizando membresía común con fecha de pago: " + fechaDePago);
    }
}
interface Beneficios {
    void obtenerBeneficioAdicional();
}
class MembresiaPremium extends Membresia implements Beneficios {
    public MembresiaPremium(String fechaDePago) {
        super("Premium", fechaDePago);
    }

    @Override
    public void actualizarMembresia() {
        System.out.println("Actualizando membresía premium con fecha de pago: " + fechaDePago);
    }

    @Override
    public void obtenerBeneficioAdicional() {
        System.out.println("Beneficio adicional: Descuento en clases especializadas.");
    }
}
```
