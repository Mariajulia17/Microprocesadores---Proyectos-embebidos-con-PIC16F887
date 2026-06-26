# Práctica 08 - Sistema de Monitoreo ADC de Dos Canales con LCD

Proyecto embebido desarrollado con el microcontrolador **PIC16F887**, utilizando **MPLAB X IDE**, compilador **XC8** y simulación en **Proteus**.

## Descripción General

Este proyecto implementa un sistema de monitoreo analógico de dos canales utilizando el módulo **ADC** del microcontrolador **PIC16F887**. El sistema permite leer dos señales variables generadas por potenciómetros y visualizar la información en una pantalla **LCD 16x2**.

La aplicación fue diseñada como una interfaz básica de adquisición de datos, donde el usuario puede seleccionar qué entrada analógica desea consultar y en qué formato desea visualizarla: voltaje, porcentaje o valor digital ADC.

## Objetivo del Proyecto

Desarrollar una solución embebida capaz de adquirir, procesar y mostrar señales analógicas provenientes de dos entradas independientes.

El propósito principal fue integrar lectura multicanal ADC, procesamiento numérico, manejo de pantalla LCD y control mediante botones, simulando una interfaz sencilla de monitoreo para variables analógicas.

## Componentes Utilizados

- PIC16F887
- Dos potenciómetros
- Pantalla LCD 16x2
- Push buttons
- Resistencias
- Cristal de cuarzo
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C
- Librería LCD

## Descripción del Funcionamiento

El sistema utiliza dos potenciómetros conectados a entradas analógicas del PIC16F887. Cada potenciómetro genera un voltaje variable dentro del rango de operación del microcontrolador.

El módulo ADC convierte cada señal analógica en un valor digital de 10 bits, dentro del rango de `0` a `1023`. A partir de esa lectura, el programa realiza los cálculos necesarios para representar la información en tres formatos:

- **Voltaje:** valor equivalente aproximado de la señal de entrada.
- **Porcentaje:** relación proporcional respecto al rango máximo de lectura.
- **ADC:** valor digital directo obtenido por el convertidor analógico-digital.

La pantalla LCD 16x2 funciona como interfaz de visualización. A través de botones, el usuario puede cambiar el canal mostrado y el tipo de dato visualizado, permitiendo comparar las dos señales analógicas de forma clara.

## Desarrollo Técnico

El proyecto se estructura alrededor de tres bloques principales:

### Adquisición de Datos

El PIC16F887 lee las señales analógicas mediante su módulo ADC. Para esto se configuran los registros correspondientes y se selecciona el canal analógico que se desea convertir.

### Procesamiento

Después de obtener la lectura ADC, el programa calcula el voltaje equivalente y el porcentaje correspondiente. Estos valores se convierten a texto mediante `sprintf()` para poder mostrarlos correctamente en la LCD.

### Interfaz de Usuario

La LCD 16x2 muestra la información procesada, mientras que los botones permiten cambiar entre canales y modos de visualización. Esto convierte al sistema en una pequeña interfaz de monitoreo interactiva.

## Modos de Visualización

El sistema permite mostrar la información de los potenciómetros en diferentes formatos:

| Modo | Descripción |
|---|---|
| Voltaje | Muestra el voltaje equivalente leído en la entrada analógica |
| Porcentaje | Muestra el porcentaje correspondiente al rango total del ADC |
| ADC | Muestra el valor digital crudo de la conversión ADC |

## Conceptos Aplicados

- Conversión analógica-digital
- Lectura de múltiples canales ADC
- Procesamiento de señales analógicas
- Visualización de datos en LCD 16x2
- Cambio de modo mediante botones
- Manejo de puertos analógicos y digitales
- Formato numérico en lenguaje C
- Simulación de sistemas embebidos en Proteus

## Resultado Esperado

Al ejecutar el sistema, la LCD debe mostrar la lectura correspondiente al potenciómetro seleccionado.

Al mover cualquiera de los potenciómetros, el valor mostrado debe actualizarse de acuerdo con la variación de voltaje. Mediante los botones, el usuario puede cambiar el canal analógico visualizado y alternar entre voltaje, porcentaje o valor ADC.

## Evidencias

### Circuito en Proteus

<img src="./Circuito%20proteus%20practica%208.png" width="550">

## Archivos

| Archivo | Descripción |
|---|---|
| `description.txt` | Descripción breve del proyecto para la tabla principal |
| `Practica_8.X.production.hex` | Archivo compilado para simulación |
| `Micro_practica8.pdsprj` | Proyecto de simulación en Proteus |
| `Circuito proteus practica 8.png` | Evidencia visual del circuito |
| `README.md` | Documentación técnica del proyecto |

## Estado del Proyecto

Proyecto simulado en Proteus, integrando adquisición analógica de dos canales, procesamiento de datos y visualización en LCD 16x2.
