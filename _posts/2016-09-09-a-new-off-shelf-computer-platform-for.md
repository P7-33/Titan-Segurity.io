---
title: 'A new off-the-shelf computer platform for sounding rockets
features @Adafruit and @Raspberry_Pi #Space #RaspberryPi'
date: 2019-10-14T20:58:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-50.png)

Via the AIP [Review of Scientific Instruments](https://aip.scitation.org/doi/10.1063/1.5118855):

> In order to supersede the aging Microchip ATMEGA328P as the de facto standard for Commercial off-the-shelf (COTS) On-Board Computers (OBCs) with a more powerful system for different kinds of high-speed sensors and image acquisition applications, we developed advanced processors, encryption, and security experiment (apex).
> 
> The platform consisting of a newly developed OBC using commercial components has been flight tested during the ATEK/MAPHEUS-8 sounding rocket campaign. The main advantages of the apex OBC lies in the speed and simplicity of the design while maintaining operational security with a redundant master-master microcontroller system, as well as dual flash storage within each master.
> 
> Additionally, a single board computer with a containerized and failure-resistant Operating System (OS) (balenaOS) was included to allow usage of a high-definition camera or other more compute-intensive tasks. The bench and flight tests were performed successfully and already showed feasible ways to further improve operational performance.

The package uses **four Adafruit Sensors** for various tasks: the Adafruit [LSM9DS1 9-DOF](https://www.adafruit.com/product/3387) [Accel/Mag/Gyro+Temp sensors](https://www.adafruit.com/product/3387), [DS3231 real-time clock (RTC)](https://www.adafruit.com/product/3013), [ADS1015 ADC 4 channel amp](https://www.adafruit.com/product/1083), and a [BME280 Temp/Humidity/Pressure sensor](https://www.adafruit.com/product/2652).

The biggest drawback of the ATMEGA328P microcontroller, which is commonly used in this application, is its age and now limited performance. Although it is still useful for simple applications, higher throughput data sampling, complex mathematics, or cryptographic functions require more computational power. To support more ambitious projects, advanced processors, encryption, and security experiment (apex) has been designed to flight-test a two-staged OBC using state-of-the-art COTS components to support different mission requirements.

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-49.png)

The blue boards in the package are the four Adafruit sensors while the black boards are the ESP32 microcontrollers and the green board is a Raspberry Pi Zero W single board computer.

Apex consists of two different systems to support different mission roles.

> The first system is a redundant master-master configuration of **two ESP32-PICO-D4 MCUs**, each connected to its own 32 GB micro secure digital memory card (_μ_SD). This system is tasked with the acquisition, processing, storage, and transmission of Inter Integrated Circuit (i2c) sensor data.
> 
> The second system is a Raspberry Pi Zero W, hardened with a specialized read-only Operating System (OS), which exposes a container hypervisor to run different mission-payloads in an isolated, managed, and non interruptive context. It uses a 64 GB _μ_SD card. The RPi is also connected to the telemetry and signal interface of the MAPHEUS service module—as well as to the i2c-bus of the first system. However, the main objective of the RPi is to record footage using a high definition (HD) camera and log occurrences of the different service module signals for later analysis

The performance of the ESP32 is a massive improvement—changing from a single 20 MHz, 8 bit core to a 240 MHz, 32 bit dual core with multiple cryptographic extensions, a specialized high-speed SD card interface, as well as an “ultralow power” coprocessor for management and lightweight operations.

The Raspberry Pi Zero W on apex uses the former resinOS, now called balenaOS, a specialized read-only Linux OS. Due to its design, important files cannot be corrupted with an erroneous write process or power failure, which renders it to boot successfully in every case.

For full information, [see this article](https://aip.scitation.org/doi/10.1063/1.5118855). For video of the project, see [here on YouTube](https://youtu.be/JlcReUwZXFU) and below.

And check out the inexpensive Adafruit sensors you can buy for your project: Adafruit [LSM9DS1 9-DOF](https://www.adafruit.com/product/3387) [Accel/Mag/Gyro+Temp sensors](https://www.adafruit.com/product/3387), [DS3231 real-time clock (RTC)](https://www.adafruit.com/product/3013), [ADS1015 ADC 4 channel amp](https://www.adafruit.com/product/1083), and a [BME280 Temp/Humidity/Pressure sensor](https://www.adafruit.com/product/2652).