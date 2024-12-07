# Principio de Responsabilidad Única (SRP)

El Principio de Responsabilidad Única (SRP) establece que cada clase debe tener una única razón para cambiar. Esto significa que cada clase debe ser responsable de una única tarea o funcionalidad dentro del sistema.

**Propósito:** Evitar que una clase maneje múltiples responsabilidades, lo que dificulta el mantenimiento y la escalabilidad del sistema.
**Tipo del Principio:** Principio de diseño modular y cohesivo.

# Motivación
En sistemas complejos, una clase que maneja múltiples responsabilidades tiende a ser difícil de mantener y propensa a errores. Si una funcionalidad cambia, podría romperse el comportamiento de otras partes del sistema.

**Problema original:**
Por ejemplo, una clase Notificación que maneja notificaciones de reservas, pagos, y membresías mezcla varias responsabilidades. Esto dificulta agregar nuevos tipos de notificaciones sin afectar a las existentes.

# Solución con SRP:

Dividimos los métodos de **Notificación** en clases específicas:
**NotificacionReserva**: Para enviar confirmaciones de reserva.
**NotificacionPago:** Para confirmaciones de pago.
**NotificacionMembresia:** Para alertas de membresía.
De forma similar, el principio SRP se aplica a otras clases (Clase, ControlDeAcceso, RegistroDeEquipos,Notificación, y Reserva), asegurando responsabilidades claras y separadas.
# Estructura de Clases
![solid17mejor](https://github.com/user-attachments/assets/8b21c61d-46ce-41e6-bdd9-55ce08bc9913)
# Ejemplo De Código:
```
// Clase:Carnet Digital
class CarnetDigital {
    private String qrSocio;
    private String nombreSocio;
    private String tipoMembresia;

    public CarnetDigital(String qrSocio, String nombreSocio, String tipoMembresia) {
        this.qrSocio = qrSocio;
        this.nombreSocio = nombreSocio;
        this.tipoMembresia = tipoMembresia;
    }

    public void mostrarCarnetDigital() {
        System.out.println("Carnet Digital:");
        System.out.println("QR: " + qrSocio);
        System.out.println("Nombre: " + nombreSocio);
        System.out.println("Membresía: " + tipoMembresia);
    }
}
```
```
// control de acceso y sus clases: 
class ControlDeAcceso {
    private String registroDeIngresos;
    private String registroDeSalidas;

    public ControlDeAcceso(String registroDeIngresos, String registroDeSalidas) {
        this.registroDeIngresos = registroDeIngresos;
        this.registroDeSalidas = registroDeSalidas;
    }

    public void verificarAcceso(String qrCodigo, boolean estadoMembresia) {
        if (estadoMembresia) {
            System.out.println("Acceso permitido para QR: " + qrCodigo);
        } else {
            System.out.println("Acceso denegado. Membresía inactiva.");
        }
    }
}
// clase complementaria
class EstadoDeMembresia {
    public void verificarEstadoDeMembresia(String qrCodigo, boolean estadoMembresia) {
        System.out.println("Verificando estado de membresía para QR: " + qrCodigo);
        if (estadoMembresia) {
            System.out.println("Estado: Membresía activa.");
        } else {
            System.out.println("Estado: Membresía inactiva.");
        }
    }
}
```

```
// Registro de Equipo
class RegistroDeEquipos {
    private String nombreEquipo;
    private String estadoEquipo;

    public RegistroDeEquipos(String nombreEquipo, String estadoEquipo) {
        this.nombreEquipo = nombreEquipo;
        this.estadoEquipo = estadoEquipo;
    }

    public void programarMantenimiento(String fecha) {
        System.out.println("Equipo: " + nombreEquipo + " programado para mantenimiento en " + fecha);
    }
}
///clase complementaria
class Equipo {
    public void verEquipoDisponible(String equipo) {
        System.out.println("Equipo disponible: " + equipo);
    }
}

//Clase complementaria
class ActualizacionDeEstado {
    public void actualizarEstado(String equipo, String nuevoEstado) {
        System.out.println("Actualizando estado del equipo: " + equipo + nuevoEstado);
    }
}
```

```
class Recepcionista {
    private String idRecepcionista;
    private String nombre;
    private String turno;
    private String correo;
    private String telefono;

    public Recepcionista(String idRecepcionista, String nombre, String turno, String correo, String telefono) {
        this.idRecepcionista = idRecepcionista;
        this.nombre = nombre;
        this.turno = turno;
        this.correo = correo;
        this.telefono = telefono;
    }

    public void responderConsultas(String consulta) {
        System.out.println("Recepcionista " + nombre + " (Turno: " + turno + ") está respondiendo la consulta:");
        System.out.println("Consulta: " + consulta);
    }
}
```

```
// Clase Notificación
class Notificacion {
    private String mensaje;
    private String destinatario;

    public Notificacion(String mensaje, String destinatario) {
        this.mensaje = mensaje;
        this.destinatario = destinatario;
    }

    public void enviarNotificacion() {
        System.out.println("Enviando notificación a " + destinatario + ": " + mensaje);
    }
}

//clase complementarias
class NotificacionReserva {
    public void enviarReservaConfirmada(String reserva) {
        System.out.println("Notificación: Reserva confirmada para " + reserva);
    }
}

class NotificacionPago {
    public void enviarConfirmacionPago(String pago) {
        System.out.println("Notificación: Pago confirmado de " + pago);
    }
}

class NotificacionMembresia {
    public void enviarAlertaMembresia(String socio) {
        System.out.println("Notificación: Alerta de membresía para " + socio);
    }
}
```

```
// clase: Clase
class Clase {
    private String nombreClase;
    private String fechaClase;
    private String horaClase;

    public Clase(String nombreClase, String fechaClase, String horaClase) {
        this.nombreClase = nombreClase;
        this.fechaClase = fechaClase;
        this.horaClase = horaClase;
    }
public void listaDeClases() {
        System.out.println("Clase: " + nombreClase);
        System.out.println("Fecha: " + fechaClase);
        System.out.println("Hora: " + horaClase);
    }
}
// clase complementarias
class ConsultasSobreClase {
    public void añadirConsulta(String consulta) {
        System.out.println("Consulta añadida: " + consulta);
    }
}

class Cupos {
    public void actualizarCupos(int nuevosCupos) {
        System.out.println("Cupos disponibles actualizados a: " + nuevosCupos);
    }
}
```

```
// Clase: Reserva
class Reserva {
    private String nombreSocio;
    private String claseSeleccionada;
    private String fechaDeLaReserva;
    private String horaDeLaReserva;
    private String estado;

    public Reserva(String nombreSocio, String claseSeleccionada, String fechaDeReserva, String horaDeReserva) {
        this.nombreSocio = nombreSocio;
        this.claseSeleccionada = claseSeleccionada;
        this.fechaDeReserva = fechaDeReserva;
        this.horaDeReserva = horaDeReserva;
        this.estado = "Pendiente";
    }

    public void reservarClase() {
        this.estado = "Confirmada";
        System.out.println("Clase reservada para: " + nombreSocio);
    }
// clases complementarias
class ConfirmarReserva {
    public void confirmar(Reserva reserva) {
        reserva.setEstado("Confirmada");
        System.out.println("Reserva confirmada:");
        System.out.println("Socio: " + reserva.nombreSocio);
        System.out.println("Clase: " + reserva.claseSeleccionada);
        System.out.println("Fecha: " + reserva.fechaReserva);
        System.out.println("Hora: " + reserva.horaReserva);
        System.out.println("Estado: " + reserva.getEstado());
    }
}
class CancelarReserva {
    public void cancelar(Reserva reserva) {
        reserva.setEstado("Cancelada");
        System.out.println("Reserva cancelada:");
        System.out.println("Socio: " + reserva.nombreSocio);
        System.out.println("Clase: " + reserva.claseSeleccionada);
        System.out.println("Estado: " + reserva.getEstado());
    }
}
ublic void mostrarHistorial() {
        System.out.println("Historial de Reservas:");
        for (String reserva : historial) {
            System.out.println("- " + reserva);
        }
    }
```
