# Final Work
````
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
