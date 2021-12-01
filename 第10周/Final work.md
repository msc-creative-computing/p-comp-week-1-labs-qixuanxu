# Final Work
### 'Collapse'
<img width="853" alt="封面" src="https://user-images.githubusercontent.com/91987208/144283079-75876374-46ac-4084-8eaf-7c851a7407fe.png">

<img width="1033" alt="屏幕快照 2021-12-01 下午5 35 19" src="https://user-images.githubusercontent.com/91987208/144284620-3dcec2de-85b2-49a7-9e06-21eaf9e608fe.png">

![WechatIMG191](https://user-images.githubusercontent.com/91987208/144284671-e018f851-66ef-415a-a181-40a55157e662.jpeg)

<img width="374" alt="屏幕快照 2021-12-01 下午5 36 26" src="https://user-images.githubusercontent.com/91987208/144284786-8c1aeb97-377c-46b5-a8c7-e6d71978dbad.png">
<img width="1108" alt="屏幕快照 2021-12-01 下午5 37 19" src="https://user-images.githubusercontent.com/91987208/144284934-08366185-abb4-48b3-b4bc-7cca5727522e.png">

## Vedio Link

https://youtu.be/TIn0SUcPTXc

## Code

```
#include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
const char *words[] = {"Star","to","spaces","vast","and","far","What","matters","darkness","the","star","Roll","calmly","on","let","time","go",
"by","sorrows","pass","nations","die","red","would","but","dim","light","That","distant","worlds","will","gladly","sight","To"
,"the","one","law","be","pure","bright"};
const int len = sizeof(words) / sizeof(words[0]);
int key = 7;
int led = 6;
int rot_pin = A1;
int n1;
int n2;
int n3;
int n4;
int flag = 0;
void setup() {
  lcd.begin(16, 2);
  randomSeed(A1);
  pinMode(led,OUTPUT);
  pinMode(key,INPUT_PULLUP);
  digitalWrite(led,HIGH);
}

void loop() {
  
  key_scan();
  if(analogRead(rot_pin)>=0 && analogRead(rot_pin)<200)
  {
    draw_words();
    while(analogRead(rot_pin)>=0 && analogRead(rot_pin)<200)
    {
      key_scan();
      if(flag == 1)
        break;
    
    }
  }
  else if(analogRead(rot_pin)>=200 && analogRead(rot_pin)<400)
  {
    draw_words();
    while(analogRead(rot_pin)>=200 && analogRead(rot_pin)<400)
    {
      key_scan();
      if(flag == 1)
        break;
    }
  }
  else if(analogRead(rot_pin)>=400 && analogRead(rot_pin)<600)
  {
    draw_words();
    while(analogRead(rot_pin)>=400 && analogRead(rot_pin)<600)
    {
      key_scan();
      if(flag == 1)
        break;    
    }
  }
  else if(analogRead(rot_pin)>=600 && analogRead(rot_pin)<800)
  {
    draw_words();
    while(analogRead(rot_pin)>=600 && analogRead(rot_pin)<800)
    {
      key_scan();
      if(flag == 1)
        break;    
    }
  }
  else if(analogRead(rot_pin)>=800)
  {
    draw_words();
    while(analogRead(rot_pin)>=800)
    {
      key_scan();
      if(flag == 1)
        break;    
    }
  }
  
  if(flag == 1)
  {
    lcd.clear();
    digitalWrite(led,LOW);
  }
}


void draw_words()
{
    while(1)
    {
      n1 = random(len-1);
      n2 = random(len-1);
      n3 = random(len-1);
      n4 = random(len-1);
      if(n1!=n2 && n1!=n3 && n1!=n4 && n2!=n3 && n2!=n4 && n3!=n4)
      {
        lcd.clear();
        break;
      }
    }
  	key_scan();
  	if(flag == 0)
    {
      digitalWrite(led,HIGH);
      lcd.setCursor(0,0);
      lcd.print(words[n1]);
      lcd.setCursor(8,0);
      lcd.print(words[n2]);
      lcd.setCursor(0,1);
      lcd.print(words[n3]);
      lcd.setCursor(8,1);
      lcd.print(words[n4]);
    }

	
}

void key_scan()
{
 if(digitalRead(key) == LOW)
 {
  delay(15);
   if(digitalRead(key) == LOW)
   {
    flag = !flag; 
     while(digitalRead(key) == LOW){}
   }
 }
}

```
