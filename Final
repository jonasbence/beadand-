#include "TM1637.h"

#include <DHT.h> 
#define DHTPIN A3
#define DHTTYPE DHT11   

DHT dht(DHTPIN, DHTTYPE); 
 
#define CLK 4     
#define DIO 5
 
TM1637 tm1637(CLK,DIO);

 
int fenyerzekelo = A2;
int motor = 6;
int gomb = A5;
int nedvesseg = A1;
void setup(){
  pinMode(gomb,INPUT_PULLUP);
  pinMode(fenyerzekelo,INPUT);
  pinMode(nedvesseg,INPUT);
  pinMode(motor,OUTPUT);
  
  tm1637.init();
  tm1637.set(BRIGHT_DARKEST); 
 
  delay(1500);
  dht.begin();   
  
}

void loop(){
  
   int temp = dht.readTemperature();  
 
 int digitoneT = temp / 10;
 int digittwoT = temp % 10;

    tm1637.display(0,digitoneT); 
    tm1637.display(1,digittwoT);
    tm1637.display(2,19); // fok
    tm1637.display(3,12);  // C a végén

// ha lenyomon a gombot vagy megfelelő hpmérséklet és megfelelő sötétség és megfelelő szárazság mellet locsól
 if((digitalRead(gomb)==HIGH) || (temp>15 && temp<25) && (analogRead(nedvesseg)<200) && (analogRead(fenyerzekelo)<200) ){
  digitalWrite(motor, HIGH);
  delay(2000);
 }else{
  digitalWrite(motor, LOW);
  delay(1000);
 }
}
