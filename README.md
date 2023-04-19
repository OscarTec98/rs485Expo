# RS485 y CAN bus Expo
## POR: OSCAR GARCIA
*Presentación sobre RS-485 y can bus*

##  RS-485 CAN HAT
- colors = ['#7c4dff', '#0091ea', '#ff9100', '#ff1744']

- colors.each do |color|
  .hello{style: "color: #{color}"} RS-485
  
  .hello {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 25vw;
  animation-name: wave;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
  font-family: "Righteous", cursive;
  -webkit-text-stroke-width: 3px;
  -webkit-text-stroke-color: black;
}

@for $i from 1 through 4 {
  .hello:nth-of-type(#{$i}) {
    animation-duration: 2s;
    animation-delay: 0.8s - ($i / 4);
  }
}

@keyframes wave {
  40%,
  50% {
    transform: translate(-50%, -65%) scale(1.05);
  }

  0%,
  90%,
  100% {
    transform: translate(-50%, -45%) scale(0.95);
  }
}
  
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



