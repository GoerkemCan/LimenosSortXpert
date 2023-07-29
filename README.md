---------------------------------------------------------------------------------------------------------------------------------------
**RWTH - CONSTRUCTION ROBOTICS - RESEARCH DRIVEN PROJECT - LIMENOS SORTXPERT **
---------------------------------------------------------------------------------------------------------------------------------------


This repository contains the code for a research-driven project related to Construction Robotics. The project is a collaborative effort by Görkem Can Ertemli, Gizem Erekinci Altan, and Georgi Tsakov.


---------------------------------------------------------------------------------------------------------------------------------------
**Inclusions / Libraries**
---------------------------------------------------------------------------------------------------------------------------------------


This project relies on the following libraries:

AccelStepper: Library for controlling stepper motors.
ArduinoJson: Library for handling JSON data.
EspMQTTClient: Library for MQTT communication with an ESP8266-based device.
SPI: Arduino SPI library.
Wire: Arduino I2C library.
Adafruit_GFX: Graphics library for Adafruit displays.
Adafruit_SSD1306: Library for controlling SSD1306 OLED displays.
Make sure to install these libraries before running the code through the ArduinoIDE

Additionally, the project uses the NodeMCU / ESP8266 board. If you are using this board, you need to manually add it to the Arduino IDE. For instructions on how to accomplish this, please refer to this short tutorial: [Link to the tutorial](https://randomnerdtutorials.com/how-to-install-esp8266-board-arduino-ide/)

---------------------------------------------------------------------------------------------------------------------------------------
**Wifi and MQTT Data**
---------------------------------------------------------------------------------------------------------------------------------------


Before uploading the code to your device, update the following variables in the code to match your Wifi and MQTT setup:

WIFI_NAME: Set this to your Wifi name (SSID).
WIFI_PASSWORD: Set this to your Wifi password.
MQTT_BROKER: Set this to the IP address or hostname of your MQTT broker server.
CLIENT_NAME: Set this to a unique name that identifies your device on the MQTT network.
MQTT_PORT: (Optional) Set this to the MQTT port number. The default is 1883 and can be omitted if you are using the standard port.


---------------------------------------------------------------------------------------------------------------------------------------
**Defs**
---------------------------------------------------------------------------------------------------------------------------------------


This section contains various pin definitions used in the project:

DIR_PIN: Pin for controlling the direction of the stepper motor.
STEP_PIN: Pin for sending step signals to the stepper motor.
SWITCH_PIN: Pin for the limit switch.
YLED_PIN: Pin for the yellow LED.
GLED_PIN: Pin for the green LED.
RLED_PIN: Pin for the red LED.
SCREEN_WIDTH: Width of the connected OLED display in pixels.
SCREEN_HEIGHT: Height of the connected OLED display in pixels.
OLED_RESET: Reset pin for the OLED display (set to -1 if sharing Arduino reset pin).
SCREEN_ADDRESS: Address of the OLED display (0x3C for 128x32, 0x3D for 128x64).

---------------------------------------------------------------------------------------------------------------------------------------
**Logo Definitions**
---------------------------------------------------------------------------------------------------------------------------------------


The code includes bitmap definitions for our logo and its animation on the OLED display. The logo is defined as arrays of hexadecimal values representing the pixels of the images.

