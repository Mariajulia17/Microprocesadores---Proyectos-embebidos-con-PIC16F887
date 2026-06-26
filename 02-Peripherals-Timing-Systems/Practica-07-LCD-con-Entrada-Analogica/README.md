# Práctica 07 - Lectura ADC con LCD y Botón

Proyecto desarrollado con el microcontrolador **PIC16F887**, utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

Este proyecto implementa la lectura analógica de un potenciómetro mediante el módulo **ADC** del microcontrolador **PIC16F887**. El valor obtenido se procesa y se muestra en una pantalla **LCD 16x2**, permitiendo visualizar la información en diferentes formatos.

El sistema integra una entrada analógica, una interfaz LCD y un botón de control para cambiar el modo de visualización. Con esto, el usuario puede consultar el valor leído como voltaje o como porcentaje de voltaje, dependiendo del estado seleccionado con el botón.

## Objetivo

Desarrollar un sistema de monitoreo analógico utilizando el PIC16F887, capaz de convertir una señal variable de voltaje en información legible para el usuario mediante una pantalla LCD.

El objetivo principal fue aplicar el módulo ADC del microcontrolador y combinarlo con una interfaz visual para representar datos físicos de forma clara.

## Componentes Utilizados

- PIC16F887
- Potenciómetro
- Pantalla LCD 16x2
- Push button
- Resistencias
- Cristal de cuarzo
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C
- Librería LCD

## Desarrollo del Proyecto

El circuito utiliza un potenciómetro conectado al canal analógico `AN0` del PIC16F887. Al variar la posición del potenciómetro, cambia el voltaje aplicado a la entrada analógica.

El microcontrolador realiza la conversión analógica-digital mediante el ADC de 10 bits, obteniendo valores entre `0` y `1023`. Posteriormente, el programa procesa esa lectura para mostrarla en la LCD como:

- Voltaje equivalente
- Porcentaje del rango total
- Valor digital ADC

El botón conectado a `RB0` permite cambiar entre los modos de visualización. Para evitar lecturas falsas, se implementó una lógica básica de antirrebote y espera a que el botón sea liberado.

## Funcionamiento

La pantalla LCD se controla en modo de 4 bits utilizando el **PORTC** del microcontrolador. El potenciómetro entrega una señal analógica al pin `RA0/AN0`, mientras que el botón de cambio de modo se conecta a `RB0`.

El programa inicia configurando el ADC, los puertos digitales y la LCD. Después entra en un ciclo continuo donde lee el valor del potenciómetro, detecta si el botón fue presionado y actualiza el contenido mostrado en pantalla.

Cuando el sistema se encuentra en modo voltaje, la lectura ADC se convierte a un valor aproximado entre 0 V y 5 V. En modo porcentaje, el valor se escala de 0% a 100%. En modo ADC, se muestra directamente la lectura digital de 10 bits.

## Conceptos Aplicados

- Conversión analógica-digital
- Lectura de potenciómetro
- Manejo del módulo ADC del PIC16F887
- Visualización de datos en LCD 16x2
- Cambio de modo mediante botón
- Antirrebote por software
- Formato numérico con `sprintf`
- Configuración de puertos analógicos y digitales
- Simulación en Proteus

## Resultado Esperado

Al ejecutar el proyecto, la LCD debe mostrar el valor leído del potenciómetro. Al mover el potenciómetro, el valor mostrado debe cambiar en tiempo real.

Cada vez que se presiona el botón, el sistema cambia el modo de visualización entre voltaje, porcentaje y valor digital ADC.

## Evidencias

### Circuito en Proteus

<img src="./Circuito%20proteus%20practica%207.png" width="550">

## Archivos

| Archivo | Descripción |
|---|---|
| `Practica_7.X.production.hex` | Archivo compilado de la práctica principal |
| `Actividad_7.X.production.hex` | Archivo compilado de la actividad con cambio de modo |
| `Practica7_micro.pdsprj` | Proyecto de simulación en Proteus |
| `Circuito proteus practica 7.png` | Evidencia del circuito en Proteus |

