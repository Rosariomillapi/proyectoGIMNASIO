# Patrón de Diseño Aplicado: Observer 
## Propósito y Tipo del Patrón
**Propósito**: El objetivo de aplicar el patrón Observer en este sistema es resolver el problema de notificar a los socios cuando cambia el estado de su acceso al gimnasio, cuando haya modificaciones en las clases en las que están inscritos, o cuando ocurra algún cambio en su membresía. 
 
**Tipo**: Comportamiento 

**Problema**: En sistemas manuales, los socios no reciben notificacaciones sobre cambios en su estado de acceso, como si su carnet es válido o no, o si su acceso es denegado. Tampoco reciben información de cambios en el horario o estado de las clases a las que están inscritos, o sobre la expiración de su membresía. Esto genera confusión y falta de organización en el sistema. El patrón Observer automatiza este proceso mediante una relación entre un sujeto (como Control De Acceso o Clases) y múltiples Suscriptores (los socios), asegurando que siempre estén informados y actualizados.

## Motivación:
El gimnasio enfrentaba varios problemas relacionados con la comunicación con los socios y el manejo del acceso. Los socios no sabían si su carnet era válido para ingresar al gimnasio, lo que causaba incertidumbre y posibles conflictos en la entrada. Además, no habia una forma de notificar a los socios cuando una clase se cancelaba o cambiaba de horario, lo que provocaba molestias por falta de información o cambios de último minuto. También había problemas con las membresías, ya que los socios no recibían notificaciones cuando su membresía estaba por vencer o había sido renovada, lo que generaba confusión sobre su estatus.

El patrón Observer resuelve estos problemas al permitir sistema que ControlDeAcceso, Clases y Membresías notifiquen a todos los socios suscritos cuando ocurra un cambio, ya sea en el acceso, en el estado de una clase o en el estado de la membresía. Esto asegura una comunicación, manteniendo a los socios siempre informados y actualizados en tiempo real.

## Estructura de Clases
- ![diagramaPATRON](https://github.com/user-attachments/assets/a3eb3ca8-5925-4f9b-8173-720db641cf6a)


## Ejemplo de Código
- [Codigo del patrón utilizado](https://excalidraw.com/#json=ZefbSjkcdiyN76fVe2DDE,KcQmFBX-pVnrFOzbCk1kSw)
