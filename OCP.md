# Principio Abierto/Cerrado (OCP)
El Principio Abierto/Cerrado (OCP) establece que las clases deben estar abiertas para la extensión, pero cerradas para la modificación. Esto significa que podemos agregar nuevas funcionalidades al sistema sin alterar las clases existentes, evitando así introducir errores en el código base.
**Tipo del Principio:** Modularidad y extensibilidad.
# Motivación
En un sistema de notificaciones, puede surgir la necesidad de agregar nuevos tipos de notificaciones. Si todas las notificaciones están implementadas dentro de una sola clase, cualquier cambio implicará modificar el código base, lo que viola OCP.
**Problema original:**
Una clase de notificación que maneja todos los tipos de notificaciones internamente es difícil de mantener.
**Solución con OCP:**
Creamos una interfaz Notificador y subclases para cada tipo de notificación (NotificadorPorCorreo, NotificadorPorSMS, etc.).
# Estructura de Clases
![solid20mejor](https://github.com/user-attachments/assets/cfb9ce34-40a8-4a22-a941-d96e76e4b37d)
# Ejemplo de Código

```
// PRINCIPIO OCP: Interfaz para las notificaciones
interface Notificador {
    void enviarContenido(String contenido);
}
// Clases que lo implementan: Notificador por correo
class NotificadorPorCorreo implements Notificador {
    @Override
    public void enviarContenido(String contenido) {
        System.out.println("Enviando correo: " + contenido);
    }
}

// Notificador por SMS
class NotificadorPorSMS implements Notificador {
    @Override
    public void enviarContenido(String contenido) {
        System.out.println("Enviando SMS: " + contenido);
    }
}
```
```
// asi quedaria implementado con la clase; Reserva 
class Reserva {
    private String nombreSocio;
    private String claseSeleccionada;
    private String fechaReserva;
    private String horaReserva;
    private Notificador notificador;

    public Reserva(String nombreSocio, String claseSeleccionada, String fechaReserva, String horaReserva, Notificador notificador) {
        this.nombreSocio = nombreSocio;
        this.claseSeleccionada = claseSeleccionada;
        this.fechaReserva = fechaReserva;
        this.horaReserva = horaReserva;
        this.notificador = notificador;
    }

    public void confirmarReserva() {
        String contenido = "Reserva confirmada para " + nombreSocio +
                " en la clase " + claseSeleccionada +
                " el día " + fechaReserva +
                " a las " + horaReserva;
        notificador.enviarContenido(contenido);
    }
}
```
