# Sistema de Control de Nivel de Agua con PLC

## Descripción del Proyecto 
Este proyecto tiene como objetivo el desarrollo de un **sistema de control de nivel de agua** utilizando un **PLC Phoenix Contact AXC F 2152**, programado con **PLCNext Engineer** y supervisado a través de una **interfaz SCADA en Visu+**.
El sistema permite gestionar el nivel del tanque de forma **local**, directamente desde el PLC y su software de programación, o de manera **remota**, mediante la interfaz SCADA. Además, puede operar en **modo automático**, regulando el caudal para
alcanzar un set-point de altura predefinido, o en **modo manual**, dejando el control del caudal completamente en manos del usuario.

## Estructura del PLC
El PLC utilizado cuenta con varios módulos interconectados mediente **Axioline** y **Profinet**, cada uno con funciones específicas:

- **Módulo A1: Unidad de procesamiento**\
Contiene el procesador y la memoria, ejecuta el programa y almacena variables. Dispone de dos entradas Ethernet para comunicación con otros módulos.
- **Módulo A2: Entradas y salidas digitales**\
Incluye 8 entradas y 8 salidas digitales, conectadas por defecto a interruptores y LEDs indicativos.
- **Módulo A3: Entradas y salidas analógicas**\
Posee dos entradas de tensión, dos de corriente, y dos salidas de tensión y corriente. Se utiliza para el control del nivel de agua y regulación del caudal.
- **Módulo A4: Comunicación Porfinet**\
Permite conectar módulos que no utilizan Axioline, garantizando la comunicación entre el módulo A5 y la unidad central.
- **Módulo A5: Entradas y salidas digitales vía Profinet**\
Funciona ocmo el módulo A2 pero con comunciación Profinet.

## Funcionamiento del Sistema

El control del nivel de agua se realiza mediante un esquema de arranque y parada de motor, con indicadores LED para visualizar el estado del sistema:
- **Modo local y remoto**:
  Se puede alternar mediante un interruptor, activando el control desde el PLC o desde la interfaz SCADA.
- **Modo Automático y manual**:
  Permite que el sistema regule el caudal automáticamente para alcanzar el nivel deseado o que el usuario lo controle manualmente.
- **Alarmas y seguridad**:
  El sistema cuenta con diversas entradas digitales para detectar fallas como cisterna vacía, obstrucción del tubo de llenado o nivel excesivo. Cada falla detiene automáticamente el proceso y se indica mediante un LED de alarma.
  Además, se incluye un sensor de caudal y una salida para habilitar el variador del motor.
- **Entradas y salidas analógicas**:
  Se utilizan para medir el nivel de agua y controlar el caudal de forma precisa.

## Comunicación entre módulos
Los módulos A1, A2 y A3 se conectan mediante **Axioline**, mientras que los módulos A4 y A5 se comunican mediante **Profinet**, utilizando la entrada Ethernet del módulo A1. Esta configuración permite la integración completa
del sistema y la supervisión tanto local como remota.
