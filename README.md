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
    digitalWrite(led, !digitalRead(led)); // write a HIGH or a LOW value to the led pin
    time +=period; 
  }
  
}
```

## Voltage divider

***TASK*** >> Use two resistors to make a voltage divider. Measure voltage after the first resistor. Getting a value can be viewed in ***Serial Monitor***.

Circuit for this task:
![alt text](https://github.com/Yehorich02/Arduino-Basic-Tasks/blob/main/LED_connection.png)

Program code:
```
void setup() {
 Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(A0);
  float voltage = sensorValue * (5.0 / 1024.0);
  Serial.println(voltage);
}
```

## Multitasking

***TASK*** >> Make tasks ***Flashing built-in LED*** and ***Voltage divider*** at same time.

Program code:
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
    digitalWrite(13, !digitalRead(LED_BUILTIN)); //write a HIGH or a LOW value to the led pin
    time += period;
  }
  int sensorValue = analogRead(A0);
  float voltage = sensorValue * (5.0 / 1024.0);
  Serial.println(voltage);
}
```

## LCD Display 

***TASK*** >> For given LCD display provide code, that output words or sentences on different position of display. Connect the additional ***LiquidCrystal_I2C.h*** and deal with it. Also read about ***I2C scanner***.

Circuit for this task:
![alt text](https://github.com/Yehorich02/Arduino-Basic-Tasks/blob/main/LCD_I2C.png)

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
![alt text](https://github.com/Yehorich02/Arduino-Basic-Tasks/blob/main/Interrupt_task.png)

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

***TASK*** >> Using a software or hardware method to improve the operation of button.

* ### **Software method**
Circuit for this method:

![alt text](https://github.com/Yehorich02/Arduino-Basic-Tasks/blob/main/LED_with_button.png)

Program code:
```
```


* ### **Hardware method**
Circuit for this method:

![alt text](https://github.com/Yehorich02/Arduino-Basic-Tasks/blob/main/LED_with_button_and_capacitor.png)

Program code:
```
#define LED_PIN 8 // define the led pin
#define BUTTON_PIN 5 // define the button pin

byte lastButtonState = LOW; // A variable that stores the last button status
byte ledState = LOW; // A variable that stores the LED status

void setup() {
  Serial.begin(9600);
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT);
}
void loop() {
  byte buttonState = digitalRead(BUTTON_PIN);
  Serial.println(buttonState);
  if (buttonState != lastButtonState) {
    lastButtonState = buttonState;
    if (buttonState == LOW) {
      if(ledState == HIGH)
      {
        ledState = LOW;
      }
      else 
      {
        ledState = HIGH;
      }
      digitalWrite(LED_PIN, ledState);
    }
  }
}
```

## How connect 