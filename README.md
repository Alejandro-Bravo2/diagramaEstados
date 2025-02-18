# diagramaEstados
He realizado este diseño porque en mi opinion
la puerta solo podría tener 2 estados finalizados y 2 en proceso.
##### Estados finalizados
- `Abierta`
- `Cerrada`
##### Estados en proceso
- `Abriendose`
- `Cerrandose`


Primero lo que hace es ponerse a detectar pero antes espera 10 segundos porque la actividad
pone que tiene que esperar un tiempo antes de ponerse a detectar para que le pueda
dar tiempo al usuario a acabar lo que estaba haciendo.
En detectando se queda detectando hasta encontra una persona.
En caso de si haber detectado alguien lo que hace es comprobar el estado anterior para saber si anteriormente
estaba cerrada o abierta para saber que proceso deberá hacer.
Luego se pone en ese estado y vuelve a esperar 10 segundos y se repite este bluque.


DIAGRAMA ESTADO:


@startuml

[*] --> Cerrada
[*] --> Abierto

Cerrada : Cerrado totalmente
Abierto : Abierta totalmente



Cerrada --> Detectando : Espera 10 segundos
Detectando : Comprobando si hay alguien a la vista


state condicion <<choice>>



Detectando --> Detectando: Detectando si hay alguien


Abierto --> Detectando: Espera 10 segundos
Detectando --> condicion: Cuando haya detectado alguien
condicion --> Abriendose: Si el estado anterior de la operación era cerrada
condicion --> Cerrandose: Si el estado anterior de la operación era abierta

Cerrandose --> Cerrada
Abriendose --> Abierto



Abriendose : En proceso de abrirse
Cerrandose : En proceso de cerrarse
