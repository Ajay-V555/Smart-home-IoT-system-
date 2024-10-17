# Smart Home Automation with Arduino and GSM

## Project Overview
This project focuses on developing a **Smart Home Automation System** using **Arduino** and a **GSM module**. The system allows remote control of home appliances through SMS commands sent via the GSM module, providing a convenient and efficient way to manage a smart home. The design and simulation were implemented using **Proteus software**, while the code was written and tested in the **Arduino IDE**.

## Features
- Remote control of home appliances via SMS.
- Arduino-based system for easy integration.
- GSM module for wireless communication.
- Designed and simulated in **Proteus software**.
- Code development and testing in **Arduino IDE**.

## Requirements
- **Arduino** -Arduino Uno
- **GSM Module**  SIM900D
- Relays for controlling appliances
- **Proteus** software for simulation
- **Arduino IDE** for programming
- Additional components (resistors, wires, etc.)

## Installation and Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/Ajay-V555/Smart-home-IoT-system.git

2. Open the Proteus files located in the /schematics folder for the simulation.


3. Load the source code from the /src folder into your Arduino IDE.


4. Upload the code to your Arduino board.


5. Test the system by sending SMS commands to control appliances.



## Usage

Send specific SMS commands (e.g., "LIGHT ON", "FAN OFF") to control home appliances remotely.

The system receives the SMS, processes it via the GSM module, and triggers the corresponding relay to switch appliances on or off.


## Simulation

The Proteus simulation allows you to visualize how the system functions before implementing it in a physical setup. You can simulate sending SMS commands and observe the appliance control operations.


## Code

#include <LiquidCrystal.h>
LiquidCrystal lcd(2, 3, 4, 5, 6, 7);
const int fan_pin = 8;
const int bulb_pin = 9;
const int buzzer = 10;
String gsm_read = "";
void RecieveMessage();

void setup()
{
  Serial.begin(9600);
  pinMode(fan_pin, OUTPUT);
  pinMode(bulb_pin, OUTPUT);
  pinMode(buzzer, OUTPUT);
  Serial.println("In Setup ...");
  delay(100);
  lcd.begin(16, 2);
  lcd.print("GSM Base");
  lcd.setCursor(0, 1);  
  lcd.print("Home Automation");
  delay(1000);
  RecieveMessage();
}

void loop()
{
   lcd.clear();
   lcd.print("Waiting for ");
   lcd.setCursor(0, 1);  
   lcd.print("command");
   delay(100);
    while (Serial.available() > 0)
    {
      gsm_read = Serial.readString();
      gsm_read.remove(gsm_read.length() - 1); 
      if (gsm_read == "FAN_ON")
      {
          lcd.clear();
          lcd.print("motor On");
          delay(100);
          digitalWrite(fan_pin, HIGH); 
          delay(100);
      }
      else if (gsm_read == "FAN_OFF")
      {
          lcd.clear();
          lcd.print("motor OFF");
          delay(100);
          digitalWrite(fan_pin, LOW); 
          delay(100);
      }
      else if (gsm_read == "BULB_ON")
      {
          lcd.clear();
          lcd.print("BULB ON");
          delay(100);
          digitalWrite(bulb_pin, HIGH); 
          delay(100);
      }
      else if (gsm_read == "BULB_OFF")
      {
          lcd.clear();
          lcd.print("BULB OFF");
          delay(100);
          digitalWrite(bulb_pin, LOW); 
          delay(100);
      }
      else
      {
        lcd.clear();
        lcd.print("wrong password");
        delay(100);
        digitalWrite(buzzer, HIGH); 
        delay(500);
        digitalWrite(buzzer, LOW); 
        delay(100);
      }
    }
}

void RecieveMessage()
{
  Serial.println("AT+CMGF=1");
  delay(1000);
  Serial.println("AT+CNMI = 2,2,0,0,0");
  delay(1000);
}

## License

This project is licensed under the MIT License.

