#define CUSTOM_SETTINGS
#define INCLUDE_GAMEPAD_MODULE
#define motin1 26
#define motin2 25
#define motin3 17
#define motin4 16
#define analog1 2
#define analog2 4

#define blinker1 23
#define blinker2 5
#define predni_svetlo 18
#define zadni_svetlo 19

#include <DabbleESP32.h>
#include <analogWrite.h>
#include "Arduino.h"


bool onoffb1 = 0; //logická hodnota blinkru
bool onoffb2 = 0; //logická hodnota blinkru
bool onoff = 0; //logická hodnota předních a zadních světel



void setup() {
  
  Serial.begin(115200);      
  Dabble.begin("Auticko");      
  pinMode(motin1, OUTPUT);
  pinMode(motin2, OUTPUT);
  pinMode(motin3, OUTPUT);
  pinMode(motin4, OUTPUT);    
  pinMode(analog1, OUTPUT);
  pinMode(analog2, OUTPUT);

  pinMode(blinker1, OUTPUT);
  pinMode(blinker2, OUTPUT);

  pinMode(predni_svetlo, OUTPUT);
  pinMode(zadni_svetlo, OUTPUT);
  
 
}



void loop() {
    drive();
  
    Dabble.processInput();
    bool g = GamePad.isStartPressed();
    bool h = GamePad.isTrianglePressed();
    bool i = GamePad.isCrossPressed();
    
    //"tlačítko" na vypínání a zapínání blinkru
    if (h){
      if(onoffb1){
      onoffb1 = 0;
      }else{
      onoffb1 = 1;
      }
    }
    if(onoffb1){
      lights1();
      }
    //"tlačítko" na vypínání a zapínání blinkru
   if (i){
      if(onoffb2){
      onoffb2 = 0;
      }else{
      onoffb2 = 1;
      }
    }
    if(onoffb1){
      lights2();
      } 
    //"tlačítko" na vypínání a zapínání předních azadních světel
     if (g){
      if(onoff){
      Serial.println("Světla ON");
      analogWrite(predni_svetlo, 1024);
      analogWrite(zadni_svetlo, 1024); 
      onoff = 0;
      }else{
      Serial.println("Světla Off");
      analogWrite(predni_svetlo, 0);
      analogWrite(zadni_svetlo, 0);
      onoff = 1;
      }
    }
       
    
    
} 

void lights1(){
  
  static unsigned long lastTime = 0;
  const long interval = 3000;
  static bool state = 0;

  unsigned long now = millis();

  if ( now - lastTime > interval && state == 0) {
    state = 1;
    lastTime = now;
    analogWrite(blinker1, 1024);
    Serial.println("BLINK up 1");
    
  }

  if ( now - lastTime > interval && state == 1) {
    state = 0;
    lastTime = now;
    analogWrite(blinker1, 0);
    Serial.println("BLINK down 1");
  }
  
  
}

void lights2(){
  
  static unsigned long lastTime = 0;
  const long interval = 3000;
  static bool state = 0;

  unsigned long now = millis();

  if ( now - lastTime > interval && state == 0) {
    state = 1;
    lastTime = now;
    analogWrite(blinker2, 1024);
    Serial.println("BLINK up 2");
    
  }

  if ( now - lastTime > interval && state == 1) {
    state = 0;
    lastTime = now;
    analogWrite(blinker2, 0);
    Serial.println("BLINK down 2");
  }
  
  
}



void drive() {
  Dabble.processInput();             
  bool a = GamePad.isUpPressed();
  bool b = GamePad.isDownPressed();
  bool c = GamePad.isLeftPressed();
  bool d = GamePad.isRightPressed();
  bool e = GamePad.isSquarePressed();
  bool f = GamePad.isCirclePressed();
  
 
   
 
   
          if (a || b || c || d || e || f)
          {
            if (a)
            {
              analogWrite(motin1, 1024);
              analogWrite(motin2, 0);
              analogWrite(motin3, 1024);
              analogWrite(motin4, 0);
          
              analogWrite(analog1, 1024);
              analogWrite(analog2, 1024);
          
              Serial.println("dopředu");
              
            }
          
            if (b)
            {
              analogWrite(motin1, 0);
              analogWrite(motin2, 1024);
              analogWrite(motin3, 0);
              analogWrite(motin4, 1024);
             
              analogWrite(analog1, 1024);
              analogWrite(analog2, 1024);
          
              Serial.println("dozadu");
          
            }
          
            if (c)
            {
              analogWrite(motin1, 1024);
              analogWrite(motin2, 0);
              analogWrite(motin3, 1024);
              analogWrite(motin4, 0);
              
              analogWrite(analog1, 0);
              analogWrite(analog2, 1024);
          
              Serial.println("doleva");
              
              
            }
          
            if (d)
            {
              analogWrite(motin1, 1024);
              analogWrite(motin2, 0);
              analogWrite(motin3, 1024);
              analogWrite(motin4, 0);
          
              analogWrite(analog1, 1024);
              analogWrite(analog2, 0);
          
              Serial.println("doprava");
              
            }
            if (e)
            {
              analogWrite(motin1, 0);
              analogWrite(motin2, 1024);
              analogWrite(motin3, 0);
              analogWrite(motin4, 1024);
          
              analogWrite(analog1, 0);
              analogWrite(analog2, 1024);
              
              Serial.println("dozadu doleva");
          
            }
            if (f)
            {
              analogWrite(motin1, 0);
              analogWrite(motin2, 1024);
              analogWrite(motin3, 0);
              analogWrite(motin4, 1024);
          
              analogWrite(analog1, 1024);
              analogWrite(analog2, 0);
          
              Serial.println("dozadu doprava");
            }
            
          
            
          }
          else
          {
            analogWrite(motin1, 0);
            analogWrite(motin2, 0);
            analogWrite(motin3, 0);
            analogWrite(motin4, 0);
          
            analogWrite(analog1, 0);
            analogWrite(analog2, 0);
            
          }

  }



