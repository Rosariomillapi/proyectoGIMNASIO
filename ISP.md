# Principio de Segregación de Interfaces (ISP)
El Principio de Segregación de Interfaces (ISP) establece que las interfaces deben ser pequeñas y específicas, de modo que una clase solo implemente los métodos que realmente necesita. Este principio evita el diseño de interfaces grandes y generalistas que obligan a las clases a implementar métodos que no utilizan.
**Propósito:** Dividir las interfaces en contratos más pequeños y específicos para evitar acoplamiento innecesario.
**Tipo del Principio:** Diseño modular y cohesivo.
# Motivación
El sistema de Atención a Consultas enfrentaba el problema de tener una interfaz general que obligaba a las clases a implementar métodos innecesarios.
Por ejemplo, una clase que solo manejaba consultas de reservas también debía implementar métodos para consultas sobre la expiración de membresía o clases disponibles. 
Esto generaba:

**Métodos innecesarios:** Las clases se veían forzadas a implementar métodos que no utilizaban, como los de otros tipos de consultas.
Acoplamiento y falta de cohesión: Las clases manejaban más responsabilidades de las necesarias, lo que complicaba la extensión y el mantenimiento del sistema.

El Principio de Segregación de Interfaces (ISP) resuelve este problema dividiendo las interfaces en partes pequeñas y específicas.
Así, cada clase solo implementa los métodos que realmente necesita. En el caso de Atención a Consultas, la clase implementa solo la interfaz RecibirConsultaDelSocio, evitando sobrecargarla con métodos irrelevantes.
Esto mejora la cohesión y permite agregar nuevos tipos de consultas sin modificar las clases existentes.TAmbien Aplicamos este Principio a Registro de acceso


 # Ejemplo de Código
 ```
// Interfaz para recibir consultas de los socios
interface RecibirConsultaDelSocio {
    void recibirConsulta(String consulta);
}

// Clase que implementa la interfaz para recibir consultas de los socios
class AtencionAConsultas implements RecibirConsultaDelSocio {
    private String tipoDeConsulta;
    private String fechaDeConsulta;

    public AtencionAConsultas(String tipoDeConsulta, String fechaDeConsulta) {
        this.tipoDeConsulta = tipoDeConsulta;
        this.fechaDeConsulta = fechaDeConsulta;
    }

    // Métodos para consultar tipos específicos
    public void consultarReserva() {
        System.out.println("Consultando reserva...");
    }

    public void consultarExpiracionMembresia() {
        System.out.println("Consultando restricción de membresía...");
    }

    public void consultarSobreUnaClase() {
        System.out.println("Consultando detalles de la clase...");
    }

    // Implementación del método de la interfaz
    @Override
    public void recibirConsulta(String consulta) {
        System.out.println("Consulta recibida: " + consulta);
        // Lógica para manejar la consulta
    }
}

// Interfaz para reportar el mantenimiento de equipos
interface Reportar {
    void reportarMantenimiento(String equipo, String detalle);
}

// Clase que implementa la interfaz para reportar mantenimiento de equipo
class Recepcionista implements RecibirConsultaDelSocio, Reportar {
    @Override
    public void recibirConsulta(String consulta) {
        System.out.println("Recepcionista recibiendo consulta: " + consulta);
        // Lógica para gestionar la consulta
    }

    @Override
    public void reportarMantenimiento(String equipo, String detalle) {
        System.out.println("Reportando mantenimiento de equipo: " + equipo);
        System.out.println("Detalles del mantenimiento: " + detalle);
    }
}

// Clase que implementa la interfaz Reportar
class RegistroDeEquipos implements Reportar {
    private String nombreEquipo;
    private String estadoEquipo;

    public RegistroDeEquipos(String nombreEquipo, String estadoEquipo) {
        this.nombreEquipo = nombreEquipo;
        this.estadoEquipo = estadoEquipo;
    }

    // Método para programar mantenimiento
    public void programarMantenimiento(String fecha) {
        System.out.println("Programando mantenimiento para el equipo: " + nombreEquipo);
        System.out.println("Estado actual: " + estadoEquipo);
        System.out.println("Fecha de mantenimiento programada: " + fecha);
    }

    @Override
    public void reportarMantenimiento(String equipo, String detalle) {
        System.out.println("Reporte de mantenimiento para el equipo: " + equipo);
        System.out.println("Detalles del mantenimiento: " + detalle);
    }
}

    
```
