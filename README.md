# SÜZS
The **S**pannungs**Ü**berwachungs**Z**entral**S**teuerungsplatine to control your 3D Printer.

This Board aims to provide a lowe Level control for your 3D Printer. You can connect several Buttons to Turn On/OFF your main Power Supply or the Raspberry Pi.


![ESP32 NODE-MCU](/images/PCB-3D.PNG)

##The Main Features are:

* Raspberry Pi Power Control. 
  * Safely Power your Raspberry Pi with the touch of a button. One Press Powers it On, another Press sends the Shutdown command to savely shut down your Pi.
  * Raspberry Input Voltage Check.
  * Raspberry Pi UART to Control Board Header (no need to use the bulky USB cable anymore)
* WLED Implementation to control the Power of your Printer via Smart Home (Alexa, Google Home or Apple Homekit)
* W2812B / Neopixel Levelshifter to set the special mood for you and your printer..
* LED controll can be bridged from Klipper control.
* Control for external/electronics Bay Fan / Pump (including Power PWM or PWM Signal). Normally supplied by 5V, optionally up to 25V possible.
* Air Temp Sensor
* Interface for 2 RGB Buttons (Mainly used for Power and Lighting)
* Emergency Off Button

##Hardware

![ESP32 NODE-MCU](/images/PCB.jpg)

The SÜZS is designed as a HAT/Piggyboard for a Raspberry Pi. The controller used is an ESP32 NodeMCU. 
There are several version of this Board on the market, one has to check the Pinout to find a matching one.
This Board has 19x2 Pins to connect to the SÜZS.

![ESP32 NODE-MCU](/images/nodemcu_esp32-full.jpg)


## Firmware!

The Firmware will be based on the WLED Project including some realtime GPIO checks for Power Monitoring and Raspberry Status control (TBD).