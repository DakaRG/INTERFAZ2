# INTERFAZ2
##### Ejercicio n°1 Arduino: "Hola, Mundo"

```js
void setup() {
  Serial.begin(9600); // Inicia la comunicación serie a 9600 bps
  Serial.println("Hola, Mundo!"); // Envía "Hola, Mundo!" al monitor serie
}

void loop() {
  // No es necesario poner nada en el loop para este ejemplo
}
```

##### Ejercicio n°2 arduino: LED intermitente (Blink)
```
void setup() {  // Configuración inicial (ej: pines como entrada/salida)
  pinMode(13, OUTPUT);  // Pin 13 como salida
  pinMode(8, OUTPUT);
}

void loop() {   // Se repite infinitamente
  digitalWrite(13, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(13, LOW);   // Apagar LED
  //delay(1000);             // Esperar 1 segundo
  digitalWrite(8, HIGH);  // Encender LED
  delay(1000);             // Esperar 1 segundo
  digitalWrite(8, LOW);   // Apagar LED
  //delay(1000);             // Esperar 1 segundo
}
```
<img src="https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ledparpadeante.png" width=1024 height=550/>
<img src="https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej2.2.jpg" width=1024 height=800/>
<img src="https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej2.jpg" width=1024 height=800/>


##### Ejercicio n°3 Arduino: Control por pulsador
Objetivo: Encender un LED solo al presionar un botón. Circuito: Pulsador en pin 2 (con resistencia pull-down de 10k Ω). LED en pin 13.
```
void setup() {
  pinMode(2, INPUT);  // Botón como entrada
  pinMode(13, OUTPUT);
}
void loop() {
  if (digitalRead(2) == HIGH) {  // Si se presiona el botón
    digitalWrite(13, HIGH);
  } else {
    digitalWrite(13, LOW);
  }
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ledpulsador.png" width=1024 height=550 />


##### Ejercicio n°4: LED con potenciometro
Objetivo: Regular brillo de un LED con un potenciómetro. Circuito: Potenciómetro: Patas extremas a +5V y GND, central a pin A0. LED en pin 9 (con resistencia 220 Ω).
```
void setup() {
  pinMode(9, OUTPUT);  // Pin PWM (símbolo ~)
}
void loop() {
  int valor = analogRead(A0);           // Leer potenciómetro (0-1023)
  int brillo = map(valor, 0, 1023, 0, 255);  // Convertir a rango PWM
  analogWrite(9, brillo);               // Ajustar brillo
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/potenciometro.png" width=1024 height=550 />
<img src="https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej4.jpg" />

##### Ejercicio n°5: Semáforo
```
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(2000); // 2 segundos
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/semaforo.png" width= 1024 height= 550 />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej5.jpg" />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej5.1.jpg" width= 1024 height= 800 />

##### EJERCICIO 5.1 SEMAFORO PARPADEANTE
```
// C++ code - Semáforo Autos y Peatones

// Definición de pines
int LED_1 = 6;  // Luz roja autos
int LED_2 = 7;  // Luz amarilla autos
int LED_3 = 8;  // Luz verde autos
int LED_4 = 9;  // Luz verde peatones
int LED_5 = 10; // Luz roja peatones

void setup() {
  // Configuramos todos los pines como salida
  pinMode(LED_1, OUTPUT);
  pinMode(LED_2, OUTPUT);
  pinMode(LED_3, OUTPUT);
  pinMode(LED_4, OUTPUT);
  pinMode(LED_5, OUTPUT);
}

void loop() {
  // 🚦 Fase 1: Autos en verde, peatones en rojo
  digitalWrite(LED_1, LOW);   // Rojo autos apagado
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado
  digitalWrite(LED_3, HIGH);  // Verde autos encendido
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  delay(5000); // 5 segundos

  // 🚦 Fase 2: Amarillo autos, peatones siguen en rojo
  digitalWrite(LED_3, LOW);   // Verde autos apagado
  digitalWrite(LED_2, HIGH);  // Amarillo autos encendido
  delay(2000); // 2 segundos
  digitalWrite(LED_2, LOW);   // Amarillo autos apagado

  // 🚦 Fase 3: Rojo autos, verde peatones
  digitalWrite(LED_1, HIGH);  // Rojo autos encendido
  digitalWrite(LED_5, LOW);   // Rojo peatones apagado
  digitalWrite(LED_4, HIGH);  // Verde peatones encendido
  delay(3000); // 3 segundos
  
  for(int i =0; i<5; i++) {
    digitalWrite(LED_4, LOW);
    delay(300);
    digitalWrite(LED_4, HIGH);
    delay(300);
  }
 
  
  // 🚦 Fase 4: Rojo autos, rojo peatones (tiempo intermedio)
  digitalWrite(LED_4, LOW);   // Verde peatones apagado
  digitalWrite(LED_5, HIGH);  // Rojo peatones encendido
  //delay(2000); // 2 segundos
}
```
##### Ejercicio 6: Elipse interactivo
Arduino
```
unsigned int ADCValue;
void setup(){
    Serial.begin(9600);
}

void loop(){

 int val = analogRead(0);
   val = map(val, 0, 300, 0, 255);
    Serial.println(val);
delay(50);
}
```

codigo processing
```
Serial myPort;  // Crear objeto de la clase Serial
static String val;    // Datos recibidos desde el puerto serial
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM3";// Cambia el número (en este caso) para que coincida con el puerto correspondiente conectado a tu Arduino. 

  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);

}

