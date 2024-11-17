---
id: 1731793058-fundamentos-ingenieria-de-software
aliases:
  - Fundamentos Ingeniería de Software
tags: []
---

# Fundamentos Ingeniería de Software

**Bit**: mínima expresión de un dato, tiene dos estados, encendido y apagado, lo conocemos como 0 y 1, en electrónica corresponde a un tipo de transistor que permite o no pasar la corriente

Byte: Ocho unidades de Bit, es posible guardar 256 unidades diferentes en un byte

Assembler: bytes de una CPU asignadas para almacenar instrucciones básicas para procesar todo tipo de datos en su manera más elemental.

CPU: 
  - Unidad Central de Procesamiento
  - Ghz: velocidad de instrucciones procesadas por segundo
  - Core: cantidad de CPUs que pueden trabajar en paralelo
  - Están construidos con silicio
  - Un superconductor solucionaría gran parte de los problemas asociados a la creación de CPUs dado que permiten el movimiento de electricidad sin pérdida, la pérdida de electricidad provoca
  el calentamiento del material
  - Cuándo la CPU recibe la información del SO desde la RAM, comienza a activar todos los periféricos del sistema
  - Para las pantallas, la CPU envía los datos gráficos a la GPU
  - La CPU puede procesar todos los periféricos por sí solo, pero relega trabajo a chips especializados para optimizar la velocidad de procesos complejos

BIOS: Sistema operativo de arranque, le da la señal de inicio a la CPU para comenzar a trabajar. Comienza a funcionar con al primera señal de electricidad recibida
  - BIOS es una marca
  - La bios detecta los componentes de una máquina y comienza a generar las conexiones iniciales para el funcionamiento
    - Envía una orden al disco duro el SO y lo envía a la RAM, la cuál envía la información a la CPU


RAM:
  - Random Access Memory
  - Contiene memoria volátil, que no perdura si no hay corriente, pero es extremadamente rápida de acceder
  - Cuándo abrimos un programa, la información editable se guarda en esta memoria, de forma que es posible acceder a ella de manera rápida, y pasa a guardarse de forma persistente en el HDD o SSD al momento de guardar.
  - Además contiene todos los softwares que estamos utilizando, como el SO, programas abiertos, etc.

HDD:
  - Disco Duro sólido
  - Guarda la información en discos, son lentos ya que los discos deben rotar para que el cabezal lea la información de los diferentes puntos donde fueron guardados.

SSD:
  - Solid State Drive
  - No utiliza discos, si no chip de información que perdura información
  - Viene de los USB
  - Utiliza memorias Flash, chips rápidos que permiten acceder a la información de manera directa

GPU:
  - Unidad de procesamiento Gráfico
  - No es tan rapida como una CPU, pero genera muchos procesos en paralelo
  - Permite en paralelo procesar millones de pixeles al mismo tiempo

Bus de datos:
  - Cables o puentes de conexión entre los componentes
  - La CPU se conecta con la GPU a través de la conexión PCI Express

OS:
  - Sistema operativo
  - Cuándo arranca una computadora, la BIOS envía una instrucción al disco duro para que cargue el SO en la RAM
  - Orden de privilegios:
    - 0. Lo primero que se carga en la RAM es el kernel, que es el núcleo del SO y tiene acceso a todo los datos.
    - 1. Luego carga los Drivers
    - 2. Drivers de aplicaciones
    - 3. Aplicaciones
  - Cuándo una aplicación necesita acceder a algún componente de un anillo de seguridad menor, se deben entregar permisos explícitos
