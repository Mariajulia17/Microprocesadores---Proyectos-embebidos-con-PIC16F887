# Práctica 09 - Temporización con Timer0 y Monitoreo de Voltaje

Proyecto embebido desarrollado con el microcontrolador **PIC16F887**, utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

Este proyecto implementa un sistema de temporización y monitoreo analógico utilizando periféricos internos del microcontrolador **PIC16F887**. La aplicación integra el módulo **Timer0** para llevar un conteo de tiempo y el módulo **ADC** para adquirir una señal analógica generada por un potenciómetro.

La información procesada se muestra en una pantalla **LCD 16x2**, permitiendo visualizar el tiempo transcurrido y el voltaje medido en tiempo real. Este diseño representa una base funcional para sistemas embebidos que requieren medición de tiempo, adquisición de datos y visualización local.

## Objetivo del Proyecto

Desarrollar una aplicación embebida capaz de medir tiempo transcurrido mediante el temporizador interno Timer0 y combinarlo con la lectura de una señal analógica.

El objetivo principal fue integrar temporización, conversión analógica-digital y visualización en LCD dentro de un mismo sistema, reforzando el uso coordinado de periféricos internos del PIC16F887.

## Componentes Utilizados

- PIC16F887
- Pantalla LCD 16x2
- Potenciómetro
- Cristal de cuarzo
- Resistencias
- Push button de reset
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C
- Librería LCD

## Descripción del Funcionamiento

El sistema utiliza el **Timer0** del PIC16F887 como base de tiempo. Mediante la configuración del temporizador y el uso de interrupciones o conteos internos, el programa lleva el registro de los segundos y minutos transcurridos desde que el circuito inicia su operación.

De forma paralela, el microcontrolador lee el voltaje generado por un potenciómetro conectado a una entrada analógica. Esta señal es convertida por el módulo **ADC** de 10 bits, obteniendo un valor digital dentro del rango de `0` a `1023`.

Posteriormente, el programa convierte esta lectura en un valor de voltaje aproximado y lo muestra en la LCD junto con el tiempo transcurrido.

## Desarrollo Técnico

### Conteo de tiempo con Timer0

Se implementó un sistema de cronometraje utilizando el módulo Timer0 del PIC16F887. El sistema permite llevar la cuenta de segundos y minutos desde el arranque del circuito.

La LCD muestra el tiempo en ejecución, permitiendo observar cómo el temporizador interno puede utilizarse como base para aplicaciones de medición de tiempo.

### Conteo de tiempo y monitoreo de voltaje

El sistema fue ampliado con la lectura de un potenciómetro mediante el ADC del microcontrolador. Además del tiempo transcurrido, la pantalla LCD muestra el voltaje generado por el potenciómetro.

Al variar la posición del potenciómetro, el valor mostrado en la LCD cambia en tiempo real, demostrando la integración entre temporización y adquisición de datos analógicos.

## Conceptos Aplicados

- Configuración de Timer0
- Temporización en sistemas embebidos
- Conteo de segundos y minutos
- Lectura analógica mediante ADC
- Conversión de lectura ADC a voltaje
- Visualización de datos en LCD 16x2
- Manejo de periféricos internos del PIC16F887
- Simulación de sistemas embebidos en Proteus

## Resultado Esperado

Al iniciar el sistema, la LCD debe mostrar el conteo de tiempo transcurrido en segundos y minutos.

En la versión con monitoreo de voltaje, la pantalla también debe mostrar el valor de voltaje leído desde el potenciómetro. Al modificar la posición del potenciómetro, el voltaje desplegado debe actualizarse en tiempo real mientras el conteo continúa funcionando.

## Evidencias

### Circuito en Proteus

<img src="./Circuito%20proteus%20practica%209.png" width="550">

## Archivos

| Archivo | Descripción |
|---|---|
| `Practica_9.X.production.hex` | Archivo compilado de la práctica principal |
| `Actividad_9.X.production.hex` | Archivo compilado de la actividad con monitoreo de voltaje |
| `Circuito proteus practica 9.png` | Evidencia visual del circuito en Proteus |
| `README.md` | Documentación técnica del proyecto |

## Estado del Proyecto

Proyecto simulado en Proteus, integrando temporización con Timer0, lectura ADC de voltaje analógico y visualización de datos en LCD 16x2.
