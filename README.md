# so-exam2



**Parcial 2**


**Curso:** Sistemas Operativos  

**Docente:** Daniel Barragán C.  

**Tema:** Introducción a systemd 


**Correo:** daniel.barragan at correo.icesi.edu.co

**Nombre:** Tomas Julian Lemus Rubiano

**Código:** A00054616  

**URL:** https://github.com/tjlr50/so-exam2/edit/A00054616/Parcial2


Se crean y se ejecutas los procesos a los que se les cambiarán sus caracteristicas de procesamiento. Cabe aclarar,que se deben habilitar los permisos de ejecución para rpobar su funcionamiento.

![][1]


### CPUQuotas


Posteriormente, se establecen los servicios por medio del systemctl;

Primero, se otorgan permisos con el comando chmod.

Segundo, se deben habilitar los servicios.

Tercero,se verifica el estatus como inactivo para los servicios.

![][2]

Una vez comprobados los pasos para el primero servicio, se repiten para el segundo (lol2.service)

![][4]

Ahora, se cargan los demonios y se ejecutan los servicios con el comando start.

![][3]

Por medio del comando top que ilustra los procesos de la CPU, se observa que ambos cumplen con la cuota asignada anteriormente; inclusive, despues de eliminar un proceso, el otro sigue cumpliendo con la cuota designada.

![][5]
![][6]

### CPUShares

A partir de los service configurados anteriormente, se utiliza el comando vi para editarlos y en este caso, asignar un CPUShares de 750 a un servicio y, 250 al otro. De esta forma:

![][7]

Para efectuar los cambios en los services, se cargan nuevamente los demonios y se ejecutan los servicios con el comando start.

![][8]

Nuevamente el comando top permite listar los procesos con su respectivo uso de la  CPU.

![][9]

PD: Fue necesario elminar los procesos anteriores para visualizar el cambio de la columna %CPU.

Finalmente, se elimina uno de los procesos, y se evidencia como el proceso en ejecución casi que alcanza el 100% de la CPU.

![][10]


[1]:scriptlolypermisos.PNG

[2]:servicePermisosEnableStatus.PNG

[3]:daemonystart.PNG

[4]:repite.PNG


[5]:top.PNG

[6]:.top2PNG


[7]:cpushare.PNG

[8]:startshares.PNG

[9]:topshare.PNG

[10]:topsharekill.PNG

[]:.PNG
[]:.PNG
