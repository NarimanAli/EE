# Electronics and Power Task 1,2,3


# Task 1 : Brushless motor control system design, including the algorithm and the electronic circuit

Brushless Code :

``` c++
int buttonState = 0;
int potensio = 0;
int saveData = 0;
int pinA = 7;
int pinB = 8;
int pwm = 9;
void setup()
{
  pinMode(2, INPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
}
void loop()
{
  buttonState = digitalRead(2);
  if(buttonState == LOW){
    right();
  }
  else{
    left();
  }```
  delay(10);
}
void right()
{
  digitalWrite(pinA, LOW);
  digitalWrite(pinB, HIGH);
  saveData = analogRead(potensio);
  analogWrite(pwm, saveData);
  delay(15);
}
  void left()
{
  digitalWrite(pinA, HIGH);
  digitalWrite(pinB, LOW);
  saveData = analogRead(potensio);
  analogWrite(pwm, saveData);
  delay(15);
}
```



#  Task 2,3 Connecting the Stepper motor and the Servo motor with the arduino
# Stepper Code

```c++
#include<Stepper.h> 

const int stepsPerRevolution = 200; //change this to fit the number
//of revolutions for your motor

//initialize the stepper library on pins 8 through 11 Stepper mystepper(stepsPerRevolution, 8, 9, 10, 11); 
int stepCount = 0; // number of steps the motor has taken 

void setup() { 
  // nothing to do inside the setup 
} 

void loop(){ 
  // read the sensor value:
  int sensorReading = analogRead(A0);
  // map it to a range from 0 to 100:
  int motorSpeed = map(sensorReading, 0, 1023, 0, 250); 
  // set the motor speed: 
  if (motorSpeed > 0){ 
    mystepper.setSpeed(motorSpeed);
    // step 1/100 of a revolution
    mystepper.step(stepsPerRevolution/100); 
  } 
}
```


# Servo Code

```c++
#include<Servo.h>

Servo servoequiv;
int pos = 0; 
void setup() { 
  servoequiv.attach(13); //because I have connected signal pin with 13
}

void loop() { 
  // rotate from 0 to 180 degree 
  
  for(pos=0;pos<=180;pos++) 
    { servoequiv.write(pos);
    delay(15);
    }
  
  for(pos=180;pos>=0;pos--);
    { servoequiv.write(pos); 
    delay(15);
    } 
}
```
