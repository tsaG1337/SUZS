# SÜZS
The **S**pannungs**Ü**berwachungs**Z**entral**S**teuerungsplatine to control your 3D Printer.

The SUZS gives you control over your 3D Printer instantly without the need to power your Raspberry or your MCU, either via pushbuttons or over network.
Need to switch on the lights to watch your print via webcam? No problem!
This is currently a WIP. Although first prototypes are up and running, there might be some things that will be changed/added in the future.

<p align="center">
![Raspberry Assembly](/images/Raspberry_assembly.JPG)
</p>

## Main Features:

* Implementation into Home-Assist
  * Control the Power of your printer over the net or with your favourite voice assistant (Siri, Alexa etc.)
* Fundamental 3D Printer Control.
  * Support for a Print Chamber heater and Fan combination.
  * Safely Power your Raspberry Pi with the touch of a button. Regardless of whether its the physical button on your printer itself, or over the WEB-IDE.
  * Once you are done, let the SUZS send the Shutdown command to safely shut down your Pi and cut the power (hey, you are doing something good for the environment!).
  * Raspberry Input Voltage Check.
  * Raspberry Pi UART to Control Board Header (no need to use the bulky USB cable anymore)
* W2812B / Neopixel Levelshifter to set the special mood for you and your printer including WLED (The ESPHome WLED implementation is currently WIP)..
* LED control can be bridged from Klipper control to match the color theme your printing stats (TBD)
* Control for external/electronics compartment Fan / Pump (including Power PWM or PWM Signal). Normally supplied by 5V, optionally up to 25V.
* Air Temp Sensor
* Interface for 2 RGB Buttons (Mainly used for Power and Lighting)
* Emergency Off Button
* Wattmeter input: See how much power you have drawn during printing by connecting an external power counter.

## Hardware

<p align="center">
![SUZS PCB](/images/PCB.PNG)
</p>

The SÜZS is designed as a HAT/Piggyboard for a Raspberry Pi. The controller used is an ESP32 NodeMCU. 
There are several version of this Board on the market, one has to check the Pinout to find a matching one.
This Board has 19x2 Pins to connect to the SÜZS.

<p align="center">
<img src="/images/nodemcu_esp32-full.jpg" width="60%">
</p>


## Software

The Firmware will be based on the ESPHome Project including some realtime GPIO checks for Power Monitoring and Raspberry Status control.
You are able to Monitor the basics via Home-Assist and also hit the E-Stop button from the warmth of your chair.

<p align="center">
<img src="/images/home_assist.png" width="60%">
</p>

Pick your favourite Color in the web interface to set the theme for your printer. 
The color picked for the printing Chamber lighting, sets the theme for all RGB LEDs connected. 


<p align="center">
<img src="/images/HAS_Color_picker.png" width="60%">
</p>

## Changelog:

### Hardware Rev 0.2

- Added 2 NTC Sensors (Chamber heater output and Chamber heater)
- Discrete RGB Outputs (Power and Light Button) are now designed for common Cathode LEDs
- Added Filtering capacitors to the 5V Rail (the RGB Strip created some noise that lead to a reboot of the ESP)
- Added Wattmeter Pulse input.
- Added Protection diode for AC mains Relais (actually not needed as it is controlled on the high side, but you never know...)
- ~~removed external Pullups for the Switches and enabled the ESP internal ones.~~
- removed the RGB connection between RPi and ESP for the NTC and Wattmeter (RGB shall be handled via the I2C connection lateron)
