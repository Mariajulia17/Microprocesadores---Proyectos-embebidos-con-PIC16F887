# Detector de Infieles con PIC16F887

## Descripción del proyecto

Este proyecto consiste en un sistema interactivo llamado **Detector de Infieles**, desarrollado con el microcontrolador **PIC16F887**. El sistema funciona como una simulación tipo polígrafo, donde una persona responde una serie de preguntas usando botones de **SI** y **NO**.

Además de las respuestas, el sistema utiliza dos potenciómetros para simular el nivel de **nervios** y **estrés** de la persona. Con estos datos, el programa calcula un porcentaje de culpa y muestra un veredicto final en una pantalla LCD.

El proyecto también utiliza LEDs, un buzzer y un servomotor para representar el resultado de forma visual y sonora.

> Este proyecto es recreativo y didáctico. No detecta una infidelidad real, sino que sirve para demostrar el uso de entradas analógicas, entradas digitales, LCD, PWM, LEDs, buzzer y servomotor con el PIC16F887.

## Objetivo general

Diseñar y programar un sistema con PIC16F887 capaz de mostrar preguntas, recibir respuestas, leer valores analógicos y calcular un resultado final utilizando diferentes dispositivos electrónicos.

## Materiales utilizados

| Componente | Función |
|---|---|
| PIC16F887 | Microcontrolador principal |
| LCD 16x2 | Muestra preguntas, mensajes y resultados |
| 2 potenciómetros | Simulan nervios y estrés |
| 2 botones | Respuestas SI y NO |
| LED verde | Indica resultado inocente |
| LED rojo | Indica resultado culpable |
| Buzzer | Emite sonidos y alarma |
| Servomotor | Indica visualmente el porcentaje de culpa |
| Cristal de 4 MHz | Reloj del microcontrolador |
| Resistencias | Protección y conexiones |
| Fuente de 5V | Alimentación del circuito |

## Conexiones principales

| Elemento | Pin del PIC16F887 | Descripción |
|---|---|---|
| Potenciómetro de nervios | RA0 / AN0 | Entrada analógica |
| Potenciómetro de estrés | RA1 / AN1 | Entrada analógica |
| Botón SI | RB3 | Entrada digital |
| Botón NO | RB1 | Entrada digital |
| LED verde | RD0 | Salida digital |
| LED rojo | RD1 | Salida digital |
| Buzzer | RD2 | Salida digital |
| Servomotor | RC1 / CCP2 | Salida PWM |
| LCD 16x2 | Puerto C | Pantalla de texto |

## Funcionamiento general

Al iniciar la simulación, la pantalla LCD muestra el título del proyecto:

```text
DETECTOR DE
INFIELES
```

Después, el sistema muestra una instrucción para que el usuario responda usando los botones de **SI** y **NO**.

El programa realiza cinco preguntas. En cada pregunta se toman en cuenta tres factores principales:

- La respuesta seleccionada.
- El nivel de nervios del potenciómetro en RA0.
- El nivel de estrés del potenciómetro en RA1.
- El tiempo que tarda la persona en responder.

Con estos datos, el programa calcula una culpa parcial. Al final, obtiene el promedio de las cinco preguntas y muestra un veredicto.

## Preguntas utilizadas

El programa muestra preguntas en la pantalla LCD 16x2. Como la pantalla tiene dos líneas, cada pregunta está dividida en dos partes.

Ejemplo:

```text
Saliste anoche?
[SI]      [NO]
```

Otro ejemplo:

```text
Coqueteaste con
alguien?[SI][NO]
```

Después de cada pregunta, el usuario debe presionar el botón correspondiente.

## Lectura de potenciómetros

Los potenciómetros están conectados a RA0 y RA1. Estos pines funcionan como entradas analógicas.

El PIC16F887 convierte el voltaje de los potenciómetros en un valor digital de 0 a 1023 usando el ADC.

En el código, el ADC se configura así:

```c
ANSEL  = 0x03;
ANSELH = 0x00;
ADCON0 = 0x81;
ADCON1 = 0x80;
```

Después, el valor leído se convierte a porcentaje:

```c
p_nervio = (nervio * 100) / 1023;
p_estres = (estres * 100) / 1023;
```

Esto significa que:

| Valor ADC | Porcentaje |
|---:|---:|
| 0 | 0% |
| 512 | 50% |
| 1023 | 100% |

