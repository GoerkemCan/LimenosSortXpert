RWTH - CONSTRUCTION ROBOTICS - RESEARCH DRIVEN PROJECT - LIMENOS SORTXPERT
---------------------------------------------------------------------------------------------------------------------------------------


This repository contains the code for a research-driven project related to Construction Robotics. The project is a collaborative effort by Görkem Can Ertemli, Gizem Erekinci Altan, and Georgi Tsakov.

You can find the demonstartion video of the working prototype through this [link](https://youtu.be/UH-Ukme-pDA)


Inclusions / Libraries
---------------------------------------------------------------------------------------------------------------------------------------


This project relies on the following libraries:

AccelStepper: Library for controlling stepper motors. \
ArduinoJson: Library for handling JSON data.\
EspMQTTClient: Library for MQTT communication with an ESP8266-based device.\
SPI: Arduino SPI library.\
Wire: Arduino I2C library.\
Adafruit_GFX: Graphics library for Adafruit displays.\
Adafruit_SSD1306: Library for controlling SSD1306 OLED displays.

Make sure to install these libraries before running the code through the ArduinoIDE

Additionally, the project uses the NodeMCU / ESP8266 board. If you are using this board, you need to manually add it to the Arduino IDE. For instructions on how to accomplish this, please refer to this short tutorial: [Link to the tutorial](https://randomnerdtutorials.com/how-to-install-esp8266-board-arduino-ide/)


Wifi and MQTT Data
---------------------------------------------------------------------------------------------------------------------------------------


Before uploading the code to your device, update the following variables in the code to match your Wifi and MQTT setup:

WIFI_NAME: Set this to your Wifi name (SSID).\
WIFI_PASSWORD: Set this to your Wifi password.\
MQTT_BROKER: Set this to the IP address or hostname of your MQTT broker server.\
CLIENT_NAME: Set this to a unique name that identifies your device on the MQTT network.\
MQTT_PORT: (Optional) Set this to the MQTT port number. The default is 1883 and can be omitted if you are using the standard port.


Defs
---------------------------------------------------------------------------------------------------------------------------------------


This section contains various pin definitions used in the project:

DIR_PIN: Pin for controlling the direction of the stepper motor.\
STEP_PIN: Pin for sending step signals to the stepper motor.\
SWITCH_PIN: Pin for the limit switch.\
YLED_PIN: Pin for the yellow LED.\
GLED_PIN: Pin for the green LED.\
RLED_PIN: Pin for the red LED.\
SCREEN_WIDTH: Width of the connected OLED display in pixels.\
SCREEN_HEIGHT: Height of the connected OLED display in pixels.\
OLED_RESET: Reset pin for the OLED display (set to -1 if sharing Arduino reset pin).\
SCREEN_ADDRESS: Address of the OLED display (0x3C for 128x32, 0x3D for 128x64).

Logo Definitions
---------------------------------------------------------------------------------------------------------------------------------------


The code includes bitmap definitions for our logo and its animation on the OLED display. The logo is defined as arrays of hexadecimal values representing the pixels of the images.


Functions
---------------------------------------------------------------------------------------------------------------------------------------

Function: void setup()

Definition:\
This function is called once when the microcontroller (NodeMCU/ESP8266) starts up. It is used to initialize various settings and configurations for the project.

Function: void loop()

Definition:\
This function is the main program loop that runs continuously after the setup() function has executed. It contains the core logic of the project and handles the real-time operation of the system.

Function: void moveStepperMotor(int steps, bool direction)

Definition:\
This function is responsible for controlling the stepper motor's movement. It takes two parameters:

steps: The number of steps the motor should move.
direction: A boolean value indicating the direction of the motor (true for forward, false for backward).
Function: void checkLimitSwitch()

Definition:\
This function checks the status of the limit switch. When the limit switch is triggered, it indicates that the motor has reached its physical limit, and this function takes appropriate actions based on the project's requirements.

Function: void displayLogoAnimation()

Definition:\
This function displays an animation on the OLED display using the defined bitmap logos. It creates a visual representation of the project's identity or status.

Function: void sendDataToMQTTBroker(String topic, String data)

Definition:\
This function is responsible for sending data to the MQTT broker. It takes two parameters:

topic: The MQTT topic to which the data should be published.
data: The actual data to be sent.
Function: void receiveDataFromMQTTBroker(String topic, String data)

Definition:\
This function handles incoming data from the MQTT broker. It takes two parameters:

topic: The MQTT topic from which the data is received.
data: The received data.


Setup and Assembly of the Prototype:
---------------------------------------------------------------------------------------------------------------------------------------


This step in the prototype development involves wiring all the components together to make the system operational with the provided code. The main components include the ESP8266 (NodeMCU) board, the A4988 stepper motor driver, the limit switch, LEDs, and the OLED display. To facilitate assembly, a breadboard is used to house the NodeMCU board, and the other elements are connected to their respective locations.

ESP8266 (NodeMCU) and A4988 Driver:\
Pin D6 on the NodeMCU is connected to the DIR pin on the A4988 driver.\
Pin D5 on the NodeMCU is connected to the STEP pin on the A4988 driver.\
The GND pin of the driver is connected to the GND of the NodeMCU.\
The 5V pin of the driver is connected to the Vin pin of the NodeMCU.\
Caution: Before proceeding, ensure that the power supply is not connected to electricity to avoid any accidents. After this, a 9V power supply is connected to the COM pin, and the GND of the power supply is connected to the GND of the NodeMCU. Care should be taken to prevent the driver from burning, which can happen if the power supply is disconnected abruptly.

Stepper Motor:\
Connect the motor to the A4988 driver using the cable provided with the motor.

Limit Switch:\
The limit switch serves as a homing stop to ensure the system takes the same starting position and maintains a consistent 0 position during every startup.\
Connect the normally open (NO) terminal of the limit switch to pin D7 of the NodeMCU.\
Connect the GND terminal of the limit switch to GND on the NodeMCU.

LEDs:\
Connect three LEDs of different colors to the NodeMCU for visual feedback.\
The yellow LED is connected to pin D0.\
The green LED is connected to pin D3.\
The red LED is connected to pin D4.

OLED Display:\
An I2C device is used for the OLED display for simplicity and reduced wiring.\
Connect the OLED display as follows:\
Connect the Vin pin to 5V.\
Connect GND to GND.\
Connect the SDA pin to D2.\
Connect the SCK pin to D1.\
No additional declaration is needed for the SDA and SCK pins since the Wire library specifies their connections.
Note: For more information about the declaration for SD1306 displays, please refer to this link: https://randomnerdtutorials.com/guide-for-oled-display-with-arduino/.

Power Supply:\
The prototype can be connected to a power supply using a capacitor or by connecting it to a computer for power supply.\
If using a capacitor, exercise caution to avoid burning the driver when disconnecting the power supply.\
If using the computer for power, disconnect the power supply first and then disconnect from the computer to prevent any damage.\
Once the code is uploaded to the NodeMCU, the prototype is ready for operation. It requires a Wi-Fi connection and an MQTT topic for communication. Users can create these before proceeding and set up a Node-RED UI or other interfaces to test the system. The code itself utilizes MQTT commands in JSON format, with four rotation configurations (L, Z, U, I) and their corresponding values. By creating the necessary MQTT topics and setting up the Wi-Fi connection, users can start the system and observe its automated rebar bending and sorting process.

For more detailed information about the A4988 driver and how to configure it, please refer to this link: https://lastminuteengineers.com/a4988-stepper-motor-driver-arduino-tutorial/.
