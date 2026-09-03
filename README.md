# trabajo-de-robotica-2-
<img width="1283" height="716" alt="image" src="https://github.com/user-attachments/assets/a43e6582-4e53-4e3a-9113-d469992612ec" />

const int LED1 = 4;
const int LED2 = 5;
const int LED3 = 6;
const int LED4 = A1;
const int LED5 = A3;
const int LED6 = A2;
const int LED7 = A0;

const int PUSH = 7;

int RESULTADO = 0;

void setup()
{
pinMode(LED1,OUTPUT);
pinMode(LED2,OUTPUT);
pinMode(LED3,OUTPUT);
pinMode(LED4,OUTPUT);
pinMode(LED5,OUTPUT);
pinMode(LED6,OUTPUT);
pinMode(LED7,OUTPUT);
  
pinMode(PUSH,INPUT_PULLUP);
Serial.begin(9600);   
}

void loop()
{ 
  if(digitalRead(PUSH)==LOW)
  {
  RESULTADO = random(1,7);
  Serial.println(RESULTADO);  
  delay(500);  
  } 
  if (RESULTADO==1)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,LOW);
    digitalWrite(LED4,HIGH);
    digitalWrite(LED5,LOW);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,LOW);
  }
   if (RESULTADO==2)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,HIGH);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,LOW);
  }
   if (RESULTADO==3)
  {
    digitalWrite(LED1,LOW);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,HIGH);
    digitalWrite(LED5,HIGH);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,LOW);
  }
   if (RESULTADO==4)
  {
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,HIGH);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,HIGH);
  }
   if (RESULTADO==5)
  {
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,LOW);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,HIGH);
    digitalWrite(LED5,HIGH);
    digitalWrite(LED6,LOW);
    digitalWrite(LED7,HIGH);
  }
   if (RESULTADO==6)
  {
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,HIGH);
    digitalWrite(LED3,HIGH);
    digitalWrite(LED4,LOW);
    digitalWrite(LED5,HIGH);
    digitalWrite(LED6,HIGH);
    digitalWrite(LED7,HIGH);
  }
}

Este proyecto es un dado electrónico. Al presionar el botón, la placa genera un número aleatorio del 1 al 6 y enciende la combinación correspondiente de LEDs para representar la cara de un dado tradicional.

Descripción del Código
El código genera un valor pseudoaleatorio entre 1 y 6 mediante la función random(1, 7) cada vez que detecta la pulsación del botón en el pin 7. Luego, envía el valor al monitor serie a 9600 baudios y evalúa una serie de estructuras if para encender o apagar los 7 LEDs con el patrón visual exacto de un dado de seis caras (1 punto al centro, 2 en diagonal, etc.).

Componentes Utilizados

1 Placa Arduino Uno R3: Procesa la lógica y genera el número aleatorio.

1 Protoboard: Para montar la matriz de LEDs en disposición de dado y el botón.

7 LEDs azules: Dispuestos en un patrón rectangular con uno en el centro para simular la cara de un dado.

7 Resistencias limitadoras: Protegen a cada uno de los LEDs conectados a las salidas del Arduino.

1 Botón (Push Button): Conectado al pin digital 7 con pull-up interno para lanzar el dado.

Cables de puente (Jumper wires): Conexiones hacia pines digitales (4, 5, 6, 7) y analógicos usados como salidas digitales (A0, A1, A2, A3), además de tierra (GND).

Funcionamiento paso a paso

Configuración (setup): Se declaran los 7 pines de los LEDs como salidas digitales y el pin del botón como entrada con INPUT_PULLUP. Se inicia la comunicación serie.

Lectura del botón: En el ciclo loop, el código verifica si el botón está en estado bajo (LOW), indicando que ha sido presionado.

Generación del número: Se obtiene un valor aleatorio entre 1 y 6, el cual se guarda en la variable RESULTADO y se muestra en la consola. Se incluye un pequeño retardo (delay(500)) para evitar múltiples lecturas accidentales por el rebote del botón.

Mapeo del Dado: Se compara el valor de RESULTADO:

1: Enciende únicamente el LED central (LED4).

2 a 5: Activa combinaciones específicas de LEDs esquineros y/o el centro.

6: Enciende todos los LEDs laterales (6 en total), dejando el central apagado.
