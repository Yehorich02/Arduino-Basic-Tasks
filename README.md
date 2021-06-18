# Tasks

## Flashing built-in LED

***TASK*** >> Make the built-in arduino LED flashing every seconds.

My code:
```
#define led 5 //define the led diode pin
const int period = 1000;
int time =0;
int cur_time=0;
void setup() {
  pinMode(led,OUTPUT); //specify the mode of operation of the led pin
}

void loop() {
  cur_time = millis(); // measure the current time
  if(cur_time >= time)
  {
    digitalWrite(led, !digitalRead(led)); // Write a HIGH or a LOW value to the led pin.
    time +=period; 
  }
  
}
```

## Voltage divider

***TASK*** >> You need measure a voltage value from ADT on Arduino. For this task you need two resistors, wires and Arduino. Getting a value can be viewed in ***Serial Monitor***.

Circuit for this task:
```
Circuit
```

My code:
```
int time =0;
int cur_time =0;
const int period = 1000;

void setup() {
 pinMode(13,OUTPUT);
 Serial.begin(9600);
}

void loop() {
  cur_time = millis();
  if(cur_time >= time)
  {
    digitalWrite(13, !digitalRead(LED_BUILTIN));
    time += period;
  }
  int sensorValue = analogRead(A0);
  float voltage = sensorValue * (5.0 / 1024.0);
  Serial.println(voltage);
}
```

## Multitasking

***TASK*** >> Make tasks ***Flashing built-in LED*** and ***Voltage divider*** at same time.

My code:
```
CODE
```

## LCD Display 

***TASK*** >> For given LCD display provide code, that output words or sentences on different position of display. Connect the additional ***LiquidCrystal_I2C.h*** and deal with it. Also read about ***I2C scanner***.

My code:
```
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd (0x3F, 16, 2);

void setup()
{  
  lcd.init();
  lcd.backlight();
  lcd.begin(0,1);
  lcd.print("Hello");
}

void loop()
{
}
```


## Iterruption with the button

***TASK*** >> Read what an interruption is. Make sure that when you press the button, the diode turns off.

Circuit for this task:

My code:
```
void button()
{
  digitalWrite(5,LOW);
}
void setup() {
  pinMode(2, INPUT);
  pinMode(5,OUTPUT);
  digitalWrite(5,HIGH);
  attachInterrupt(0, button, RISING);
}

void loop() 
{
}
```
## Debouncing a button

***TASK*** >> 

* ### **Software method**


* ### **Hardware method**

