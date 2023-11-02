# Responsibility and resource
This is the unofficial target for INAV( Original source: https://github.com/iNavFlight/inav). Provides support for flight control boards that do not have official INAV support for the STM32F411CEU6 board. 
Whether or not to use this firmware is the user's responsibility and is free to do so. INAV developer link : https://github.com/iNavFlight/inav/tree/master/docs/development You can find all the details for firmware development here.

# STM32F411CEU6 INAV Firmware
STM32F411CEU6 Board Firmware
First, let's connect the board and the computer.
![image](https://user-images.githubusercontent.com/19993109/139479391-49dafee0-a7da-49ae-9196-10a578d4ac55.png)

# Download INAV Configurator
https://github.com/iNavFlight/inav-configurator/releases

# Windows
Download Configurator for Windows platform (win32 or win64 is present)
Extract ZIP archive
Run INAV Configurator app from unpacked folder
Configurator is not signed, so you have to allow Windows to run untrusted application. There might be a monit for it during first run

# Install DFU Drivers (DFU mode)
## ImpulseRC Driver Fixer
https://impulserc.blob.core.windows.net/utilities/ImpulseRC_Driver_Fixer.exe
* Start ImpluseRC Driver Fixer
* Connect the FC USB to the PC While holding the boot button in. (DO NOT power on FC via external 5V or Vbat)
* The ImpulseRC Driver Fixer should then see and load the proper driver
* Start INAV configurator
* Connect the FC USB to the PC while holding the boot button in.
* INAV configurator should show it’s connected in DFU mode in the top right corner (DO NOT click the CONNECT button)
* Choose the latest hex file for your FC and then “Load Firmware local”. Once loaded, click “Flash Firmware”.

# Setup sensors video
https://youtu.be/HbSUMauSkiw

[![sensors setup](https://user-images.githubusercontent.com/19993109/143448588-6d599bb3-b89d-479a-997a-c6c4c3e21fea.png)](https://youtu.be/HbSUMauSkiw "sensors setup")
# For INAV 6.1 "Horizon Hawk" New wire connection

## Quadcopter and Plane Firmware inav_6.1.1_STM32F411CE.zip
### This firmware provides SOFTSERIAL support for Quadcopter and Plane. There is no extra servo support for Plane. Supports two extra servos for Quadcopter. The pin connections below are the same for both firmwares.
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/a7bc5353-be8f-49d7-b47e-8685062d16f3)

## Hexacopter and Plane Firmware inav_6.1.1_STM32F411CE_HEX.zip
### This firmware supports two extra servos for Hexacopter and Plane. There is no SOFTSERIAL support.
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/723ac35d-372e-4f74-93bd-077c431e5369)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/79192a7b-2e28-4fb5-9351-c9b4a1ace3c0)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/49380a04-1bc8-4fac-9199-5dccc1e06aba)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/4eb16000-7abe-4209-af25-581cc869b4e0)


![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/1795caa1-f74d-40f2-b38e-1c8d144271c0)

![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/ca81d0db-c112-4351-80a9-414d85008cc9)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/c9fdb76d-98cc-43ad-b9f8-2bcff9c55686)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/1c16d8e9-cdd1-47fe-917a-640c6c577156)
## WS2811 5 Volt Led Strip
There must be a 5V external voltage source. Don't buy from board source, you will burn the microcontroller.
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/7cbca6a2-a52e-4717-baac-76d49ab18dff)
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/01d31dc0-9265-437c-8cec-c1dc0161a9a5)

# Calibration for ESC

Instructions for setting throttle calibration for ESC high and low signal input:
1. Connect the ESC with the motor, connect the signal lead to the board according to the pin and motor port according to the diagram. You should do this for all of the motors you are going to use.
2. Open the INAV Configurator and connect to the flight control hub.
3. Adjust the gyroscope / accelerometer and magnometer calibration settings.
4. Turn on the remote control and enable the receiver protocol in the Receiver section. 
5. Go to the Output field and set the ESC output protocol according to you. We describe the setup for the STANDARD protocol.
6.To calibrate ESCs, make sure the propellers are off, flick on the “I understand” toggle, raise Master to full value, and plug in your battery.
7. The ESCs will go through their tones.
8. When the double beeping sound is heard (the highest point of the throttle is confirmed), move the throttle to the lowest point.
9. ESC calibration is considered done when three beeps mean OK.
10. Now unplug, plug in again, and raise Master very slowly until the motors are spinning comfortably.

