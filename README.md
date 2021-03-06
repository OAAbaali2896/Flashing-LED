# Flashing LEDs in LPC1768
[![HitCount](http://hits.dwyl.io/OAAbaali2896/Flashing-LED.svg)](http://hits.dwyl.io/OAAbaali2896/Flashing-LED)

<img width="250" alt="Capture" src="https://user-images.githubusercontent.com/40522456/57877843-bedf4f00-77e6-11e9-87cf-9e88fa135c81.PNG">

This project contains both C & ARM Assembly code of 8 LEDs flashing at different pattern and speeds. 

The board manual for LPC1768 can be viewd here: https://github.com/OAAbaali2896

## A - LED Interface
The LEDs display the current bitpattern on the databus. The LPC1768 board has 8 LEDs. A picture is shown below:

<img width="300" alt="LED" src="https://user-images.githubusercontent.com/40522456/58436757-fd9dc080-8094-11e9-8b92-2572c7cca633.PNG">

The board schematic for the 8 LEDs is shown below:

<img width="315" alt="Capture" src="https://user-images.githubusercontent.com/40522456/58436951-d5fb2800-8095-11e9-8544-ab72bcda75ae.PNG">

From this picture:
* We can see the LEDs are connected to **GPIO Port 2** Pins (0 through 7), also called P2.0, P2.1, …, P2.7.
* A high voltage will turn the LEDs **ON** and a low voltage will turn them **OFF**, so we will write a **1** to turn each LED on to the corresponding pin.
* P2.7 corresponds to LD4 (**leftmost**), P2.0 corresponds to LD11 (**rightmost**)

## B - Switches/Joystick to control the Pattern & Speed
### B(1) - Switches
The LandTiger LPC17XX board features 4 switches: Key1 (SW4), Key2 (SW3), INT0 (SW2), RESET (SW1).









A picture and the functionality of each switche is shown below:

<img width="350" alt="LED" src="https://user-images.githubusercontent.com/40522456/58438644-d3043580-809d-11e9-8a11-ddfd6ace8df8.PNG">


| **Key type** | **Description** | **Comment** |
| :--- |:---|:--- |
|Key1|Connected to INT1 (P2.11), Active Low, Pull-Up R of 10K installed.|SW4|
|Key 2|Connected to INT2 (P2.12), Active Low, Pull-Up R of 10K installed.|SW3, Secondary function to enter the USB ISP mode.|
|INT0|Connected to INT0 (P2.10) when JP5 is inserted. Active Low, Pull-Up R of 10K installed.|SW2, Secondary function to enter the COM1 ISP mode.|
| RESET|Manual Reset|SW1|

### B(2) - Joystick
The LandTiger LPC17XX board features a 5 way digital joystick (SW5). Each direction (up, down, left, right) and the Select function are connected to a dedicated digital input pin on the LPC17XX. Multiple keys can be pressed at the same time (e.g. up and right). 
A picture of the joystick is shown below:

<img width="350" alt="LED" src="https://user-images.githubusercontent.com/40522456/58441063-e66acd00-80ac-11e9-8581-baf90a151b80.PNG">

The board schematic for the joystick is shown below:

<img width="390" alt="LED" src="https://user-images.githubusercontent.com/40522456/58440915-cedf1480-80ab-11e9-8137-6973782bd999.PNG">

From the picture:
* We can see the 5 pins are connected to **GPIO Port 1**.
* The input pins are **active low** when a key is pressed. If a button is pressed, we will read a **0** value at the pin.

A table of the 5 pins is shown below:

| **IO Pin** | **Description** |
| :--- |:---|
|P1.25|Select (Active Low)|
|P1.26|Down (Active Low)|
|P1.27|Left (Active Low)|
|P1.28|Right (Active Low)|
|P1.29|Up (Active Low)|

