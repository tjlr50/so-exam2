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



### Limitación de recursos hardware

Partiendo de la importancia de la seguridad en nuestros servicios:
A veces puede que nuestra  información no sea tan importante como para ser atacado por un hacker, o que una X persona quiso probar un tutorial que encontró en internet pueda alterar nuestros servicios o jugar con nuestra reputación, es un riesgo que se puede minimizar.
Por ejemplo:

Mediante cgroups podemos limitar el acceso al hardware y no permitir a los contenedores más uso de hardware del que nosotros requerimos. En ello podemos limitar tanto en CPU como en RAM o red. En este caso usamos la limitación de la CPU con los siguientes grupos de control:

## 1. CPUQuota:
Es un valor representado en porcentaje, el cual se asigna a un proceso para determinar el tiempo maximo en el que podrá abastecer de cpu en un periodo (en microsegundos) y la cuota mínima permitida para la cuota o el período es 1 ms.
Hay dos formas en que un grupo puede ser acelerado: Consumir completamente su propia cuota dentro de un período o que la cuota de uno de los padres está completamente consumida dentro de su período.


## 2. CPUShares:

Como su nombre lo indica, especifica el porcentaje de recursos de CPU disponibles para compartir la CPU según la cantidad de procesos y el consumo necesario de cada uno de ellos. Lo cual permite una administración dinamica para los servicios que da pie a una característica técnica, llamada hyperthreading, que permite que el servidor físico parezca tener realmente 16 unidades de CPU. Hyperthreading aprovecha el hecho de que las CPU suelen estar inactivas, a la espera de que se completen otros procesos relativamente más lentos, como los accionamientos de las unidades de disco. 

En conclusión, Es preferible usar CPUQuotas cuando se quiera evitar la ejecución de procesos que requieran timepos elevados de CPU. Mientras que CPUShares es preferible cuando se desea una mejor asignación de recursos a los procesos y una mejor distribución de la CPU, pues no se dejarían recursos sin utilizar. 


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

