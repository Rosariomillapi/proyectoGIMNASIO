 # PROYECTO "FITNESS PRO"
- **NOMBRE Y APELLIDO:** Rosario Millapi
- **MATERIA Y CARRERA:** Diseño orientado a objetos  - Tecnicatura En Programación 
- **PROFESOR:** Matias Velazquez
- **AÑO:** 2024

 ## **INTRODUCCIÓN**
 El sistema para el gimnasio "Fitness Pro" busca mejorar los procesos internos que actualmente se hacen de manera manual, como el registro de  de manera digital,socios, las reservas de clases y el control de acceso. El objetivo es automatizar las operaciones del gimnasio. Los socios podrán registrarse, reservar clases y acceder al agilizando todo el proceso y eliminando los problemas que surgen con el método manual.

 ## **REQUISITOS ABORDADOS**
 - Registro de socios digital.
 - Reservas online. 
 - Control de acceso con carnet digital.
 - Gestión de mantenimiento de equipos.

---
## **Diagramas y Diseños**

 ## **Diagramas UML:**

 - [Diagrama de casos de uso](https://drive.google.com/file/d/1HJboCE5IGiOjh_onm2bhqtqUCmFkbG68/view?usp=sharing)

  - [Escenario de casos de usos](https://ucesvirtual-my.sharepoint.com/:x:/g/personal/r_millapi_comunidad_uces_edu_ar/EdGoQyUKFzRFpfQAryOJuqUBxhEbcWsOjB7JKW-cBIPbMQ?e=VMdSbH)
   
  ### **Diagrama De Clases:**

  ### **Diagrama V2:**
- ![diagramadeClasesV2](https://github.com/user-attachments/assets/96ae57db-688d-420d-92e8-e075d9b00bc4)





- [Diagrama De Actividades](https://drive.google.com/file/d/1ij7q7-M_28qmoa0G5nJe0TUEylpXxDOp/view?usp=sharing)

### **Diagrama De Secuencia:**

[Caso De uso 1](https://drive.google.com/file/d/1kOWA4urbu0nqzt-Il1EwyePs_UWgMnYu/view?usp=sharing)

[Caso De Uso 2](https://drive.google.com/file/d/1KS72_F-5u2kpkWr-DeSS9cdnCbTlxtZs/view?usp=sharing)

[Caso De uso 3](https://drive.google.com/file/d/1auvOvi7ZLlYV4YMovxFggDfsPVEzJDKN/view?usp=sharing)

[Caso De Uso 4](https://drive.google.com/file/d/15IGNfOsTHtXvLsQG_IH5UZ1Ynpx7VBGY/view?usp=sharing)

[Caso De Uso 5](https://drive.google.com/file/d/1moEQ8GdDERg1IivG2uOsrPtwysAWdz_p/view?usp=sharing)

## **Herramientas Agiles:**
- ![matrizdefinitiva1](https://github.com/user-attachments/assets/de2cb4fe-8736-4f00-8917-76ddc8f643d7 "Matriz CLAE")



- [TajetasCRC](https://drive.google.com/file/d/1q82gGCUhgcrwphYNKUyMSf58UGA9aS1h/view?usp=sharing)

## Implementación del Patrón Observer  

### Patrón Implementado  
Se implementó el patrón de diseño OBSERVER, que permite que los objetos observadoras como `Socio` reciban notificaciones  cuando ocurren cambios en los estados de otras clases (como `ControlDeAcceso`, `Membresia`, y `Clase`).  

### Problema Resuelto  
El patrón Observer soluciona el problema de mantener sincronizados a los socios con los cambios importantes en el sistema:  
- Notificaciones sobre el estado de su membresía (activa o expirada).  
- Avisos de cancelaciones o cambios en las clases del gimnasio.  
- Actualizaciones relacionadas con el acceso permitido o denegado al gimnasio.  

### Documento Explicativo  
 PatrónDeDiseño.md

