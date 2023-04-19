# RS485 y CAN bus Expo
## POR: OSCAR GARCIA
*Presentación sobre RS-485 y can bus*

#  RS-485 CAN HAT
Es un estándar de comunicaciones muy utilizado en aplicaciones de adquisición y control de datos.

  <figure>
  <img src = "https://m.media-amazon.com/images/I/71bvQ4m6yDL._AC_SL1500_.jpg" width = 500 height = 400>
    <figcaption>RS-485 CAN HAT</figcaption>
    </figure>


Una interfaz estándar de la capa física de comunicación, un método de transmisión de señales, el 1er nivel del modelo OSI. Este protocolo fue creado para ampliar las capacidades físicas de la interfaz RS-232. La conexión serie EIA-485 es realizada utilizando un cable de dos o tres hilos: un hilo de datos, un hilo con datos invertidos y, a menudo, un hilo cero (tierra, 0 V). De este modo, los transmisores y los receptores intercambian los datos a través de un cable de par trenzado de hilos rígidos de 22 o 24 AWG.

  <figure>
<img src ="https://www.rhino.mx/wp-content/uploads/2018/03/CARS-1.png" width = 400 height= 400>
    <figcaption>CABLE RS-232</figcaption>
    </figure>

## Su principal función es transportar una señal a través de dos cables
 ➡️ Uno transmite la señal original
 ⬅️ Y el otro transporta la copia inversa
 > ❗ Este método de transmisión ofrece una gran resistencia a las interferencias en modo común.
 > 
 > 🦺 El cable de par trenzado puede ser blindado o no.