void draw()
{
  if ( myPort.available() > 0) {  // Si hay datos disponibles,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // léelos y guárdalos en vals!
  }  
 //background(0);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 0 y 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Escala el valor de mouseX de 0 a 640 a un rango entre 40 y 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej6circuito.jpg" width= 1024 height= 800 />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej6.jpg" />

##### Ej 7 Arduino + botón + Processing
Código Arduino
```
int buttonPin = 2;  // Pin del botón
int buttonState = 0;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {   // Botón presionado
    Serial.println(1);        // Enviar un "1" a Processing
    delay(200);               // Evitar rebotes
  }
}
```
Código Processing
```
import processing.serial.*;

Serial myPort;
ArrayList<PVector> circles; 

void setup() {
  size(1920, 1080);
  background(0);
  
  // Ajusta el nombre del puerto según tu Arduino
  println(Serial.list());
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<PVector>();
}

void draw() {
  //background(0);
  
  // Dibujar círculos almacenados
  fill(0, 0, 0);
  //noStroke();
  stroke(255, 0, 0);
  for (PVector c : circles) {
    ellipse(c.x, c.y, 30, 30);
  }
  
  // Revisar si llega algo de Arduino
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.equals("1")) {
        // Cada vez que se aprieta el botón, agregar un círculo en posición aleatoria
        circles.add(new PVector(random(width), random(height)));
      }
    }
  }
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej7circuito.jpg" />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej7.jpg" width= 1024 height= 800 />

##### Ej unión botonera y potenciómetro 
```
setup() {
pinMode(2, INPUT);
pinMode(13, OUTPUT);
pinMode(9, OUTPUT);

loop() {
digitalRead(2) == HIGH) {
digitalWrite(13, HIGH);
} else {
digitalWrite(13, LOW);

int valor = analogRead(A0);
int brillo = map(valor, 0, 1023, 0, 255);
analogWrite(9, brillo);
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej%208%20profe.PNG" width= 1024 height= 600 />

##### EJ 8 Arduino Boton+Pot Processing PRESENTACIÓN
código arduino
```
int buttonPin = 2;       // Pin del botón
int potPin = A0;         // Pin del potenciómetro
int buttonState = 0;    //Variable donde se guarda el valor del botón 

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // Botón con resistencia interna
  Serial.begin(9600);
}

void loop() {
  buttonState = digitalRead(buttonPin);  //lee el estado del botón

  if (buttonState == HIGH) {   // si el Botón es presionado
    int potValue = analogRead(potPin);   // lee el potenciómetro que va 0 - 1023
    Serial.print("BTN,");     // etiqueta para Processing
    Serial.println(potValue); // mando el valor junto con el evento
    delay(400);               // debounce simple (permite evitar señales repetidas)
  }
}
```

Codigo processing
```
import processing.serial.*;  //se llama la librería serial

Serial myPort;
ArrayList<CircleData> circles; //aquí se guardan los círculos dibujados

void setup() {
  size(1200, 720);
  background(0);
  
  // Ajusta el puerto según tu Arduino
  println(Serial.list());
  //myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  myPort = new Serial(this, Serial.list()[0], 9600);
  
  circles = new ArrayList<CircleData>();
}

void draw() {
 // background((0),(200), random(100,255));
  
  // Dibujar todos los círculos guardados
  //fill(0, 150, 255);
  //noStroke();
  fill(random(255), 0, 200);  //relleno aleatorio
  stroke(60, 255, 0);
  for (CircleData c : circles) {
    ellipse(random(c.x), c.y, c.size*3, c.size*3);
    ellipse(c.x, random(300,900), c.size*6, c.size*4);
  }
  
  // Leer datos de Arduino y reconocer si hay datos nuevos
  if (myPort.available() > 0) {
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      val = trim(val);
      if (val.startsWith("BTN")) {
        // Extraer el valor del potenciómetro
        String[] parts = split(val, ',');
        if (parts.length == 2) {
          float potVal = float(parts[1]);
          float circleSize = map(potVal, 0, 1023, 10, 100); //traduce el valor del potenciómetro a un tamaño de 10-100 px, se gira el potenciometro, circulos mas grandes o pequeños
          circles.add(new CircleData(random(width), random(height), circleSize)); //se genera el nuevo circulo y lo guarda en la lista circles para que se dibuje en la pantalla
        }
      }
    }
  }
}

// Clase para guardar datos de cada círculo
class CircleData {
  float x, y, size;
  CircleData(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej8circuito.jpg" />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej8.jpg" width= 1024 height= 800 />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ej8.1.jpg" width= 1024 height= 800 />

#### Ejercicio If Else Potenciómetro
```
int valor;  // aquí guardaremos la lectura del sensor

void setup() {
  Serial.begin(9600);   // Inicia la comunicación serial
}

void loop() {
  valor = analogRead(A0);   // lee el pin analógico A0

  if (valor < 200) {
    Serial.println("Muy bajo");
  } else if (valor < 500) {
    Serial.println("Medio");
  } else {
    Serial.println("Alto");
  }

  delay(500); // medio segundo entre lecturas
}
```

##### Ejercicio 9: ForIfElse LEDS / if else if else
```
int leds[] = {2, 3, 4, 5}; // Creamos un arreglo con los pines donde van conectados los LEDs

void setup() {
  // Esta función corre solo una vez al iniciar Arduino
  for (int i = 0; i < 4; i++) {         // Recorre el arreglo desde i = 0 hasta i = 3
    pinMode(leds[i], OUTPUT);           // Configura cada pin del arreglo como salida (para controlar LEDs)
  }
}

void loop() {
  // Esta función corre en bucle infinito
  for (int i = 0; i < 4; i++) {         // Recorre los 4 LEDs, uno por uno
    if (i % 3 == 0) {                   // Si el índice es par (0, 2)...
      digitalWrite(leds[i], HIGH);      // Enciende el LED correspondiente
    } else {                            // Si el índice es impar (1, 3)...
      digitalWrite(leds[i], LOW);       // Apaga el LED correspondiente
    }
    delay(500);                         // Espera 0,5 segundos antes de pasar al siguiente
  }
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/forifelse.PNG" width= 1024 height= 500 />

###### Ejercicio 10: Botonera LED
```
// --- Configuración de botones ---
const int numButtons = 3;
const int buttonPins[numButtons] = {2, 4, 7};
const int ledButtonPins[numButtons] = {9, 10, 11}; // LEDs botones

// --- Configuración de potenciómetros ---
const int numPots = 2;
const int potPins[numPots] = {A0, A1};
const int ledPotPins[numPots] = {3, 5}; // LEDs PWM

// Variables de estados previos
int lastButtonState[numButtons];
int lastPotValue[numPots];

void setup() {
  Serial.begin(9600);

  // Configurar botones y LEDs
  for (int i = 0; i < numButtons; i++) {
    pinMode(buttonPins[i], INPUT_PULLUP);
    pinMode(ledButtonPins[i], OUTPUT);
    lastButtonState[i] = digitalRead(buttonPins[i]);
  }

  // Configurar LEDs de potenciómetros
  for (int i = 0; i < numPots; i++) {
    pinMode(ledPotPins[i], OUTPUT);
    lastPotValue[i] = analogRead(potPins[i]);
  }
}

void loop() {
  // Leer y enviar botones
  for (int i = 0; i < numButtons; i++) {
    int buttonState = digitalRead(buttonPins[i]);

    // LED se enciende cuando botón está presionado
    digitalWrite(ledButtonPins[i], buttonState == LOW ? HIGH : LOW);

    if (buttonState != lastButtonState[i]) {  // enviar cambios
      Serial.print("B");
      Serial.print(i); 
      Serial.print(":");
      Serial.println(buttonState);
      lastButtonState[i] = buttonState;
    }
  }

  // Leer y enviar potenciómetros
  for (int i = 0; i < numPots; i++) {
    int potValue = analogRead(potPins[i]); // 0–1023
    int pwmValue = potValue / 4;           // 0–255

    // Ajustar LED según valor
    analogWrite(ledPotPins[i], pwmValue);

    if (abs(pwmValue - lastPotValue[i]) > 2) { // evitar ruido
      Serial.print("P");
      Serial.print(i);
      Serial.print(":");
      Serial.println(pwmValue);
      lastPotValue[i] = pwmValue;
    }
  }

  delay(10);
}
```
##### Botonera Processing audios
```
// Importamos librería para comunicación serial
import processing.serial.*;
// Importamos librería Minim para manejar audio
import ddf.minim.*;

// Declaramos el objeto serial para comunicarnos con Arduino
Serial myPort;
// Objeto principal de Minim
Minim minim;
// Array de reproductores de audio (3 pistas)
AudioPlayer[] players;
// Variable para guardar el índice de la pista que está sonando
int currentTrack = -1;  // -1 significa que no hay pista activa al inicio

void setup() {
  size(400, 200); // Ventana de 400x200 píxeles
  
  // --- Configuración del puerto serial ---
  printArray(Serial.list()); // Muestra en consola la lista de puertos disponibles
  myPort = new Serial(this, Serial.list()[0], 9600); // Abrimos el primer puerto de la lista a 9600 baudios
  
  // --- Configuración de audio ---
  minim = new Minim(this); // Inicializamos Minim
  players = new AudioPlayer[3]; // Creamos un array de 3 reproductores
  
  // Cargamos los 3 archivos de audio desde la carpeta "data"
  players[0] = minim.loadFile("audio1.mp3", 2048); 
  players[1] = minim.loadFile("audio2.mp3", 2048); 
  players[2] = minim.loadFile("audio3.mp3", 2048); 
}

void draw() {
  background(0); // Fondo negro
  fill(255);     // Color blanco para el texto
  textSize(16);  // Tamaño del texto
  
  // Mostramos en pantalla qué botón está activo
  text("Botón actual: " + (currentTrack == -1 ? "ninguno" : currentTrack), 20, 40);
}

void serialEvent(Serial myPort) {
  // Leemos la cadena que llega desde Arduino hasta el salto de línea
  String inString = trim(myPort.readStringUntil('\n'));
  
  // Si no llega nada, salimos
  if (inString == null) return;

  // --- Si el mensaje recibido empieza con "B" significa que es un botón ---
  if (inString.startsWith("B")) {
    // Quitamos la letra "B" y separamos el mensaje en partes (ejemplo "0:0")
    String[] parts = split(inString.substring(1), ':');
    
    // Si realmente recibimos dos partes (índice y estado)
    if (parts.length == 2) {
      int buttonIndex = int(parts[0]); // Número del botón (0,1,2)
      int state = int(parts[1]);       // Estado del botón (0 = presionado, 1 = suelto)
      
      // Si el botón fue presionado (LOW = 0 en Arduino)
      if (state == 0) { 
        playTrack(buttonIndex); // Llamamos a la función para reproducir la pista correspondiente
      }
    }
  }
}

// --- Función que reproduce una pista según el botón ---
void playTrack(int index) {
  // Si ya había una pista sonando, la pausamos y la rebobinamos al inicio
  if (currentTrack != -1 && players[currentTrack].isPlaying()) {
    players[currentTrack].pause();
    players[currentTrack].rewind();
  }
  
  // Reproducimos en bucle la pista seleccionada
  players[index].loop();
  
  // Actualizamos la variable para saber cuál es la pista activa
  currentTrack = index;
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/botonera.PNG" width= 1024 height= 500 />
LINK DRIVE CON REGISTRO DE SONIDOS: https://drive.google.com/drive/folders/1BS_4HVPIA8Epd3rhjGsshbNoOhZ9KH9F?usp=drive_link

# Inasistencias con fecha: 14 y 21 de Octubre con justificativo médico para el día 21.

### sensor sharp/ de distancia

codigo arduino
```
// Definir el pin del sensor Sharp
int sharpPin = A0;

void setup() {
  Serial.begin(9600); // Iniciar comunicación serial
}

void loop() {
  int sensorValue = analogRead(sharpPin); // Leer valor del sensor
  Serial.println(sensorValue); // Enviar valor a Processing
  delay(100); // Esperar un momento
}
```
codigo processing
```
import processing.serial.*;

Serial myPort;  // Create object from Serial class
static String val;    // Data received from the serial port
int sensorVal = 0;

void setup()
{
  background(0); 
  //fullScreen(P3D);
   size(1080, 720);
   noStroke();
  noFill();
  String portName = "COM5";// Change the number (in this case ) to match the corresponding port number connected to your Arduino. 

  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
}

void draw()
{
  if ( myPort.available() > 0) {  // If data is available,
  val = myPort.readStringUntil('\n'); 
  try {
   sensorVal = Integer.valueOf(val.trim());
  }
  catch(Exception e) {
  ;
  }
  println(sensorVal); // read it and store it in vals!
  }  
 //background(0);
  // Scale the mouseX value from 0 to 640 to a range between 0 and 175
  float c = map(sensorVal, 0, width, 0, 400);
  // Scale the mouseX value from 0 to 640 to a range between 40 and 300
  float d = map(sensorVal, 0, width, 40,500);
  fill(255, c, 0);
  ellipse(width/2, height/2, d, d);   

}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/sensorsharp.jpg" />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ejsensorsharp.jpg" />


### Sensor de humedad / de vapor
##### Codigo Arduino
```
void setup()
{
  Serial.begin(9600);// abre el puerto serial y Establece la velocidad en baudios a 9600 bps
}
void loop()
{
  int sensorValue;
  sensorValue = analogRead(0);   //conectar el sensor de humedad al pin analogo 0
  Serial.println(sensorValue); //imprime el valor a serial.
  delay(200);
}
```

### Sensor Sharp con Camara/video/movimiento

##### Codigo Arduino
```
// --- Sensor Sharp conectado al pin A0 ---
int sensorPin = A0;
int valor;

void setup() {
  Serial.begin(9600);
}

void loop() {
  valor = analogRead(sensorPin);
  Serial.println(valor);
  delay(50); // envío cada 50 ms
}
```

##### Codigo processing
```
// --- Librerías necesarias ---
import processing.serial.*;
import processing.video.*;

// --- Variables de cámara y serial ---
Capture cam;
Serial myPort;

// --- Variables del sensor ---
float sensorValue = 0;
float suavizado = 0;

// --- Parámetros para detección de silueta ---
float umbral = 100; // controla el contraste para definir la silueta

void setup() {
  size(1280, 720);
  background(0);
  
  // --- Inicializar cámara ---
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se encontró cámara.");
    exit();
  } else {
    println("Cámara encontrada: " + cameras[0]);
    cam = new Capture(this, cameras[0]);
    cam.start();
  }
  
  // --- Inicializar puerto serie (Arduino) ---
  // Puedes ver la lista de puertos con println(Serial.list());
  String portName = Serial.list()[0]; 
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  //myPort = new Serial(this, portName, 9600);
}

void draw() {
  background(0);
  
  // --- Leer datos del sensor ---
  while (myPort.available() > 0) {
    String inString = trim(myPort.readStringUntil('\n'));
    if (inString != null) {
      sensorValue = float(inString);
      suavizado = lerp(suavizado, sensorValue, 0.1);
    }
  }
  
  // --- Mapear los valores del sensor ---
  float escala = map(suavizado, 0, 1023, 1.5, 0.5); // tamaño de la silueta
  float alpha = map(suavizado, 0, 1023, 255, 80);   // opacidad según distancia
  
  // --- Captura de video ---
  if (cam.available()) {
    cam.read();
  }

  // --- Dibujar silueta desde la cámara ---
  cam.loadPixels();
  loadPixels();
  
  for (int y = 0; y < cam.height; y++) {
    for (int x = 0; x < cam.width; x++) {
      int loc = x + y * cam.width;
      color c = cam.pixels[loc];
      float brillo = brightness(c);
      
      // Si el brillo es menor que el umbral, dibujamos píxel blanco (silueta)
      if (brillo < umbral) {
        int px = int(x * escala);
        int py = int(y * escala);
        if (px < width && py < height) {
          stroke(255, alpha);
          point(px, py);
        }
      }
    }
  }
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/ejsensorsharpcuerpovideo.jpg" />



### Ejercicio promedio de imagenes (con sensor sharp)
##### Código arduino
```
void setup() {
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(A0);
  Serial.println(potValue);
  delay(20);
}
```

##### Código processing
```
// --- Librerías necesarias ---
// Importa la librería de comunicación serial para conectar con Arduino
import processing.serial.*;
// Importa la clase File de Java para listar archivos y carpetas
import java.io.File;

// --- Comunicación serial con Arduino ---
// Variable que contendrá el objeto de puerto serial (conexión con Arduino)
Serial myPort;
// Variable que guarda el valor leído del potenciómetro (0..1023)
float potValue = 0;

// --- Variables de imágenes ---
// Arreglo dinámico que contendrá todas las imágenes cargadas desde la carpeta
PImage[] imgs;
// Imagen donde se almacenará el resultado del promedio/interpolación
PImage avgImg;

// --- Configuración inicial ---
void setup() {
  // Define el tamaño de la ventana de Processing (ancho, alto)
  size(745, 1024);
  
  // Cargar imágenes desde carpeta "data/imagenes"
  // Llama a la función que busca todas las imágenes dentro de esa carpeta
  imgs = loadImagesFromFolder("imagenes");
  // Imprime en la consola cuántas imágenes se cargaron (útil para debug)
  println("Imágenes cargadas: " + imgs.length);
  
  // Redimensionar todas las imágenes al tamaño del lienzo para que coincidan pixel a pixel
  for (int i = 0; i < imgs.length; i++) {
    imgs[i].resize(width, height); // redimensiona cada imagen al ancho y alto de la ventana
  }
  
  // Crea una imagen vacía del tamaño del lienzo donde guardaremos el promedio
  avgImg = createImage(width, height, RGB);
  
  // Conectar con Arduino (ver lista de puertos)
  // Muestra en consola la lista de puertos seriales disponibles (para identificar cuál usar)
  printArray(Serial.list());
  // Alternativa automática (comentada): abrir el primer puerto disponible a 9600 baudios
  // myPort = new Serial(this, Serial.list()[0], 9600);
  // Abrir un puerto específico (ejemplo para macOS). Ajusta según el puerto real en tu sistema.
  myPort = new Serial(this, "/dev/cu.usbmodem1101", 9600);
  // Nota: si no funciona el puerto, revisa la salida de printArray(Serial.list()) y usa el nombre correcto.
}

// --- Bucle principal ---
// draw() se ejecuta continuamente (aprox. 60 veces por segundo)
void draw() {
  // Pinta el fondo de negro en cada frame
  background(0);
  // Llama a la función que lee datos desde el puerto serial (actualiza potValue)
  readSerial();
  
  // Si no hay imágenes o sólo hay una, no hacemos nada (necesitamos al menos 2 para interpolar)
  if (imgs == null || imgs.length < 2) return;
  
  // Mapear el valor del potenciómetro (0..1023) al rango de índices entre 0 y imgs.length-1
  // Esto permite moverse a lo largo de la secuencia de imágenes
  float mixValue = map(potValue, 0, 1023, 0, imgs.length - 1);
  
  // Calcular el promedio/interpolación entre las dos imágenes vecinas según mixValue
  avgImagesWeighted(mixValue);
  
  // Mostrar la imagen promedio resultante en la pantalla, en la posición (0,0)
  image(avgImg, 0, 0);
  
  // Mostrar texto con el valor actual del potenciómetro en la esquina inferior izquierda
  fill(255); // color blanco para el texto
  text("Valor pot: " + nf(potValue, 1, 0), 10, height - 10); // nf para formatear el número
}

// --- Función que calcula el promedio ponderado entre imágenes ---
// mix es un valor flotante que indica la posición entre imágenes (ej. 2.3 -> entre img2 e img3)
void avgImagesWeighted(float mix) {
  // Accede al arreglo de píxeles de avgImg para poder modificarlos directamente
  avgImg.loadPixels();
  
  // Asegura que mix esté dentro del rango válido [0, imgs.length - 1]
  mix = constrain(mix, 0, imgs.length - 1);
  
  // i1 es el índice de la imagen "inferior" (por ejemplo 2 en 2.3)
  int i1 = floor(mix);
  // i2 es la imagen siguiente (i1 + 1), pero sin pasarse del último índice
  int i2 = min(i1 + 1, imgs.length - 1);
  // t es la fracción entre i1 e i2 (por ejemplo, 0.3 si mix es 2.3)
  float t = mix - i1;
  
  // Cargar los píxeles de las dos imágenes que vamos a mezclar
  imgs[i1].loadPixels();
  imgs[i2].loadPixels();
  
  // Recorre todos los píxeles de la imagen objetivo
  for (int i = 0; i < avgImg.pixels.length; i++) {
    // Coge el color del píxel i de la imagen i1
    color c1 = imgs[i1].pixels[i];
    // Coge el color del píxel i de la imagen i2
    color c2 = imgs[i2].pixels[i];
    
    // Interpola por separado cada componente de color (rojo, verde, azul)
    // red(c1) obtiene la componente roja del color c1
    float r = lerp(red(c1), red(c2), t);
    // green(c1) obtiene la componente verde del color c1
    float g = lerp(green(c1), green(c2), t);
    // blue(c1) obtiene la componente azul del color c1
    float b = lerp(blue(c1), blue(c2), t);
    
    // Crea un nuevo color a partir de las componentes interpoladas y lo asigna al píxel i
    avgImg.pixels[i] = color(r, g, b);
  }
  
  // Aplica los cambios realizados en el arreglo de píxeles a la imagen avgImg
  avgImg.updatePixels();
}

// --- Leer valor del potenciómetro desde Arduino ---
// Lee datos desde el puerto serial hasta encontrar saltos de línea y los convierte a número
void readSerial() {
  // Mientras el puerto exista y tenga bytes disponibles para leer...
  while (myPort != null && myPort.available() > 0) {
    // Lee una línea completa hasta '\n' (salto de línea)
    String val = myPort.readStringUntil('\n');
    if (val != null) {
      // Elimina espacios y caracteres de control al inicio/final
      val = trim(val);
      // Si la cadena no está vacía, la convierte a float y la asigna a potValue
      if (val.length() > 0) {
        potValue = float(val);
      }
    }
  }
}

// --- Cargar todas las imágenes desde una carpeta ---
// Devuelve un arreglo PImage[] con todas las imágenes JPG/PNG encontradas en data/folderName
PImage[] loadImagesFromFolder(String folderName) {
  // Construye la ruta absoluta a la carpeta dentro de la carpeta data del sketch
  String path = sketchPath("data/" + folderName);
  // Crea un objeto File apuntando a esa carpeta
  File folder = new File(path);
  // Lista todos los archivos dentro de la carpeta (puede devolver null si no existe)
  File[] files = folder.listFiles();
  
  // Si files es null, la carpeta no existe o no tiene permisos -> avisar y devolver null
  if (files == null) {
    println("Carpeta no encontrada: " + path);
    return null;
  }
  
  // Crea una lista dinámica para almacenar las PImage cargadas
  ArrayList<PImage> loaded = new ArrayList<PImage>();
  // Recorre cada archivo encontrado en la carpeta
  for (File f : files) {
    // Obtiene el nombre del archivo y lo convierte a minúsculas para comparar extensiones
    String fname = f.getName().toLowerCase();
    // Si termina en .jpg o .png, lo cargamos
    if (fname.endsWith(".jpg") || fname.endsWith(".png")) {
      // loadImage busca en data/folderName el archivo y devuelve un PImage
      PImage img = loadImage(folderName + "/" + f.getName());
      // Si la imagen se cargó correctamente, la agregamos a la lista
      if (img != null) loaded.add(img);
    }
  }
  
  // Convierte la ArrayList a un arreglo PImage[] y lo retorna
  return loaded.toArray(new PImage[loaded.size()]);
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/promedioimagenes.jpg" />

LINK DRIVE CON VIDEOS DE LOS EJERCICIOS:
https://drive.google.com/drive/folders/1b45O2BfcJ6RduNLXU76lctVqxf0sKntt



### Ejercicio Grupal Entrega 4 de nov
##### Rastro sin contacto.

Descripción: Para nuestro proyecto ocuparemos Processing, arduino y potenciómetro como herramientas para desarrollar nuestra obra. En Processing buscaremos crear un una obra de carácter interactivo y con elementos visuales estimulantes y que sean llamativos desde el aspecto de color y la figura. Esta instalación interactiva es posible gracias al uso del sensor de la cámara que ayuda a reconocer el movimiento, en este caso el de la mano, de quien esté frente a esta.
Cuando el usuario mueve la mano frente a la cámara, aparece una estela blanca que sigue ese movimiento. Además, aparece un círculo amarillo en la pantalla que el usuario puede y debe tocar con su mano. Cuando lo toca mediante la estela, el círculo explota y aparece otro nuevo en nueva posición aleatoria.
Por medio del arduino y el potenciómetro se añade una nueva experiencia,ya que con ayuda del potenciómetro se cambia el color de la estela a gusto personal, esto añade un sentimiento de control sobre la actividad.

### Código Arduino:
```
void setup() {
  Serial.begin(9600);
}

void loop() {
  int valor = analogRead(A0);  // Lee el potenciómetro
  Serial.println(valor);       // Envía el valor (0–1023)
  delay(50);                   // Evita saturar el puerto serie
}
```
### Codigo processing
```
import processing.video.*;
import processing.serial.*;

Capture cam;
Serial myPort;

// --- Variables de movimiento ---
PImage prevFrame;
float threshold = 40; // sensibilidad
PVector motionPos;

// --- Estela (seguimiento) ---
int num = 60;
float mx[] = new float[num];
float my[] = new float[num];

// --- Color controlado por potenciómetro ---
float potValue = 0;  
color trailColor = color(255, 255, 255); 

// --- Círculo interactivo ---
PVector targetCircle;
float circleSize = 60;
boolean circleVisible = true;
boolean exploding = false;
float explosionSize = 0;
float explosionAlpha = 255;

// --- Límites seguros ---
float margin = 100;

void setup() {
  size(640, 480);
  
  // Iniciar cámara
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se detectó ninguna cámara.");
    exit();
  }
  cam = new Capture(this, cameras[0]);
  cam.start();
  
  prevFrame = createImage(width, height, RGB);
  motionPos = new PVector(width/2, height/2);
  
  noStroke();
  
  // Crear círculo aleatorio
  targetCircle = new PVector(random(margin, width - margin), random(margin, height - margin));
  
  // --- Inicializar puerto serie ---
  println(Serial.list()); // muestra los puertos disponibles
  String portName = "COM8"; // ✅ Puerto correcto
  myPort = new Serial(this, portName, 9600);
  myPort.bufferUntil('\n');
}

void captureEvent(Capture cam) {
  cam.read();
}

void serialEvent(Serial myPort) {
  String inString = trim(myPort.readStringUntil('\n'));
  if (inString != null && inString.length() > 0) {
    try {
      potValue = float(inString);
      potValue = constrain(potValue, 0, 1023);
      
      // 🎨 Mapear valor del potenciómetro a un tono de color HSB (0-255)
      colorMode(HSB, 255);
      float hue = map(potValue, 0, 1023, 0, 255);
      trailColor = color(hue, 255, 255);  // tono, saturación, brillo
      colorMode(RGB, 255); // volver a RGB para el resto del dibujo
    } catch (Exception e) {
      println("Error al leer potenciómetro: " + e);
    }
  }
}

void draw() {
  if (cam.width == 0) return;
  
  background(0);
  
  PImage diff = createImage(width, height, RGB);
  cam.loadPixels();
  prevFrame.loadPixels();
  diff.loadPixels();
  
  float avgX = 0;
  float avgY = 0;
  int motionCount = 0;

  // Detectar movimiento (mano)
  for (int i = 0; i < cam.pixels.length; i++) {
    color curr = cam.pixels[i];
    color prev = prevFrame.pixels[i];
    
    float diffR = abs(red(curr) - red(prev));
    float diffG = abs(green(curr) - green(prev));
    float diffB = abs(blue(curr) - blue(prev));
    float diffVal = (diffR + diffG + diffB) / 3;
    
    if (diffVal > threshold) {
      diff.pixels[i] = color(255);
      int x = i % width;
      int y = i / width;
      avgX += x;
      avgY += y;
      motionCount++;
    } else {
      diff.pixels[i] = color(0);
    }
  }
  diff.updatePixels();
  prevFrame.copy(cam, 0, 0, width, height, 0, 0, width, height);
  
  // Posición promedio del movimiento
  if (motionCount > 500) {
    motionPos.set(width - (avgX / motionCount), avgY / motionCount);
  }

  // --- Estela colorida controlada por potenciómetro ---
  int which = frameCount % num;
  mx[which] = motionPos.x;
  my[which] = motionPos.y;

  noStroke();
  for (int i = 0; i < num; i++) {
    int index = (which + 1 + i) % num;
    float alpha = map(i, 0, num, 50, 200);
    fill(red(trailColor), green(trailColor), blue(trailColor), alpha);
    ellipse(mx[index], my[index], i, i);
  }

  // --- Círculo amarillo interactivo ---
  if (circleVisible) {
    fill(255, 200, 0, 200);
    ellipse(targetCircle.x, targetCircle.y, circleSize, circleSize);
    
    float d = dist(motionPos.x, motionPos.y, targetCircle.x, targetCircle.y);
    if (d < circleSize / 2) {
      circleVisible = false;
      exploding = true;
      explosionSize = circleSize;
      explosionAlpha = 255;
    }
  }

  // --- Explosión ---
  if (exploding) {
    fill(255, random(150, 255), 0, explosionAlpha);
    ellipse(targetCircle.x, targetCircle.y, explosionSize, explosionSize);
    explosionSize += 15;
    explosionAlpha -= 20;

    if (explosionAlpha <= 0) {
      exploding = false;
      targetCircle.set(random(margin, width - margin), random(margin, height - margin));
      circleVisible = true;
    }
  }
}
```
### LINKS A VIDEOS DE PRUEBA
https://www.youtubeeducation.com/watch?v=XciaUtJu_mo 
https://www.youtubeeducation.com/watch?v=OPgpKR6e550 



## Entrega Final:
Para esta ocasión, mejoramos el código pasado con: ya no sigue solo el movimiento, sino que reconoce el color rojo. Existe un contador de puntos, el cual se reinicia una vez se apreta el botón conectado al arduino. Mantuvimos el poteciómetro para el cambio de color de las estelas. 

#### Código Arduino:
```
const int buttonPin = A1;  // Pin donde está conectado el botón
int lastButtonState = HIGH;
int currentButtonState;

void setup() {
  Serial.begin(9600);
  pinMode(buttonPin, INPUT_PULLUP);  // Configura botón con resistencia pull-up interna
}

void loop() {
  // Leer estado del botón (LOW cuando está presionado)
  currentButtonState = digitalRead(buttonPin);

  if (lastButtonState == HIGH && currentButtonState == LOW) {  // flanco de bajada, botón presionado
    Serial.println("R");  // enviar comando reiniciar
    delay(200);           // anti rebote y evitar múltiples envíos
  } else if (currentButtonState == HIGH) {  // botón no presionado, enviar valor potenciómetro
    int valor = analogRead(A0); // Lee valor potenciómetro
    Serial.println(valor);      // Envía el valor (0–1023)
    delay(50);                  // evita saturar puerto serie
  }

  lastButtonState = currentButtonState;
}

```

### Código Processing
```
import processing.video.*;
import processing.serial.*;
import ddf.minim.*;   // 🔊 Librería de sonido

Capture cam;
Serial myPort;

// --- Variables de sonido ---
Minim minim;
AudioPlayer[] sonidos = new AudioPlayer[5];

// --- Variables de color (detección de manos rojas) ---
color targetColor = color(255, 0, 0);  
float colorThreshold = 150;            
PVector motionPos;

// --- Estela (seguimiento) ---
int num = 60;
float mx[] = new float[num];
float my[] = new float[num];

// --- Color controlado por potenciómetro ---
float potValue = 0;  
color trailColor = color(255, 255, 255); 

// --- Círculo interactivo ---
PVector targetCircle;
float circleSize = 60;
boolean circleVisible = true;
boolean exploding = false;
float explosionSize = 0;
float explosionAlpha = 255;

// --- Límites seguros ---
float margin = 100;

// --- Conteo de explosiones ---
int explosionCount = 0;

void setup() {
  size(640, 480);
  
  // Iniciar cámara
  String[] cameras = Capture.list();
  if (cameras.length == 0) {
    println("No se detectó ninguna cámara.");
    exit();
  }
  cam = new Capture(this, 640, 480, cameras[0]);
  cam.start();
  
  motionPos = new PVector(width/2, height/2);
  noStroke();
  
  // Crear círculo aleatorio
  targetCircle = new PVector(random(margin, width - margin), random(margin, height - margin));
  
  // --- Inicializar puerto serie ---
  println(Serial.list()); 
  String portName = "COM3"; 
  myPort = new Serial(this, portName, 9600);
  myPort.bufferUntil('\n');

  // --- Inicializar sonido ---
  minim = new Minim(this);

  sonidos[0] = minim.loadFile("sonido1.mp3");
  sonidos[1] = minim.loadFile("sonido2.mp3");
  sonidos[2] = minim.loadFile("sonido3.mp3");
  sonidos[3] = minim.loadFile("sonido4.mp3");
  sonidos[4] = minim.loadFile("sonido5.mp3");
}

void captureEvent(Capture cam) {
  cam.read();
}

void serialEvent(Serial myPort) {
  String inString = trim(myPort.readStringUntil('\n'));
  if (inString != null && inString.length() > 0) {
    if (inString.equals("R")) {
      explosionCount = 0;  // Reiniciar conteo si llega "R"
      println("Conteo reiniciado desde Arduino");
    } else {
      try {
        potValue = float(inString);
        potValue = constrain(potValue, 0, 1023);
        
        // 🎨 Mapear potenciómetro a tono de color
        colorMode(HSB, 255);
        float hue = map(potValue, 0, 1023, 0, 255);
        trailColor = color(hue, 255, 255);
        colorMode(RGB, 255);
      } catch (Exception e) {
        println("Error al leer potenciómetro: " + e);
      }
    }
  }
}

void draw() {
  if (cam.width == 0) return;
  
  background(0); 

  cam.loadPixels();
  
  // --- Buscar color rojo en cámara ---
  float avgX = 0;
  float avgY = 0;
  int count = 0;
  
  for (int x = 0; x < cam.width; x += 2) {
    for (int y = 0; y < cam.height; y += 2) {
      int loc = x + y * cam.width;
      int current = cam.pixels[loc];
      
      float d = distSqColor(current, targetColor);
      if (d < colorThreshold * colorThreshold) {
        avgX += x;
        avgY += y;
        count++;
      }
    }
  }
  
  if (count > 50) {
    avgX /= count;
    avgY /= count;
    
    motionPos.set(width - avgX, avgY);  // efecto espejo
  }

  // --- Estela colorida ---
  int which = frameCount % num;
  mx[which] = motionPos.x;
  my[which] = motionPos.y;

  noStroke();
  for (int i = 0; i < num; i++) {
    int index = (which + 1 + i) % num;
    float alpha = map(i, 0, num, 50, 200);
    fill(red(trailColor), green(trailColor), blue(trailColor), alpha);
    ellipse(mx[index], my[index], i, i);
  }

  // --- Círculo amarillo interactivo ---
  if (circleVisible) {
    fill(255, 200, 0, 200);
    ellipse(targetCircle.x, targetCircle.y, circleSize, circleSize);
    
    float d = dist(motionPos.x, motionPos.y, targetCircle.x, targetCircle.y);
    if (d < circleSize / 2) {

      // 🔥 Explosión y sonido
      circleVisible = false;
      exploding = true;
      explosionSize = circleSize;
      explosionAlpha = 255;

      playRandomSound();   // 🔊 Sonido aleatorio
    }
  }

  // --- Explosión ---
  if (exploding) {
    fill(255, random(150, 255), 0, explosionAlpha);
    ellipse(targetCircle.x, targetCircle.y, explosionSize, explosionSize);
    explosionSize += 15;
    explosionAlpha -= 20;

    if (explosionAlpha <= 0) {
      exploding = false;
      targetCircle.set(random(margin, width - margin), random(margin, height - margin));
      circleVisible = true;
      
      explosionCount++;  // Incrementar conteo
    }
  }
  
  // Mostrar conteo de círculos explotados
  fill(255);
  textSize(20);
  text("Explotados: " + explosionCount, 10, height - 20);
}

// --- Función de distancia entre colores ---
float distSqColor(int c1, int c2) {
  float r1 = red(c1);
  float g1 = green(c1);
  float b1 = blue(c1);
  float r2 = red(c2);
  float g2 = green(c2);
  float b2 = blue(c2);
  return sq(r1 - r2) + sq(g1 - g2) + sq(b1 - b2);
}

// --- 🔊 Reproducir sonido aleatorio ---
void playRandomSound() {
  int idx = int(random(sonidos.length));
  sonidos[idx].rewind();
  sonidos[idx].play();
}
```
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/Montaje.jpg" />
<img src= "https://raw.githubusercontent.com/DakaRG/INTERFAZ2/refs/heads/main/img/montaje%201.jpg" />

LINK DRIVE REGISTRO DE MONTAJE FINAL
https://drive.google.com/drive/u/0/folders/1Dsicy1mUTEc919w5UEG8gVPpzdoaSMIv 
