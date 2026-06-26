# Práctica 02 - Matriz LED 8x8

Proyecto desarrollado con el microcontrolador **PIC16F887** utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

En esta práctica se trabajó con el control de una **matriz LED 8x8** utilizando el microcontrolador **PIC16F887**. La actividad principal consistió en mostrar una figura en forma de **X** dentro de la matriz, y posteriormente realizar una actividad adicional donde se mostraron letras personalizadas.

Para la actividad libre se diseñaron y programaron las letras **M, J, A y G**, utilizando arreglos binarios para representar el patrón de encendido de cada fila de la matriz.

## Objetivo

Comprender el funcionamiento de una matriz LED 8x8 mediante el uso de salidas digitales y técnica de multiplexación, aplicando patrones binarios para formar figuras y letras.

## Componentes Utilizados

- PIC16F887
- Matriz LED 8x8
- Resistencias
- Cristal de cuarzo
- Push button para reset
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C

## Desarrollo de la Actividad

Primero se configuraron los puertos del microcontrolador para controlar las filas y columnas de la matriz LED. En esta práctica, el **PORTB** se utilizó para activar las filas y el **PORTD** para controlar las columnas.

En la primera parte se programó un patrón fijo para formar una **X** en la matriz. Después, en la actividad adicional, se crearon arreglos de 8 posiciones para representar letras. Cada posición del arreglo corresponde a una fila de la matriz, y cada bit indica si un LED de esa fila debe encenderse o apagarse.

## Funcionamiento

La matriz LED se controla mediante **multiplexación**, activando una fila a la vez y enviando el patrón correspondiente a las columnas. Este proceso se repite rápidamente para que el ojo humano perciba la imagen completa.

Para mostrar las letras **M, J, A y G**, el programa llama a una función que mantiene cada letra visible durante un tiempo determinado. Después se apaga brevemente la matriz antes de mostrar la siguiente letra.

## Conceptos Aplicados

- Control de matriz LED 8x8
- Multiplexación
- Manejo de filas y columnas
- Uso de arreglos binarios
- Configuración de puertos digitales
- Generación de patrones visuales
- Simulación en Proteus

## Resultado Esperado

Al ejecutar la primera actividad, la matriz LED debe mostrar una figura en forma de **X**.

En la actividad adicional, la matriz debe mostrar secuencialmente las letras **M, A, J y G**, con una pequeña pausa entre cada una.

## Evidencias

### Circuito en Proteus

![Circuito de la matriz](./Circuito%20de%20la%20matriz.jpg)

### Matriz mostrando la letra M

![Matriz en M](./Matriz%20en%20M.jpg)

### Matriz mostrando la letra A

![Matriz en A](./Matriz%20en%20A.jpg)

### Matriz mostrando la X

![Matriz en X](./Matriz%20en%20X.jpg)

## Archivos

| Archivo | Descripción |
|---|---|
| `description.txt` | Descripción corta para la tabla principal |
| `Practica2_micro.pdsprj` | Proyecto de simulación en Proteus |
| `Circuito de la matriz.jpg` | Evidencia del circuito de la matriz LED |
| `Matriz en X.jpg` | Evidencia de la figura X en la matriz |
| `Matriz en M.jpg` | Evidencia de la letra M |
| `Matriz en A.jpg` | Evidencia de la letra A |
| `.hex` | Archivo compilado para cargar en Proteus |

## Estado

Práctica simulada en Proteus.
