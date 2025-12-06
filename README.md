# REPORTE DE DHT CON LCD

## Introducción

## Materiales
Simulador WOKWI (https://wokwi.com) :
- Tarjeta ESP32
- Sensor DHT22
- LCD 16x2

## Procedimiento 
1. En el buscador ingresar la página https://wokwi.com

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20010958.png)

2. Seleccionar la opción ``ESP32`` en ambos casos

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20011019.png)
![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20011217.png)

Nos llevará a la siguiente página:

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20010757.png)

3. En la parte de ``sketch.ino`` nos muestra el código anterior que debemos borrar para colocar el nuevo a continuación:
````
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.clear();
  lcd.setCursor(2, 1);
  lcd.print("BIENVENIDOS");
  delay(1500);
  lcd.clear();
  lcd.setCursor(2, 1);
  lcd.print("MODULO 5");
  delay(1500);
  lcd.clear();
  lcd.setCursor(2, 1);
  lcd.print("HELEN XIMENA");
  delay(1500);
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  delay(1500);

  delay(2000);
} 
````
4. En ``Library Manager`` en la opción de ``+`` vamos a buscar las siguientes bibliotecas:
- DHT sensor library for ESPx
- LiquidCrystal I2C

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20203053.png)

5. Para el siguiente paso en la parte de ``Simulation`` en la opción de ``+`` 

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-04%20230350.png)

Vamos a buscar las opciones de: 
- DHT22
- LCD 16x2

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20205947.png)
![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-04%20231406.png)

6. Hacer la conexión del ESP32 con el DHT22 y LCD

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20212454.png)

7. Iniciamos la simulación con el botón ``play (|>)`` y empezará a visualizarse los lectores del sensor

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-04%20230350.png)

8. Una vez que los resultados han sido compilados de manera correcta arrojara los resultados:

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20213606.png)

## Resultados

![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20213540.png)
![]()
![]()
![](https://github.com/ximena01ta/practica-DHT-con-LCD/blob/main/Captura%20de%20pantalla%202025-12-05%20213606.png)