#### EJEMPLO DE UNA RED DE COMUNICACIÓN CONSTRUIDA CON LA INTERFAZ RS-485
![](https://www.eltima.com/images/upload/products/spm/articles/rs/wire.jpg)

## Características principales.
☑️ Transmision de datos bidireccional semidúplex.
 - No se puede transmitir y recibir datos al mismo tiempo.

☑️ Canal de comunicación simétrico.
 - Mayor estabilidad de la señal y elimina la radiación electromagnética generada por la señal útil.

☑️ Multipunto.
 - Dependiendo de la información enviada, ninguno o varios nodos de la línea responden al maestro.

## Ventajas
✔️ Intercambio de datos bidireccional a través de un par de hilos trenzados.

✔️ Admite varios tranceptores conectados a la misma línea, es decir, permite crear una red.

✔️ Gran longitud de la línea de comunicación (4000ft)

✔️ Alta velocidad de transmisión

## DATOS EXTRAS
| Protocolo | RS485 |
| --- | --- |
| Tipo de protocolo | Semi-dúplex |
| Tipo de señal | Balanceado |
| Número de dispositivos | Hasta 32 transmisores y 43 receptores |
| Transmisión máxima de datos | 10 Mbps a 15 metros |
| Longitud máxima del cable | Aproximadamente 1220 metros a 100 Kbps |
| Corriente de salida | 250mA |
| Voltaje mínimo de entrada | 0,2V diferencial |

## Aplicaciones.
💻 El uso de señales RS-485 se utilizan en una amplia gama de sistemas informáticos y de automatización.

✈️ Tambien se puede usar para comunicaciones de datos de baja velocidad en cabinas de aviones comerciales ya que requiere de un cableado minimo y puede compartir el cableado entre varios asientos, reduciendo el peso.

🎦 En teatros y salas de espectaculos para controlar la iluminación y otros sistemas como la interconexión de audio digital.

## Comunicación serial entre una Raspberry PI y Arduino Uno utilizando RS-485 

![](https://circuitdigest.com/sites/default/files/projectimage_mic/RS-485-Serial-Communication-between-Raspberry-Pi-and-Arduino-Uno.jpg)

```
Master Raspberry Pi Code:


import time

import serial

import RPi.GPIO as GPIO

from time import sleep


GPIO.setwarnings(False)

GPIO.setmode(GPIO.BOARD)

GPIO.setup(7, GPIO.OUT, initial=GPIO.HIGH)



send = serial.Serial(

    port='/dev/serial0',

    baudrate = 9600,

    parity=serial.PARITY_NONE,

    stopbits=serial.STOPBITS_ONE,

    bytesize=serial.EIGHTBITS,

    timeout=1

)


i = [0,10,45,90,135,180,135,90,45,10,0]


while True:

 for x in i:

     send.write(str(x))

     print(x)

     time.sleep(1.5)


 


Slave Arduino Code:


#include <LiquidCrystal.h>              //Include LCD library for using LCD display functions 

#include <Servo.h>                //For using Servo functions

int enablePin = 2; 


LiquidCrystal lcd(8,9,10,11,12,13);      // Define LCD display pins RS,E,D4,D5,D6,D7


Servo servo;


void setup() 

{

  lcd.begin(16,2);

  lcd.print("CIRCUIT DIGEST");

  lcd.setCursor(0,1);

  lcd.print("RS_485");

  delay(3000);

  lcd.clear();

  Serial.begin(9600);                   // initialize serial at baudrate 9600:

  pinMode(enablePin, OUTPUT);

  delay(10);

  digitalWrite(enablePin, LOW);        //  (Pin 2 always LOW to receive value from Master)

  servo.attach(3);                     //  (Servo PWM pin connected to Pin 3 PWM pin of Arduino)

}


void loop() 


{                                                  

  while (Serial.available())                   //While have data at Serial port this loop executes

     {

                     

        lcd.clear();

        int angle = Serial.parseInt();            //Receive INTEGER value from Master throught RS-485

        servo.write(angle);                       //Write received value to Servo PWM pin (Setting Angle)

        lcd.setCursor(0,0);

        lcd.print("Angle From RPi ");

        lcd.setCursor(0,1);

        lcd.print(angle);                        //Displays the Angle value

        

    }

 }


```
## Resultado
<a href="https://picasion.com/"><img src="https://i.picasion.com/pic92/2c71d48cfaac56fc6e45e5c709eb5a78.gif" width="300" height="200" border="0" alt="https://picasion.com/" /></a><br /><a href="https://picasion.com/">https://picasion.com/</a>

# bus CAN
La Red de Area del Controlador, es un protocolo basado en mensajes diseñado para permitir que las unidades de control electrónico (ECU) de los automóviles actuales, así como otros dispositivos, se comuniquen entre sí de manera confiable y basada en prioridades. Todos los dispositivos reciben mensajes o tramas, por lo que no se requiere de una computadora host.

![](https://m.media-amazon.com/images/I/71GrlmKgF1L._SX522_.jpg)

CAN-Bus compatible para Arduino.

## Funcionamiento.
Los dispositivos en un bus CAN se denominan "nodos". Cada nodo consta de una CPU, un controlador CAN y un transceptor, que adapta los niveles de señal de los datos enviados y recibidos por el nodo. Todos los nodos pueden enviar y recibir datos, pero no al mismo tiempo. Los nodos no pueden enviarse datos directamente entre sí. En cambio, envían sus datos a la red, donde están disponibles para cualquier nodo al que se hayan dirigido. El protocolo CAN no tiene pérdidas y utiliza un método de arbitraje bit a bit para resolver disputas en el bus.

## Ventajas
✔️ Sencillo y de bajo costo

✔️ Totalmente centralizado

✔️ Extremadamente robusto

✔️ Eficiente

✔️ Reduccion de peso

✔️ Implementación sencilla

## Aplicaciones
🚗 Todo tipo de vehículos

✈️ Aviones

🛗 Ascensores

🏭 Plantas de fabricación de todo tipo

⛵ Buques

⚕️ Equipo médico

🔌 Electrodomésticos

# Referencias 
- Weis, O. (2021, 20 octubre). Qué es RS485 - Guía de la Comunicación RS485 [2023]. Electronic Team, Inc. https://www.eltima.com/es/article/rs485-communication-guide/#:~:text=RS-485%20(actualmente%20conocido%20como,de%20la%20interfaz%20RS-232.

- colaboradores de Wikipedia. (2023). TIA-485. Wikipedia, la enciclopedia libre. https://es.wikipedia.org/wiki/TIA-485

- ¿Qué es Can Bus (red de área de controlador)? (2023, 13 febrero). Soluciones de Adquisición de Datos (DAQ). https://dewesoft.com/es/blog/que-es-el-bus-can

- RS-485 Serial Communication between Raspberry Pi and Arduino Uno. (s. f.). https://circuitdigest.com/microcontroller-projects/rs485-serial-communication-between-arduino-and-raspberry-pi?fbclid=IwAR0AJsNSA43W04jWK36vFWS284XMIoJ7dAih1xpjg1udpdke1yK4jyRKlzA
