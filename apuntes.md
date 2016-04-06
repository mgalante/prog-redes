#Programacion en Redes
Diego Malafetti
email: dmaraf@palermo.edu


##Calendario 
*08/03 
*15/03
*22/03
*29/03
*05/04
*12/04
*19/04
*26/04
*03/05
*10/05 Primer Parcial
*17/05
*24/05 --No hay clase--
*31/05
*07/06
*14/06 
*21/06 Segundo Parcial
*28/06 Primer Recuperatorio
*06/07 Segundo Recuperatorio
 
##Trabajo Práctico
Definicion 
Descoponer el problema en partes


##Proceso

* Un programa en institucion
* Una instancia de un programa corirendo en una computadora
* Una entidad que puede ser asiganda ye ejcutada en el procesador
* Una entidad carcterizada por la ejeucion de una secuencia de instrucciones, un estado y un conjutno de rcursos del sistema asociados.

Que tiene un proceso:
* Un pid que lo identifica
* Prioridad
* Punteros de memoria
* ...

Es un codigo + datos (pcb)
Cuando se crea un proceso
Nuevo usuario
servicio
coreado por otro proceso (Process Spawn)
    Relacion Parent Child


##Modos de Ejecucion
El sistema operativo nos ofrece una interfaz para manejar memoria, disco. Lo hace a traves de la API (aplication program interface).
Por ejemplo fopen, tenia que incluir el headrer de stdlib.h. Eso es un wrapper para la llamada abstraer la llamada al sistema, y que funcione en cualquier plataforma. Al invocarlo, en algumento hay una invocacion al sistema operativo, y el tranfiere el control al mismo para que levnte el archivo y nos devuelta un puntero al mismo. Esas instrucciones ocurren en Kernel Mode. 



###Process scheduler
Decide que se ejecuta en una procion de tiempo. Preemtive (puede sacar un proceso de ejecucion).

##Dispatcher
Le da el control al CPU al proceso seleccionado por el short term scheduler.

###Fibers
son como hilos pero en control del programa.


Fork()
Crea un nuevo proceso en el sistema. La llamada reotrna dos veces (called once, return twice)
Retorna 0 para el hijo, y el pid del child para el padre.
El kernel hace una copia de todos los files descriptors.
Otras vecariantes mas modernas incluyen: vfork(), posix_spawn();

fork + exec.


#Multithreading
Capacidad del operativo para soportar multiples y concurrentes caminos de ejecucion dentro de un mismo preceos

Proceso tiene
    Manejo de recursos -> proceso o tarea (task
    Schedulling o ejecution -> Thread o preceso ligero 
    
    
##Que uso se le da a mutliples threads
Ejecucion en background 
Procesamiento asincrononico
Velocidad de ejecucion
Programacion modular




##Beneficios
Toma menos tiempo crear un thread que el proceso completo.
terminar
swichear


##Process y thread affinity 
A que cpu mando a procesar


Multiprogracion - muchos procesos en un solo procesador . Concurrente
Multiprocesamiento - multiples procesos en multiples procesadores. Concurrente y paralelo
Procesamiento Distribuido - Manejo multiples procesos en sistema distribuidos

##User Level Thread vs Kernel Level Thread

callback pattern
typedef void(* ON_DATA_CALLBACK)(void *buffer, size_t size)

void onDataCallback(void *buffer, size_t size)
{
    free(buffer);
}


void handleSocket(ON_DATA_CALLBACK callback){
    int ret = recv(socket, cxBuffer, bufferSize);
    if(ret == -1) printf("Recv error, %s\n", sterror(errno));
    callback(cxBuffer, bufferSize);    
}
