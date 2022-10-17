# SCR 2022-23 Telecom (WIP)
## Overview:
- We gave **2 communication systems** on the rover, ``2.4 GHz`` for small data and long ranges *(instructions/commands)*, and ``5 GHz`` for larger data and short ranges *(mainly Zed2 camera feed)*.
<br/>

- You'll need 3 antennas/*Rocket M3* & Raspberry Pi 4B which act as a gateway: Base station; Pi, 2.4 GHz, and 5 GHz will be mounted on the rover.
    + Base station is where you'll have your machine hooked up to the base anntena, and attempt to connect to the 2 rover's antennas through the Raspberry Pi (Ymir).
    + Your machine should be able to connect to either antenna, and send/receive data/instructions to Ymir.
    + **Ymir's static ip address:** `192.168.1.120` (you can change this if you want)
<br/>

- Ymir is acting as a gateway, and will be talking to all the other Pis on the Rover: `Drive (Loki)`, `Arm (Nyx)`, `Autonomy (TBH - ORIN Jetson)`, etc...
    + All the pi is connected through a switch. Proof of concept: you could `ssh`-ing into Ymir, you'll be able to `ssh` into any other pi on the rover.
<br/>

- Once you set up everything on your local network, all the raspberry pi’s on your rover should be visible from your local machine If you look at the rover, all the pis are connected to a switch and the antennas are also connected to that switch. Once everything is set up, your last touch is to use ROS domain to set all the nodes that’re communicating with each other one the same domain So the messages get across, and goes to the correct node
    + Example of data feed: `Camera stream` **→** `Drive Pi (Loki)` **→** `5 GHz antenna on the Rover` **→** `5GHz antenna Base station` **→** `Local machine (someone’s computer)`.
<br/>

- Below are detailed instructions, documentation, and resources to help you setup, test, trouble shoot, and use the telecom system.
<br/>

---------------------
## Telecom System Documentation
### [Pi Gateway Setup](doc/Pi_Gateway_Setup.md)
- This is the main documentation for setting up the Pi Gateway. It includes instructions for setting up the Pi and settings its static IP address (gateway).
<br/>

### [Base Station & Anntena Setup](doc/BaseStation_Antenna_Setup.md)
- Setting up the Rocket M3 antennas on the rover / base station & bridging point to point connection between 2 antennas.
<br/>

### [Telecom System Diagram](doc/Diagram.md)
- Diagram of the telecom system, and how the data is being sent/received.
<br/>

### [Hardware Requirements](doc/Hardware.md)
- Hardware requirements for the telecom system.
<br/>

### [Backup](backup/backup_data.md)
- Backup in the event that Telecom/Ymir's SD card fails/corrupts/broke.
- This has a img of the Telecom SD card used as the gateway.