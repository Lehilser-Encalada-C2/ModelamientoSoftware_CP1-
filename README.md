# ModelamientoSoftware_CP1-
Facultad de Ciencias e Ingeniería 
Estudiante: Lehilser Eduardo Encalada Lascano Carrera
Ingeniería de Software, tercer semestre 
Universidad: Universidad Estatal de Milagro (UNEMI)
Asignatura: Modelamiento de Software 
Docente: MSc. Jorge Dumar Guevara Serrano 
Fecha de entrega: 15 de octubre de 2026

1. Caso de estudio:
TravelNow: Plataforma de reservas y check-in de una cadena hotelera.

2. Descripción breve del sistema:
TravelNow necesita una plataforma para que los huéspedes reserven alojamiento y gestionen su estadía antes de llegar al hotel. El cliente consulta la disponibilidad indicando ciudad y fechas de entrada y salida, elige una opción y hace su reserva. Para confirmarla, el sistema registra los datos del cliente, vuelve a comprobar la disponibilidad y calcula el valor total. El pago es electrónico y lo procesa una pasarela de pagos externa. Cuando el pago es aprobado, el sistema confirma la reserva y avisa al cliente mediante un servicio externo de correo electrónico. Antes de la estadía, el cliente puede modificar o cancelar su reserva dentro de las condiciones definidas, hacer el pre check-in indicando su hora estimada de llegada y pedir servicios adicionales, como desayuno o traslado al aeropuerto.
Del lado del hotel, los empleados consultan las reservas y actualizan su estado. El supervisor hace lo mismo y además autoriza las modificaciones que exceden las condiciones normales.

Objetivo general: gestionar las reservas, los pagos, las modificaciones y cancelaciones, y el proceso de pre check-in de los clientes.

Actores
Actor       	        Tipo	                                                 Función
Cliente	            Primario	                            Consulta disponibilidad, reserva, paga, modifica o cancela y hace el pre check-in
Empleado	          Primario	                            Consulta reservas y actualiza su estado
Supervisor         	Primario	                            Hace lo del empleado y autoriza modificaciones excepcionales (especialización de Empleado)
Pasarela de Pagos	  Secundario(externo)	                  Procesa el pago electrónico y lo aprueba o rechaza
Servicio de Correo  Electrónico	Secundario(externo)	      Envía la notificación de confirmación de la reserva

Reglas de negocio:
1. La disponibilidad se comprueba otra vez al confirmar la reserva.
2. La reserva solo se confirma cuando el pago electrónico es aprobado.
3. Modificar o cancelar solo procede antes de la fecha de la estadía y dentro de las condiciones definidas.
4. Los servicios adicionales se agregan solo si el cliente los pide y pasan a formar parte de la reserva.
5. Las modificaciones que exceden las condiciones normales requieren autorización del supervisor.
6. Si la última habitación disponible ya fue asignada, el sistema informa al cliente y le pide una nueva selección.

3. Diagramas incluidos y su relación:
El repositorio contiene tres diagramas UML de comportamiento, todos del mismo caso de estudio y con los mismos actores y procesos.
Diagrama	                                                   Qué muestra
Casos de uso	              Los límites del sistema, los 5 actores y los 14 casos de uso (CU-01 a CU-14), con sus relaciones include, extend y la generalización de Supervisor hacia Empleado
Comunicación(CU-02 Realizar reserva)  Quién se comunica con quién: Cliente, Sistema TravelNow, Pasarela de Pagos y Servicio de Correo Electrónico, con mensajes numerados
Secuencia(CU-02 Realizar reserva)    	Los mismos mensajes en orden temporal, con líneas de vida y barras de activación

Cómo se relacionan entre sí:
°El diagrama de casos de uso define qué hace el sistema y quién lo usa. De ahí sale CU-02 Realizar reserva, que es el caso que desarrollamos en los diagramas de interacción.
°Los diagramas de comunicación y de secuencia representan el mismo flujo con enfoques distintos. La secuencia muestra el cuándo y la comunicación el quién con quién, así que se complementan.
°En ambos, el pago debe ser aprobado (mensaje 5) antes de confirmar la reserva (5.1) y notificar al cliente (5.2). Esto es coherente con las relaciones include del diagrama de casos de uso y con las reglas de negocio.

Relaciones clave en los casos de uso:
°include: CU-02 incluye Registrar datos del cliente (CU-03), Comprobar disponibilidad (CU-04), Calcular valor total (CU-05), Procesar pago electrónico (CU-06) y Enviar notificación de confirmación (CU-07), porque son pasos obligatorios de una reserva exitosa.
°extend: Solicitar servicios adicionales (CU-11) extiende a Realizar pre check-in (CU-10), y Autorizar modificación excepcional (CU-14) extiende a Modificar reserva (CU-08). Ambos son comportamientos opcionales que dependen de una condición.
°Generalización: el Supervisor hereda las funciones del Empleado (CU-12 y CU-13) y suma la autorización de modificaciones excepcionales.

Correcciones aplicadas en la versión definitiva:
°La situación de "última habitación ya asignada" se trata como un flujo de excepción de Realizar reserva y no como un caso de uso aparte, porque no es el objetivo de ningún actor.
°Se diferencia Consultar disponibilidad (objetivo del cliente, CU-01) de Comprobar disponibilidad (verificación interna al reservar, CU-04).
°Cada actor se conecta solo con los casos de uso que el texto del caso justifica.

4. Organización del repositorio


<img width="343" height="282" alt="image" src="https://github.com/user-attachments/assets/2dab7b97-0636-41d8-9ca5-9757b537be93" />


