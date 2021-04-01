# Setup for Raspberry pi

## Wiring Pi update for Rapberry pi 4
Info from: https://learn.sparkfun.com/tutorials/raspberry-gpio/c-wiringpi-setup

We highly recommend using Git to download the latest version. To check what version you have, enter the following command.
```
gpio -v
```
If you receive an output similar to to the following with the Unknown17, you'll want to update WiringPi on a Raspberry Pi 4 or above.
```
gpio version: 2.50
Copyright (c) 2012-2018 Gordon Henderson
This is free software with ABSOLUTELY NO WARRANTY.
For details type: gpio -warranty

Raspberry Pi Details:
  Type: Unknown17, Revision: 02, Memory: 0MB, Maker: Sony
    * Device tree is enabled.
    * --> Raspberry Pi 4 Model B Rev 1.2
    * This Raspberry Pi supports user-level GPIO access.
```
Enter the following to remove the wiringPi and configuration files.
```
sudo apt-get purge wiringpi
```
Then type the following for the Pi to remove all locations that remember wiringPi.
```
hash -r
```
As long as you have Git installed, these commands should be all you need to download and install Wiring Pi.
```
git clone https://github.com/WiringPi/WiringPi.git
```
This will make a folder in your current directory called WiringPi. Head to the Wiring Pi directory.
```
cd WiringPi
```
Then pull the latest changes from the origin.
```
git pull origin
```
Then enter the following command. The ./build is a script to build Wiring Pi from the source files. This builds the helper files, modifies some paths in Linux and gets WiringPi ready to rock.
```
./build
```
At this point, the library should work. Run the gpio command shown below to view some information about the wiringPi version and the Pi that it is running on.
```
gpio -v
```
Entering the following command will draw a table illustrating the configuration for the pins in the 40-pin connector.
```
gpio readall
```

## Test Wiring Pi

Toggling an LED
Open up a terminal, and try some of these system calls. To configure pin 18, enter the following. By default, the pin is set as an input.
```
gpio -g mode 18 output
```
To turn the pin HIGH, enter the following.
```
gpio -g write 18 1
```
To turn it back low, enter the following.
```
gpio -g write 18 0
```
As long as your LED is still connected to pin 18, it should blink on and off following the last two commands.

Reading a Button Press
To test the button, you will first need to configure pin 17 with the Pi's internal pull-up resistor.
```
gpio -g mode 17 up
```
To read the pin, enter for the following.
```
gpio -g read 17
```
