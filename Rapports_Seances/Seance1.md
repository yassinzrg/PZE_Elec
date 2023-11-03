#include <OneWire.h>
#include <DallasTemperature.h>

// UTILISER PIN 15 16 17 POUR RELEVER LA TEMPERATURE

// GPIOs where the DS18B20 sensors are connected to
const int oneWireBus1 = 15; // Connect the first DS18B20 sensor to pin 15
const int oneWireBus2 = 16; // Connect the second DS18B20 sensor to pin 16
const int oneWireBus3=17; // Connect the second DS18B20 sensor to pin 17
//Setup oneWire instances for communication with the sensors
OneWire oneWire1(oneWireBus1);
OneWire oneWire2(oneWireBus2);
OneWire oneWire3(oneWireBus3);
// Pass oneWire references to Dallas Temperature sensors
DallasTemperature sensors1(&oneWire1);
DallasTemperature sensors2(&oneWire2);
DallasTemperature sensors3(&oneWire3);


void setup() {
  // Start the Serial Monitor
  Serial.begin(250000);

  // Start the DS18B20 sensors
  sensors1.begin();
  sensors2.begin();
  sensors3.begin();
}

void loop() {
  // Request temperature readings for all sensors
  sensors1.requestTemperatures();
  sensors2.requestTemperatures();
  sensors3.requestTemperatures();

  // Read temperatures from all sensors
  float temperatureC1 = sensors1.getTempCByIndex(0);
  float temperatureC2 = sensors2.getTempCByIndex(0);
  float temperatureC3 = sensors3.getTempCByIndex(0);


  float temperatureF1 = sensors1.getTempFByIndex(0);
  float temperatureF2 = sensors2.getTempFByIndex(0);
  float temperatureF3 = sensors3.getTempFByIndex(0);
  // Print temperature readings for the first sensor
  Serial.print("Sensor 1: ");
  Serial.print(temperatureC1);
  Serial.print("°C");
  Serial.print(" / ");
  Serial.print(temperatureF1);
  Serial.println("°F");

  // Print temperature readings for the second sensor
  
  Serial.print("Sensor 2: ");
  Serial.print(temperatureC2);
  Serial.print("°C");
  Serial.print(" / ");
  Serial.print(temperatureF2);
  Serial.println("°F");
  // Print temperature readings for the third sensor
  Serial.print("Sensor 3: ");
  Serial.print(temperatureC3);
  Serial.print("°C");
  Serial.print(" / ");
  Serial.print(temperatureF3);
  Serial.println("°F");
  
  delay(1000);
}
