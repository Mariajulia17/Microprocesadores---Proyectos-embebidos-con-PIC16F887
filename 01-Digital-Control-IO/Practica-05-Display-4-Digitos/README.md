# Práctica 05 - Display de 4 Dígitos

Proyecto desarrollado con el microcontrolador **PIC16F887** utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

En esta práctica se trabajó con el control de displays de 7 segmentos utilizando el microcontrolador **PIC16F887**. Se implementaron diferentes contadores para comprender el uso del multiplexado, la visualización de números y el manejo de interrupciones externas.

Las actividades realizadas fueron un contador de 0 a 9999 con cambio de dirección, un contador de 0 a 99 utilizando 4 displays de 7 segmentos y un contador de 0 a 9 con interrupción externa y LED indicador.

## Objetivo

Comprender el funcionamiento del multiplexado en displays de 7 segmentos, utilizando el PIC16F887 para controlar varios dígitos con menos conexiones. Además, se buscó aplicar interrupciones externas mediante el pin `RB0/INT` para modificar el comportamiento del programa durante la ejecución.

## Componentes Utilizados

- PIC16F887
- Display de 4 dígitos de 7 segmentos
- Display de 7 segmentos
- LED
- Push buttons
- Resistencias
- Cristal de cuarzo
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C

## Desarrollo de la Actividad

### Actividad 1 - Contador 0-9999 con cambio de dirección

En esta actividad se realizó un contador de **0 a 9999** utilizando una pantalla de 4 displays de 7 segmentos y el microcontrolador PIC16F887. El contador puede trabajar en dos modos: conteo ascendente y conteo descendente.

El cambio de dirección se realiza mediante un botón conectado al pin `RB0/INT`. Cada vez que se presiona el botón, se activa una interrupción externa que cambia el valor de la variable de dirección. Si la variable indica modo ascendente, el contador aumenta; si indica modo descendente, el contador disminuye.

Esta actividad integró multiplexado, interrupciones externas, manejo de displays y lógica de control de dirección.

### Actividad Clase 1 - Contador 0-99 con 4 displays de 7 segmentos

En esta actividad se realizó un contador decimal del **0 al 99** utilizando el microcontrolador PIC16F887 y una pantalla formada por 4 displays de 7 segmentos.

Aunque la pantalla cuenta con cuatro displays disponibles, en esta práctica se utilizaron principalmente dos posiciones para mostrar las decenas y las unidades del contador.

El objetivo principal fue comprender el uso del multiplexado en displays de 7 segmentos. A diferencia de conectar un display de forma directa, el multiplexado permite controlar varios displays utilizando el mismo puerto para los segmentos y otro puerto para seleccionar qué display se encuentra activo en cada instante.

Esta práctica permitió reforzar el uso de arreglos, operaciones aritméticas, control de puertos digitales y visualización de números mediante displays de 7 segmentos.

### Actividad Clase 2 - Contador 0-9 con interrupción y LED

En esta actividad se realizó un contador del **0 al 9** utilizando un display de 7 segmentos y el microcontrolador PIC16F887. Además, se incorporó una interrupción externa mediante un botón conectado al pin `RB0/INT`.

Mientras el contador avanza normalmente del 0 al 9, al presionar el botón se ejecuta una rutina de interrupción. Durante esta rutina, el conteo se detiene temporalmente y un LED conectado a `RC0` parpadea de forma intermitente.

Una vez terminada la rutina de interrupción, el programa regresa al ciclo principal y continúa el conteo.

## Funcionamiento

El PIC16F887 utiliza un arreglo de patrones para representar los números del 0 al 9 en los displays de 7 segmentos. Cada patrón activa los segmentos necesarios para formar el dígito correspondiente.

En el caso del display de 4 dígitos, se utiliza multiplexado. Esto significa que el microcontrolador activa un dígito a la vez y envía el valor correspondiente a los segmentos. Al repetir este proceso rápidamente, se percibe que todos los dígitos están encendidos al mismo tiempo.

También se utilizó la interrupción externa `RB0/INT`, la cual permite que el programa responda inmediatamente al presionar un botón, sin depender únicamente del ciclo principal.

## Conceptos Aplicados

- Control de displays de 7 segmentos
- Multiplexado de displays
- Contadores digitales
- Interrupción externa `RB0/INT`
- Manejo de puertos digitales
- Uso de arreglos para patrones de segmentos
- Control de LED mediante interrupción
- Simulación en Proteus

## Resultado Esperado

En la actividad principal, el display de 4 dígitos debe mostrar un conteo de **0 a 9999**, con la posibilidad de cambiar la dirección del conteo mediante un botón.

En la actividad de clase 1, el display debe mostrar un conteo de **0 a 99** usando multiplexado.

En la actividad de clase 2, el display debe contar del **0 al 9** y, al presionar el botón de interrupción, el LED debe parpadear temporalmente antes de continuar con el conteo.

## Evidencias

### Contador 0-9 con interrupción y LED

<img src="./1A9DF10A-0224-487F-8858-94D9EE5D01E4.jpeg" width="550">

### Display de 4 dígitos multiplexado

<img src="./DE12FB81-FBD9-4348-84DA-4F649120B529.jpeg" width="550">

## Archivos

| Archivo | Descripción |
|---|---|
| `.hex` | Archivos compilados de las actividades |
| `.pdsprj` | Proyecto de simulación en Proteus |
| `1A9DF10A-0224-487F-8858-94D9EE5D01E4.jpeg` | Evidencia del contador con interrupción y LED |
| `DE12FB81-FBD9-4348-84DA-4F649120B529.jpeg` | Evidencia del display de 4 dígitos multiplexado |
