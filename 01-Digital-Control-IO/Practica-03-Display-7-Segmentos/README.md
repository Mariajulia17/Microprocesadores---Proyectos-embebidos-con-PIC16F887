# Práctica 03 - Display de 7 Segmentos

Proyecto desarrollado con el microcontrolador **PIC16F887** utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

En esta práctica se trabajó con el control de un **display de 7 segmentos** mediante salidas digitales del microcontrolador **PIC16F887**. Se realizaron dos actividades principales: un contador decimal y un contador hexadecimal.

El objetivo fue comprender cómo se activan los segmentos del display para formar números y letras, utilizando patrones binarios enviados desde el microcontrolador.

## Objetivo

Implementar contadores visuales en un display de 7 segmentos, reforzando el manejo de puertos digitales, la configuración de salidas y la relación entre patrones binarios y representación numérica.

## Componentes Utilizados

- PIC16F887
- Display de 7 segmentos
- Resistencias
- Cristal de cuarzo
- Push button para reset
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C

## Desarrollo de la Actividad

### Contador decimal

Se implementó un contador cíclico que muestra los números del **0 al 9** en el display de 7 segmentos. Una vez alcanzado el valor máximo, la secuencia regresa al cero y continúa repitiéndose de manera indefinida.

Este ejercicio permitió comprender la relación entre los segmentos del display y los patrones necesarios para representar cada dígito decimal.

### Contador hexadecimal

Se desarrolló un contador hexadecimal capaz de mostrar los valores del **0 al 9** y las letras **A a F** en el display de 7 segmentos. Al finalizar la secuencia, el contador regresa al valor inicial y continúa su ejecución de forma cíclica.

Esta actividad permitió ampliar el uso del display para representar sistemas numéricos distintos al decimal mediante patrones específicos de activación de segmentos.

## Funcionamiento

El PIC16F887 envía combinaciones binarias al puerto conectado al display de 7 segmentos. Cada bit controla un segmento diferente, por lo que al modificar el valor enviado al puerto se forma un número o una letra.

Para el contador decimal se utilizan patrones correspondientes a los números del **0 al 9**. Para el contador hexadecimal se agregan también los patrones de las letras **A, b, C, d, E y F**.

El programa utiliza retardos para que cada valor permanezca visible durante un tiempo antes de avanzar al siguiente número de la secuencia.

## Conceptos Aplicados

- Configuración de puertos digitales
- Control de display de 7 segmentos
- Representación decimal
- Representación hexadecimal
- Patrones binarios
- Uso de retardos
- Simulación en Proteus

## Resultado Esperado

Al ejecutar el contador decimal, el display debe mostrar los números del **0 al 9** de forma continua.

Al ejecutar el contador hexadecimal, el display debe mostrar la secuencia completa de **0 a F**, regresando al inicio al finalizar.

## Evidencias

### Circuito en Proteus

<img src="./Display%20de%207%20segmentos.jpg" width="500">

## Archivos

| Archivo | Descripción |
|---|---|
| `Contador09.X.production.hex` | Archivo compilado del contador decimal |
| `Contador0F.X.production.hex` | Archivo compilado del contador hexadecimal |
| `Display de 7 segmentos.jpg` | Evidencia del circuito en Proteus |
| `Practica3_micro.pdsprj` | Proyecto de simulación en Proteus |
