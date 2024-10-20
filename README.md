# Making-of-a-Arduino-Based-Component-Tester
A minimal, powerful, robust tool for electronics component measurement with auto component detect function.
Full project details can be found on: https://www.hackster.io/sainisagar7294/making-of-a-arduino-based-component-tester-9a8206

Component tester is an essential tool for electronics component value measurement. Here we have one DIY version using Arduino’s chip made by many other hobbyists in the past. Today we will build one version with a better PCB design keeping a minimal version in mind with a combination of SMT and TH components. The code is open source and can be found on the web, some modifications are made to make it work with a 16x2 LCD panel. Moreover the input output pinout has an external PCB resistor divider which is used to interpret the values by ADC by enabling its automatic component detection. Using a suitable resistor divider network ensures accurate value of most of the components.

![My Video](https://github.com/user-attachments/assets/b8ae5170-4164-4c63-9918-196c21350a3e)

The function for different component measurement and detection is given in the code section; separate header files can be seen in the Arduino code library for each component in order to calibrate it properly according to your own circuit. Here I made a PCB using the below given circuit and the code works well for it. Code for this project can be downloaded from here. If you want to know more about the tester working and principle then refer to its 100-page manual. Which has all info about modes, screen types, microcontrollers and software.
https://drive.google.com/drive/folders/11BXJZuE8QrVZzX--K6JhTPE3IF32J7JC

Why to go with the Minimal Version:

First, to reduce the overall cost of the system. Second, many of the open source Ardu-tester Arduino codes available on the web give errors. But through this minimal system you can test different codes and then implement one in your next project.

![mini_IMG_0050](https://github.com/user-attachments/assets/fdcb0143-c83e-461d-93dd-d987e0c79e26)

I made these PCBs using Seeed Fusion prototyping service. If you are looking for fast, high-quality PCB for your projects, Seeed Fusion PCB service may be a solution to yours also.  Seeed Fusion seamless process includes free design for manufacturing (DFM) checks and instant online quotes. Whether you're working on a small project or mass production, Seeed Fusion ensures precision and reliability at every stage. Bring your ideas to life faster with their trusted PCB service!
https://www.seeedstudio.com/fusion.html

Components required:

![mini_IMG_0045](https://github.com/user-attachments/assets/667b300b-751e-4dbc-ada5-5d87c3e6b5c0)

Arduino Nano Chip (ATMEGA328P)

16x2 LCD

100nf Capacitors

10uf Capacitors

150pf Capacitor

1k Resistors

5.1K Resistor

0603 Led

5K potentiometer

16Mhz Ceramic Resonator

Type C Port (Power only)

9V battery

AMS1117 5V Regulator

M7 Diode

Tactile switch

PCB from Seeed Fusion
https://www.seeedstudio.com/fusion.html

Circuit Diagram:

The schematics is separated into 5 sections. The first section contains the power input port and filter. Different value capacitors at the input of the voltage regulator are used to minimize supply noise. Second section contains a microcontroller and reset tactile switch. Third section is reserved for LCD. We are not using any separate controller for LCD, hence it can be directly mounted.

![Schematic_transistor-tester_2024-10-16 (1)](https://github.com/user-attachments/assets/ccb9884e-6da2-4341-9a40-5f9204673004)

4th section contains control of brightness through a 5k pot, main resistor divider network of ADC and some filters. 470K and 680 Ohms resistor divider network is given to the ADC of Arduino. These values can be calibrated inside the code also. The 5th section has programming pins and main output headers. I always prefer to get a microcontroller chip directly from the top of the Arduino Nano after burning the sketch into it.

PCB designs:

![Screenshot_2024_10_08-10](https://github.com/user-attachments/assets/889e91ec-0d9a-475b-878d-5144305da99d)

I made this minimal design using the above given modified schematics. You can download all the files and code from here. Programming headers are added on the back layer to change/ update the firmware.

![Screenshot_2024_10_08-8](https://github.com/user-attachments/assets/0b67d2e3-4c86-4505-8284-b0b35130324b)

I am using FR4 material, HASL finish, Green solder mask and 1.6mm thickness. A very thanks to Seeed Fusion for sponsoring this project. Seeed fusion is one of the leading PCB manufacturing companies in China. Deals in PCB manufacturing, SMT assembly, PCBA, stencil, 3D- printing and CNC. Try out the more services from here now, and get free PCB coupons on first Sign-up using this link.
https://drive.google.com/drive/folders/11BXJZuE8QrVZzX--K6JhTPE3IF32J7JC

Uploading the Code:

Full code can be downloaded from here, try to install the latest libraries for the LCD. You can comment here, if you find any problem in uploading the code. The code has more than 10 header files, so don’t get confused with that, just keep focus on Ardu-tester_1_13 and upload it using simple steps.

![Screenshot_2024_10_17-4](https://github.com/user-attachments/assets/ac9e8eae-1f77-4b07-ad43-bd451e7a8edc)


Working:

I encountered some problems while uploading the code in an ATMEGA328, after some research the problem is with the bootloader and type of chip. Atmega chip with mini_core bootloader will not work here because of absence of some internal registers. It doesn’t support the code layout at all and we can not use some functions. My idea is to use an Arduino NANO microcontroller for this and that’s what I did. PCb has its own programming pins, and the chip can be programmed through SPI(serial peripheral interface). This component tester can test all of the passive components and most of the active components. Like- Resistor, capacitor, inductor, BJT, UJT, MOSFET, IGBT, diode and LED. Here I have made some tests using my version:

![mini_IMG_0053](https://github.com/user-attachments/assets/6a91566a-df37-47a2-974b-b86fd36a4a4d)

This version not only tells the value of the component but also gives a small usable datasheet of that component. For example in the case of a capacitor the capacitance value, ESR, series inductor and resistor values can be obtained. Hence we will be able to calculate parasitics through the actual model of a component.

Testing Resistor:

![mini_IMG_0059](https://github.com/user-attachments/assets/b0dbb0bf-77db-40d0-9263-eca18071b8b2)

Testing LED:

![My Video1](https://github.com/user-attachments/assets/342c402c-6ebf-45a3-aa04-74e60363b423)

Testing Capacitor:

![mini_IMG_0061](https://github.com/user-attachments/assets/0a83e49f-aab4-411d-aec7-dbf7201121aa)

You may refer to a YouTube channel named eevblog who actually explained the working of resistor divider network and how wisely this meter is designed. Using a very less external circuit this meter covers almost every electronic component. The software is very optimized and thanks to the maker for giving us such an extraordinary device. Have a look on ongoing discounts on new PCB order from Seeed Fusion.
https://www.seeedstudio.com/fusion.html
