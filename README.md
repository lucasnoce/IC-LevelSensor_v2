# IC-LevelSensor_v2
This is version 2 of an IoT device designed to measure water levels using an ultrasonic sensing module and transmit the acquired data via NBIoT.

## Summary
Similar to version 1, the system employs an AJ-SR04M ultrasonic sensing module now connected to a STM32L476RGT6 microcontroller. This module measures the time interval it takes for an ultrasonic wave to travel from the transducer to the water level and back. By calculating the distance based on the time duration, the speed of sound, and dividing the result by 2, the accurate water level is determined. As the speed of sound varies based on factors such as temperature, humidity, and pressure, a SHT31-DIS sensor is incorporated to measure temperature and humidity (pressure is assumed constant). This additional information allows for precise estimation of the speed of sound just before each distance measurement is taken.

To transmit data to the tago.io platform, a SIM7020 NBIoT module is utilized, employing the MQTT protocol. This facilitates the configuration of a comprehensive dashboard displaying variations in water and battery levels, local temperature and humidity over time, making it an excellent solution for monitoring purposes.

The device is specifically designed for deployment in remote environments and operates on battery power. Due to this constraint, the system primarily operates in low-power mode and wakes up periodically. In this initial version of the device, the wake-up period is intentionally kept small, and collected data is transmitted during each wake-up event via NBIoT. This design choice aims to facilitate easier debugging and testing of the device's functionality.

## Designed PCB
The following image shows the designed PCB layout. It incorporates the SMT32, SHT31, SIM7020E and its adjacent circuitry onto the layout, only leaving the AJ-SR04M as an external module. The PCB also features a selectable current sensing shunt resistor, some ESD protection and can be powered either by 1.5V AAA batteries or Micro USB type B.

<img src="https://github.com/lucasnoce/IC-LevelSensor_v2/blob/main/PCB_Design/LevelSensor_v2.0/Images/3D_PCB.jpg" width=100% height=100%>

## Software
Still under development, all drivers and functionalities will be implemented from scratch through STM32CubeIDE.
