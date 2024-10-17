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


## License

This project is licensed under the MIT License.

