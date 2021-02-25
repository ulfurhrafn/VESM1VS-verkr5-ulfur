# VESM1VS-verkr5-ulfur


#5,1
~~~
a) stýrimótor fer aðeins 180° of get farið framm og aftur mjög nákvæmlega 
b) með viðnámi

~~~

#5,3

~~~
Stýrimótorinn fer eina gráðu á 2ms 
~~~

#5,4
~~~
a) Hver er munurinn á rafhlöðu og rafþétti? Raflaða heldur inni mikið rafmagn og getur gefið straum lengi þegar raflaðan er tengd við rás. Rafþétturinn er notaður til að halda strauminum jöfnuðum og gefa auka rafmagn þegar straumurinn verður daufari. 
b) Non-Polarized geta farið í báðar áttir sem er mikilvægt því að DC mótorar þurfa að svissa áttir straumsins til að snúa við. Polarized geta ekki farið í báðar áttir og muna springa ef straumurinn fer frá - til +. þeir eru góðir sem backup þegar rafmagnið slegur út svo sum forrit geta vistað áður en rafmagnið fer út
~~~

#5,5

~~~
```#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 0; pos <= 180; pos += 1) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(1);                       // waits 15ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(2);                       // waits 15ms for the servo to reach the position
  }
}
```

![Sweep forritið í gangi](https://github.com/ulfurhrafn/VESM1VS-verkr5-ulfur/blob/main/Servo%20Sweep.mp4)
~~~

#5,6
~~~
Stepper mótor notar segull til að snúast og tekur stutt nákvæm skref. DC mótor hinsvegar getur farið í báðar áttir og þurfa ekki forrit heldur er hægt að nota áttina á straumnum
~~~

#5,7

~~~
[Stepper](https://raw.githubusercontent.com/ulfurhrafn/VESM1VS-verkr5-ulfur/main/stepper.jpg)

```
*/

#include <Stepper.h>

const int stepsPerRevolution = 200;  // change this to fit the number of steps per revolution
// for your motor

// initialize the stepper library on pins 8 through 11:
Stepper myStepper(stepsPerRevolution, 8, 9, 10, 11);

int stepCount = 0;         // number of steps the motor has taken

void setup() {
  // initialize the serial port:
  Serial.begin(9600);
}

void loop() {
  // step one step:
  myStepper.step(1);
  Serial.print("steps:");
  Serial.println(stepCount);
  stepCount++;
  delay(500);
}
```
~~~

#5,8
~~~
```//Includes the Arduino Stepper Library
#include <Stepper.h>

// Defines the number of steps per rotation
const int stepsPerRevolution = 2038;

// Creates an instance of stepper class
// Pins entered in sequence IN1-IN3-IN2-IN4 for proper step sequence
Stepper myStepper = Stepper(stepsPerRevolution, 8, 10, 9, 11);

void setup() {
	// Nothing to do (Stepper Library sets pins as outputs)
}

void loop() {
	// Rotate CW slowly
	myStepper.setSpeed(100);
	myStepper.step(stepsPerRevolution);
	delay(1000);
	
	// Rotate CCW quickly
	myStepper.setSpeed(700);
	myStepper.step(-stepsPerRevolution);
	delay(1000);
}
```
~~~