This video your can help. https://www.youtube.com/watch?v=1IrgbY0YhqM

# SBUS Signal Inverter
The inverter is easy to make, only requires 2 resistors (10K ohm and 4.7K ohm), 1 transistor (BC547b), and one servo cable. These are all very cheap and easy to find.
![image](https://github.com/rizacelik/STM32F411CEU6_INAV_Firmware/assets/19993109/ab6d0c71-d6ce-4dff-9e2d-8936900b9bbe)

# Monitoring Battery
For measuring current:

Use Current Sensor ACS712. Connect ACS712 OUT pin to CURRENT_METER_ADC FC pin.

For measuring voltage:

Use voltage divider scheme with resistors. Maximum battery voltage after dividing should be below 3.3v. Connect battery plus (after dividing, max 3.3v) to VBAT_ADC_CHANNEL pin on FC. Battery GND to FC GND.

![image](https://user-images.githubusercontent.com/19993109/201759640-6365017f-2cce-4822-a51d-53cedb853967.png)

You can use this online voltage divider calculator to play around with different values and get maximum output of 3.3v.
https://ohmslawcalculator.com/voltage-divider-calculator

# Old version INAV Firmware Full wire connection

![image](wire.png)

![image](https://user-images.githubusercontent.com/19993109/202130179-ef0616bc-785d-4cfc-98a4-097b3db7d4aa.png)

# Camera Switch and Power Switch 
![image](https://user-images.githubusercontent.com/19993109/201590186-375f1227-3c79-4911-b299-c99d0dd17070.png)

# Use DC DC converter for Servo Motors
![image](https://user-images.githubusercontent.com/19993109/202128769-e25c806f-7465-484e-b5be-e26ed039809d.png)

# Use DC DC converter for Board
![image](https://user-images.githubusercontent.com/19993109/202129433-0c62a71a-41a4-4acb-99f8-6ad0d76db480.png)

# STM32F411CEU6 PINOUT Connection
![image](https://user-images.githubusercontent.com/19993109/139479854-9793e17c-1e2a-4ccc-8b5f-ec23026710fd.png)

# GY-87 10DOF Module MPU6050 HMC5883L BMP180
![image](https://user-images.githubusercontent.com/19993109/139479938-a1166d41-17c8-41a2-8903-195406ecd020.png)

# Module Connection
![image](https://user-images.githubusercontent.com/19993109/139481190-abcfcc7e-f293-4a88-a734-72a122daef17.png)

# Receiver Connection
![image](https://user-images.githubusercontent.com/19993109/139479978-5e0735b5-34c6-4752-b130-f54a79ec9ce5.png)

![image](https://user-images.githubusercontent.com/19993109/139480054-d270bc46-24c8-4c49-a4b3-eb6e3ae2ea32.png)

# INAV Configurator IBUS Telemetry Setup

![image](https://user-images.githubusercontent.com/19993109/148845453-e8c84093-4cae-4f5f-9f57-10febcd7216a.png)

# IBUS Receiver Pins and IBUS Telemetry input Receiver
![image](https://user-images.githubusercontent.com/19993109/148845532-a4476a7b-ea24-4711-903e-6e2f61280f9a.png)

## SOFTSERIAL_1_TX_PIN     PB6
![image](https://user-images.githubusercontent.com/19993109/148846827-12eb543c-f4cb-4ab8-be8f-1b9b10d9a25b.png)

# OSD Connection
![image](https://user-images.githubusercontent.com/19993109/148816930-2e3b88e6-693b-42f9-bf57-801aac6cbe31.png)

# Motors Connection
![image](https://user-images.githubusercontent.com/19993109/139480115-09056969-39fd-42c4-a09e-0201845f48fa.png)

# Hexacopter Drone Frame
![image](https://user-images.githubusercontent.com/19993109/139480161-2b3f7512-6f71-4ec0-8eb6-8fe174400366.png)