Mientras más alto estén los potenciómetros, mayor será el porcentaje de culpa.

## Lectura de botones

El sistema tiene dos botones:

| Botón | Pin |
|---|---|
| SI | RB3 |
| NO | RB1 |

Los botones utilizan resistencias pull-up internas. Esto significa que normalmente leen `1`, y cuando se presionan leen `0`.

En el código se activan así:

```c
OPTION_REG &= 0x7F;
WPUBbits.WPUB3 = 1;
WPUBbits.WPUB1 = 1;
```

La función `Esperar_Respuesta()` espera a que el usuario presione un botón. También usa un pequeño retardo para evitar errores por rebote del botón.

## Tiempo de respuesta

El programa también mide cuánto tarda la persona en contestar.

Si responde rápido, no se agrega mucha culpa.  
Si tarda más tiempo, se agrega más culpa.  
Si no responde, se asigna culpa máxima.

| Tiempo de respuesta | Efecto |
|---|---|
| Respuesta rápida | Baja culpa |
| Respuesta media | Culpa moderada |
| Respuesta lenta | Culpa alta |
| Sin respuesta | Culpa máxima |

Esta parte hace que el sistema parezca más parecido a un polígrafo.

## Cálculo de culpa

Para calcular la culpa de cada pregunta, primero se promedian los valores de nervios y estrés:

```c
culpa_pregunta = (p_nervio + p_estres) / 2;
```

Después se suma una cantidad dependiendo de la respuesta:

```c
if(respuesta == 1)
{
    culpa_pregunta += 15;
}

if(respuesta == 0)
{
    culpa_pregunta += 5;
}
```

También se agrega una penalización por tardanza:

```c
culpa_pregunta += (p_tardanza / 4);
```

Si la persona no responde, se asigna culpa máxima:

```c
if(respuesta == 2)
{
    culpa_pregunta = 100;
}
```

Finalmente, si el valor supera 100%, se limita a 100%:

```c
if(culpa_pregunta > 100)
{
    culpa_pregunta = 100;
}
```

## Servomotor

El servomotor se usa como indicador visual del nivel de culpa. Se controla con PWM usando el módulo CCP2 del PIC16F887.

Los valores definidos son:

```c
#define SERVO_0   31
#define SERVO_180 156
```

La culpa se convierte a un ángulo de 0° a 180°:

```c
angulo = ((culpa_total / (i + 1)) * 180) / 100;
```

Relación aproximada:

| Culpa | Ángulo del servo |
|---:|---:|
| 0% | 0° |
| 25% | 45° |
| 50% | 90° |
| 75% | 135° |
| 100% | 180° |

Mientras mayor sea la culpa, más se mueve el servo.

## LEDs

El proyecto utiliza dos LEDs:

| LED | Pin | Función |
|---|---|---|
| Verde | RD0 | Inocente |
| Rojo | RD1 | Culpable |

Dependiendo del resultado final, se encienden de diferente manera.

| Resultado | LED verde | LED rojo |
|---|---|---|
| Inocente | Encendido | Apagado |
| Sospechoso | Encendido | Encendido |
| Casi culpable | Apagado | Encendido |
| Culpable | Apagado | Encendido |

## Buzzer

El buzzer está conectado al pin RD2. Se utiliza para hacer sonidos durante el programa.

El buzzer se activa en diferentes momentos:

- Al iniciar el sistema.
- Al cambiar de pregunta.
- Al mostrar el veredicto.
- Como alarma final si el resultado es culpable.

La función principal del tono enciende y apaga rápidamente el buzzer:

```c
BUZZER = 1;
__delay_us(500);
BUZZER = 0;
__delay_us(500);
```

## Veredicto final

Después de las cinco preguntas, el programa calcula el promedio final:

```c
culpa_final = culpa_total / 5;
```

Con ese resultado se obtiene el veredicto:

| Porcentaje final | Resultado |
|---:|---|
| 0% a 25% | Inocente |
| 26% a 50% | Sospechoso |
| 51% a 75% | Casi culpable |
| 76% a 100% | Culpable |

Mensajes que puede mostrar la LCD:

```text
** INOCENTE **
Te perdono...
```

```text
SOSPECHOSO...
Ojo avizor...
```

```text
CASI CASI...
Explicate!!!
```

