# Práctica 04 - Control de LEDs con Botones

Proyecto desarrollado con el microcontrolador **PIC16F887** utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

En esta práctica se trabajó con el manejo de **entradas y salidas digitales** del microcontrolador PIC16F887. Se utilizaron botones como entradas para controlar salidas conectadas a LEDs y displays de 7 segmentos.

La actividad permitió comprender cómo el microcontrolador puede leer el estado lógico de un botón y responder activando una salida digital.

## Objetivo

Implementar el control de salidas digitales mediante botones, reforzando la configuración de puertos como entrada y salida, el uso de resistencias pull-up y la lectura de estados lógicos en el PIC16F887.

## Componentes Utilizados

- PIC16F887
- Push buttons
- LEDs
- Resistencias
- Displays de 7 segmentos
- Cristal de cuarzo
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C

## Desarrollo de la Actividad

En la primera actividad se conectaron botones a los pines de entrada del microcontrolador y LEDs a los pines de salida. Al presionar un botón, el PIC16F887 detecta el cambio de estado lógico y activa el LED correspondiente.

En la segunda actividad se trabajó con displays de 7 segmentos, utilizando botones para modificar el valor mostrado. Esto permitió aplicar la lectura de entradas digitales en una salida visual más completa.

## Funcionamiento

El programa configura los puertos de entrada para leer botones y los puertos de salida para controlar LEDs o displays. Las entradas trabajan con lógica activa en bajo, por lo que al presionar un botón el estado leído cambia y el microcontrolador actualiza la salida.

En el caso de los LEDs, cada botón controla directamente un LED. En el caso de los displays, el programa utiliza patrones de segmentos para representar números y actualiza el valor mostrado según la interacción con los botones.

## Conceptos Aplicados

- Entradas digitales
- Salidas digitales
- Lectura de botones
- Control de LEDs
- Uso de displays de 7 segmentos
- Resistencias pull-up
- Configuración de registros `TRIS`
- Simulación en Proteus

## Resultado Esperado

Al ejecutar la práctica, los LEDs deben responder al estado de los botones conectados al microcontrolador.

En la actividad con displays, los botones permiten modificar o reiniciar el valor mostrado, comprobando la interacción entre entradas digitales y salidas visuales.

## Evidencias

### Circuito con displays en Proteus

<img src="./Circuito%20proteus%20practica%204.png" width="550">

### Circuito de control con botones

<img src="./Circuito_proteus%20practica%204.1.jpeg" width="550">

## Archivos

| Archivo | Descripción |
|---|---|
| `Circuito proteus practica 4.png` | Evidencia del circuito con displays de 7 segmentos |
| `Circuito_proteus practica 4.1.jpeg` | Evidencia del circuito de control con botones |
| `Micro_practica4.pdsprj` | Proyecto de simulación en Proteus |
| `Practica_4.X.production.hex` | Archivo compilado de la práctica |
| `Practica_4CLASE.X.production.hex` | Archivo compilado de la actividad de clase |

