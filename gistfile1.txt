#include "DHT.h"

DHT dht;
const int buzzer = 16; 

void setup() {
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
  Serial.println();
  Serial.println("Status\tHumidity (%)\tTemperature (C)\t(F)");

  dht.setup(4);
}

void loop() {
  delay(dht.getMinimumSamplingPeriod());

  float humidity = dht.getHumidity();
  float temperature = dht.getTemperature();

  //Serial.print(dht.getStatusString());
  //Serial.print("\t");
  Serial.print("Vlhkosť v percentách: ");
  Serial.print(humidity, 1);
  Serial.print("%");
  Serial.print("\t\t");
  Serial.print("Teplota v stupňoch Celzius: ");
  Serial.print(temperature, 1);
  Serial.print("℃");
  Serial.print("\t\t");
  Serial.print("Teplota v stupňoch Fahrenheit: ");
  Serial.print(dht.toFahrenheit(temperature), 1);
  Serial.println("℉");

  if (temperature >= 27) {
    tone(buzzer, 4000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 4000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 4000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 4000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
  } else if (temperature >= 26) {
    tone(buzzer, 3000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 3000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 3000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
  } else if (temperature >= 25) {
    tone(buzzer, 2000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    tone(buzzer, 2000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
    } else if (temperature >= 24) {
    tone(buzzer, 1000);  
    delay(100);          
    noTone(buzzer);      
    delay(100);          
}
}
