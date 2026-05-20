# Taller02
## Tabla de identificación de paradigmas y justificacion.
1. La carpeta **usuario** ya es OOP puro esto debido a que todo esta dentro de la clase, usa atributos privados, usa los metodos get y set, los datos estan encapsulados ya que no son publicos y accede mediante getters y setters, a su vez no usa metodos estaticos y no toda su logica se encuentra en el main.

2. La carpeta **Transmission listener** tambien es OOP puro, al ser una carpeta *interface* usa la abstraccion y el polimorfismo, el programa trabajo con objetos, a su vez su paradigma tambien es orientado a eventos.

3. La carpeta **Transmission** tambien es OOP puro, ya que todo esta encapsulado dentro de la clase, sus atributos son privados y sus metodos publicos algo que no rompe el OOP puro, contiene metodos dentro de la clase y accede mediante getters y setters, no posee metodos estaticos y no esta en el main, a su vez el paradigma es orientado a eventos.

4. La carpeta **StatsService** no es OOP puro ya que dentro de esta carpeta hay metodos estaticos y la logica esta separada del objeto principal, su paradigma es estructurado.

5. La carpeta **Notification Component** es OOP puro ya que al tener implements y Override estas usando herencia y polimorfismo y su paradigma es orientado a eventos.

6. La carpeta **Mensaje** tambien es OOP puro ya que sus atributos son privados, usa los getters y los setters, no usa metodos estaticos y su logica no esta dentro del main.

7. La carpeta **Main** nunca es OOP puro.

8. La carpeta **Chat Component** es OOP puro ya que hace uso de la herencia y polimorfismo a traves de *implements* y *override* y su paradigma tambien es orientado a eventos.

9. La carpeta **Attendance Component** tambien es OOP puro, al igual que **Chat Component** hace uso de la herencia y el polimorfismo a traves de *implements* y *override* y su paradigma es orientado a eventos.


-------------

## Diagrama de clases OOP puro

El sistema está compuesto por las clases principales Transmision, Usuario y Mensaje. Transmision gestiona la información de la clase, incluyendo el título, el profesor, la lista de asistentes, los mensajes y los listeners. Usuario representa a los participantes con atributos como nombre y rol, mientras que Mensaje almacena el usuario que lo envía y su contenido.

La interfaz TransmisionListener define los métodos que responden a eventos de la transmisión. Las clases ChatComponent, NotificationComponent y AttendanceComponent implementan esta interfaz para manejar distintos comportamientos cuando ocurre un evento.

Transmision mantiene una relación de tipo uno a muchos con los listeners, notificándolos cuando se inicia la transmisión, un usuario se une o se envía un mensaje.

----------------------

## 

Se tomó la clase StatsService, la cual utilizaba métodos estáticos para mostrar información de la transmisión

    long estudiantes = transmision.getAsistentes().stream()
        .filter(u -> "estudiante".equals(u.getRol()))
        .count();
Lo refactorizamos de manera que sea OOP puro:

    public class Transmision {

        private List<Usuario> asistentes;

        public long contarEstudiantes() {
            return asistentes.stream()
                .filter(u -> "estudiante".equals(u.getRol()))
                .count();
        }
    }
Este cambio hace que sea OOP mas puro ya que tenemos objetos privados los cuales se hacen cargos de ellos mismos y la responsabilidad que antes tenian que era el calculo paso a ser de la clase transmission.  