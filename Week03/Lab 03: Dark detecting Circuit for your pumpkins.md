# Lab 03: Dark detecting Circuit for your pumpkins
#### Making a dark detecting LED (From Circuit diagram to breadboard) Build this project to better understand transistors

<img width="785" alt="屏幕快照 2021-11-30 上午12 06 39" src="https://user-images.githubusercontent.com/91987208/143976170-bbef8d73-5d66-444a-af21-e2cac0820e90.png">

## Code

```
int led = 9;           // the PWM pin the LED is attached to
int brightness = 0;    // how bright the LED is
int fadeAmount = 5;    // how many points to fade the LED by

// the setup routine runs once when you press reset:
void setup() {
  // declare pin 9 to be an output:
  pinMode(led, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // set the brightness of pin 9:
  analogWrite(led, brightness);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  // wait for 30 milliseconds to see the dimming effect
  delay(30);
}
```
## Thinkercad
https://www.tinkercad.com/things/f8gop2wX1sR-fade/editel