```text
** CULPABLE!!! *
ALARMA DE INFIEL
```

## Funcionamiento en Proteus

En Proteus se simula el circuito completo con el PIC16F887, LCD, botones, potenciómetros, LEDs, buzzer y servomotor.

Para que funcione correctamente, se debe cargar el archivo `.hex` generado en MPLAB dentro del PIC16F887. También se debe configurar el PIC con un reloj de 4 MHz, ya que el código usa:

```c
#define _XTAL_FREQ 4000000
```

Al iniciar la simulación, la LCD muestra el título del proyecto. Después aparecen las preguntas y el usuario debe contestar con los botones.

Los potenciómetros se pueden mover durante la simulación para cambiar el nivel de nervios y estrés.

## Pruebas recomendadas

### Prueba 1: Resultado inocente

Condiciones:

- Potenciómetros bajos.
- Respuestas rápidas.
- Responder principalmente NO.

Resultado esperado:

- Culpa baja.
- LED verde encendido.
- Servo cerca de 0°.
- Mensaje de inocente.

### Prueba 2: Resultado sospechoso

Condiciones:

- Potenciómetros en valores medios.
- Algunas respuestas lentas.
- Respuestas mezcladas.

Resultado esperado:

- Culpa media.
- LED verde y rojo encendidos.
- Servo cerca de 90°.
- Mensaje de sospechoso.

### Prueba 3: Resultado culpable

Condiciones:

- Potenciómetros altos.
- Respuestas lentas.
- Responder SI en varias preguntas.

Resultado esperado:

- Culpa alta.
- LED rojo encendido.
- Servo cerca de 180°.
- Buzzer con alarma final.
- Mensaje de culpable.

### Prueba 4: Sin respuesta

Condiciones:

- No presionar ningún botón durante una pregunta.

Resultado esperado:

- La LCD muestra “Sin respuesta”.
- Se asigna culpa máxima.
- Aumenta el porcentaje final.

## Explicación de funciones principales

| Función | Descripción |
|---|---|
| `Botones_Init()` | Configura los botones y activa pull-ups internos |
| `ADC_Init()` | Configura RA0 y RA1 como entradas analógicas |
| `ADC_Read()` | Lee el valor de un canal ADC |
| `PWM2_Init()` | Configura el PWM para el servomotor |
| `Servo_SetAngle()` | Convierte grados a señal PWM |
| `Buzzer_Tono()` | Genera un tono en el buzzer |
| `Buzzer_Beep()` | Genera varios sonidos cortos |
| `Buzzer_AlarmaFinal()` | Activa la alarma final |
| `LED_Inocente()` | Enciende el LED verde |
| `LED_Culpable()` | Enciende el LED rojo |
| `LED_Sospechoso()` | Enciende ambos LEDs |
| `Esperar_Respuesta()` | Espera la respuesta del usuario |
| `Culpa_Tardanza()` | Calcula culpa según el tiempo de respuesta |
| `main()` | Controla todo el programa |

## Flujo del programa

1. Se inicializan LCD, ADC, botones, PWM, LEDs y buzzer.
2. Se muestra el mensaje de bienvenida.
3. Se muestran las instrucciones.
4. Se inicia el ciclo de cinco preguntas.
5. Se leen los potenciómetros.
6. Se espera la respuesta del usuario.
7. Se calcula la culpa parcial.
8. Se mueve el servo según la culpa acumulada.
9. Se muestra la culpa parcial en la LCD.
10. Al final se calcula la culpa promedio.
11. Se muestra el veredicto.
12. Se activan LEDs, buzzer y servo según el resultado.

## Conclusión

Este proyecto permitió aplicar varios temas importantes de microcontroladores en una sola práctica. Se utilizó el ADC para leer potenciómetros, entradas digitales para leer botones, una pantalla LCD para mostrar información, PWM para controlar un servomotor, LEDs como indicadores visuales y un buzzer como indicador sonoro.

Aunque el sistema tiene una temática divertida, el proyecto demuestra cómo el PIC16F887 puede recibir información, procesarla mediante programación y controlar diferentes salidas electrónicas.

El Detector de Infieles funciona como una simulación interactiva tipo polígrafo, donde los potenciómetros representan nervios y estrés, los botones registran respuestas, y el programa calcula un porcentaje de culpa para mostrar un veredicto final.
