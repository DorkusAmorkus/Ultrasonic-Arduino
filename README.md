# Ultrasonic-Arduino

/*Turns lights on and off using an ultrasonic sensor 
Source: http://www.arduino.cc/en/Tutorial/DigitalReadSerial

/*

//identifies PIN numbers

const int trigPin = 3;
const int echoPin = 4;
int ledPin = 13;
int ledPin2 = 12;
int ledPin3 = 11;
int ledPin4 = 10;

// variables:
long duration;
int distance;

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(ledPin, OUTPUT); //Pins that the lights attatch to
pinMode(ledPin2, OUTPUT);
pinMode(ledPin3, OUTPUT);
pinMode(ledPin4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}

void loop() {


// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);


// Calculating the distance
distance= duration*0.034/2;

  distance = map(distance, 0, 20, 10, 13);
   digitalWrite(distance, HIGH);   // turn the LED on (HIGH is the voltage level)
   

   if (distance == 10){
   digitalWrite(ledPin, HIGH); //These "if" statements all the way down change which LEDs are on, depending on proximity to the sensor
    digitalWrite(ledPin2, LOW);
    digitalWrite(ledPin3, LOW);
    digitalWrite(ledPin4, LOW);
   }

    if (distance == 11){
    digitalWrite(ledPin, LOW);
    digitalWrite(ledPin2, HIGH);
    digitalWrite(ledPin3, LOW);
    digitalWrite(ledPin4, LOW);
   }
    if (distance == 12){
    digitalWrite(ledPin, LOW);
    digitalWrite(ledPin2, LOW);
    digitalWrite(ledPin3, HIGH);
    digitalWrite(ledPin4, LOW);
   }
    if (distance == 13){
    digitalWrite(ledPin, LOW);
    digitalWrite(ledPin2, LOW);
    digitalWrite(ledPin3, LOW);
    digitalWrite(ledPin4, HIGH);
   }
  // Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);


// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);

}
