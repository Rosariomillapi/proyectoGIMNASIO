# Principio de Inversión de Dependencias (DIP)
El Principio de Inversión de Dependencias (DIP) establece que las clases de alto nivel no deben depender de las clases de bajo nivel.
Ambas deben depender de abstracciones (interfaces). Además, las abstracciones no deben depender de detalles concretos, sino que los detalles deben depender de las abstracciones.

**Problema Original:**

**Control de Acceso:** La clase ControlDeAcceso podría depender directamente de la implementación específica de validación de acceso, lo que dificulta cambiar o extender el sistema (por ejemplo, si se quisiera cambiar el método de validación).
**Pago:** La clase Pago dependería de la lógica concreta de diferentes tipos de pago, lo que hace que el sistema sea difícil de extender cuando se añaden nuevos métodos de pago (como transferencia, tarjeta, etc.).
**Gestor de Reserva:** La clase GestorDeReserva depende directamente de clases concretas como ConfirmarReserva, CancelarReserva y HistorialDeReserva, lo que hace que la modificación de una clase concreta afecte el comportamiento del sistema.

# Solución con DIP:

**Control de Acceso** La clase ControlDeAcceso dependerá de una interfaz ValidadorDeAcceso, y no de clases concretas, lo que permite agregar nuevas validaciones sin cambiar ControlDeAcceso.
**Pago:** La clase Pago dependerá de una interfaz MetodoDePago, lo que permite agregar nuevos métodos de pago (como transferencia, tarjeta o efectivo) sin modificar la clase Pago.
**Gestor de Reserva:** La clase GestorDeReserva dependerá de la interfaz GestorDeReserva, lo que permite gestionar las reservas sin depender de clases específicas como ConfirmarReserva, CancelarReserva, o HistorialDeReserva.

# Estructura de Clases
![solid20mejor](https://github.com/user-attachments/assets/e8783172-37d1-4360-81ef-eef10320e39d)

# Ejemplo de Código
```
// Interfaz para validar acceso de socio
interface ValidadorDeAcceso {
    boolean validarAcceso(String idSocio);
}
// Clase que depende de la interfaz ValidadorDeAcceso
class ControlDeAcceso {
    private ValidadorDeAcceso validador;

    // Constructor que recibe una implementación de ValidadorDeAcceso
    public ControlDeAcceso(ValidadorDeAcceso validador) {
        this.validador = validador;
    }

    public void verificarAcceso(String idSocio) {
        if (validador.validarAcceso(idSocio)) {
            System.out.println("Acceso permitido para el socio: " + idSocio);
        } else {
            System.out.println("Acceso denegado para el socio: " + idSocio);
        }
    }
}
// Interfaz para procesar pagos
interface MetodoDePago {
    void procesarPago(double monto);
}
// Clase que depende de la interfaz MetodoDePago
class Pago {
    private double monto;
    private MetodoDePago metodoDePago;

    // Constructor que recibe una implementación de MetodoDePago
    public Pago(double monto, MetodoDePago metodoDePago) {
        this.monto = monto;
        this.metodoDePago = metodoDePago;
    }

    public void realizarPago() {
        metodoDePago.procesarPago(monto);
    }
}
// Implementación del pago con tarjeta
class PagoTarjeta implements MetodoDePago {
    @Override
    public void procesarPago(double monto) {
        System.out.println("Procesando pago con tarjeta: $" + monto);
    }
}

// Implementación del pago por transferencia
class PagoTransferencia implements MetodoDePago {
    @Override
    public void procesarPago(double monto) {
        System.out.println("Procesando pago por transferencia: $" + monto);
    }
}

// Implementación del pago en efectivo
class PagoEfectivo implements MetodoDePago {
    @Override
    public void procesarPago(double monto) {
        System.out.println("Procesando pago en efectivo: $" + monto);
    }
}
// Interfaz para gestionar reservas
interface GestorDeReserva {
    void cancelarReserva(String reservaId);
    void confirmarReserva(String reservaId);
    void mostrarHistorialDeReservas();
}
// Clase que implementa la interfaz GestorDeReserva
class ConfirmarReserva implements GestorDeReserva {
    @Override
    public void cancelarReserva(String reservaId) {
        System.out.println("Reserva cancelada: " + reservaId);
    }

    @Override
    public void confirmarReserva(String reservaId) {
        System.out.println("Reserva confirmada: " + reservaId);
    }

    @Override
    public void mostrarHistorialDeReservas() {
        System.out.println("Mostrando historial de reservas...");
    }
}
// Clase que utiliza la interfaz GestorDeReserva para manejar las reservas
class GestorDeReserva {
    private GestorDeReserva gestor;

    // Constructor que recibe una implementación de GestorDeReserva
    public GestorDeReserva(GestorDeReserva gestor) {
        this.gestor = gestor;
    }

    public void cancelarReserva(String reservaId) {
        gestor.cancelarReserva(reservaId);
    }

    public void confirmarReserva(String reservaId) {
        gestor.confirmarReserva(reservaId);
    }

    public void mostrarHistorialDeReservas() {
        gestor.mostrarHistorialDeReservas();
    }
}
```

