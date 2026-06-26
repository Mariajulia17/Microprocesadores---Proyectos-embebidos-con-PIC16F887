# Microprocesadores — Proyectos embebidos con PIC16F887

Repositorio de proyectos de sistemas embebidos desarrollados con el microcontrolador **PIC16F887**, utilizando **MPLAB X IDE**, lenguaje **C** y simulaciones en **Proteus**.

Este repositorio documenta implementaciones prácticas de hardware y software enfocadas en control digital, manejo de displays, multiplexación, periféricos, timers y actuadores. Cada proyecto integra programación en C, diseño de circuito, simulación electrónica y pruebas de funcionamiento.

---

## Herramientas utilizadas

- PIC16F887
- MPLAB X IDE
- XC8 Compiler
- Proteus Design Suite
- Lenguaje C
- Circuitos digitales
- Simulación electrónica
- Implementación física en protoboard

---

## Proyectos

### Digital Control & I/O

Proyectos enfocados en el control de entradas y salidas digitales del microcontrolador.  
En esta sección se implementan secuencias con LEDs, contadores binarios, matrices LED y displays de 7 segmentos.

<!-- DIGITAL_PROJECTS_START -->
| Proyecto | Descripción | Enlace |
|---|---|---|
| Práctica 01 - Salidas Digitales | Manejo de salidas digitales mediante parpadeo de 4 LEDs, contador binario de 6 bits y secuencia tipo caminata de 8 bits. | [Ver proyecto](./01-Digital-Control-IO/Practica-01-Salidas-Digitales/) |
| Práctica 02 - Matriz LED 8x8 | Control de una matriz LED 8x8 mediante multiplexación, mostrando diferentes letras programadas desde MPLAB. | [Ver proyecto](./01-Digital-Control-IO/Practica-02-Matriz-LED-8x8/) |
| Práctica 03 - Display 7 Segmentos | Implementación de un contador decimal de 0 a 9 y un contador hexadecimal en display de 7 segmentos, ambos con función de reset. | [Ver proyecto](./01-Digital-Control-IO/Practica-03-Display-7-Segmentos/) |
| Práctica 04 - Control LEDs Con Botones | Uso de botones como entradas digitales en el PIC16F887 para controlar LEDs y un contador de 0 a 99 en displays de 7 segmentos. | [Ver proyecto](./01-Digital-Control-IO/Practica-04-Control-LEDs-con-Botones/) |
| Práctica 05 - Display 4 Digitos | Control de un display de 7 segmentos de 4 dígitos con el PIC16F887, utilizando salidas digitales y multiplexación para mostrar valores numéricos. | [Ver proyecto](./01-Digital-Control-IO/Practica-05-Display-4-Digitos/) |
| Práctica 14 - Servomotores Pwm Y Automaticopractica 14 Servomotores | Proyecto embebido desarrollado con PIC16F887, MPLAB X IDE y Proteus. | [Ver proyecto](./01-Digital-Control-IO/Practica-14-Servomotores-PWM-y-AutomaticoPractica-14-Servomotores/) |
<!-- DIGITAL_PROJECTS_END -->

---

### Peripherals & Timing Systems

Proyectos orientados al uso de periféricos y temporizadores del microcontrolador.  
Esta sección estará enfocada en el manejo de señales temporizadas, interrupciones, displays LCD, entradas analógicas y otros módulos de comunicación o control.

<!-- PERIPHERALS_PROJECTS_START -->
| Proyecto | Descripción | Enlace |
|---|---|---|
| Práctica 06 - Lcd 16X2 | Control de una pantalla LCD 16x2 con el PIC16F887, utilizando salidas digitales para mostrar información y reforzar el manejo de periféricos. | [Ver proyecto](./02-Peripherals-Timing-Systems/Practica-06-LCD-16x2/) |
| Práctica 07 - Lcd Con Entrada Analogica | Lectura ADC de un potenciómetro con el PIC16F887, mostrando en LCD 16x2 el valor como voltaje o porcentaje mediante un botón de cambio de modo. | [Ver proyecto](./02-Peripherals-Timing-Systems/Practica-07-LCD-con-Entrada-Analogica/) |
| Práctica 08 - Dos Voltajes En Lcd | Lectura de dos voltajes analógicos con el PIC16F887 mediante ADC, mostrando en LCD 16x2 el voltaje 1 o voltaje 2 según el botón presionado. | [Ver proyecto](./02-Peripherals-Timing-Systems/Practica-08-Dos-Voltajes-en-LCD/) |
| Práctica 09 - Timer0 Y Monitoreo De Voltaje | Monitoreo de voltaje analógico con el PIC16F887 mediante ADC, mostrando el valor en LCD 16x2 y utilizando Timer0 para temporización. | [Ver proyecto](./02-Peripherals-Timing-Systems/Practica-09-Timer0-y-Monitoreo-de-Voltaje/) |
| Proyecto 01 Videojuego Lcd Con Joystick | Videojuego en LCD 16x2 con el PIC16F887, utilizando potenciómetros como joystick simulado para controlar el movimiento mediante entradas analógicas. | [Ver proyecto](./02-Peripherals-Timing-Systems/Proyecto-01-Videojuego-LCD-con-Joystick/) |
<!-- PERIPHERALS_PROJECTS_END -->

---

### Actuator Control Systems

Proyectos enfocados en el control de actuadores físicos mediante señales generadas por el microcontrolador.  
Esta sección incluirá aplicaciones con motores DC, servomotores, puentes H y sistemas que respondan a señales de entrada.

<!-- ACTUATOR_PROJECTS_START -->
| Proyecto | Descripción | Enlace |
|---|---|---|
| Próximamente | Proyecto pendiente por agregar. | Próximamente |
<!-- ACTUATOR_PROJECTS_END -->

---

proyectos conforme se implementen nuevas funciones, periféricos y aplicaciones con actuadores.
