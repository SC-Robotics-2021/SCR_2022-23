## All odrive usb were connected to Fenrir / (Now Loki)
- Using drive_interface.py (unchanged)
- Using 24v battery (from india's team)


### Ros2 stuff:
```
source /opt/ros/foxy/setup.bash
cd drive
colcon build
. install/setup.bash
```

### Then use pip install:
```
pip install loguru
pip install opencv-python
pip install pygame
```

### Run drive:
`Terminal 1:`
```
. install/setup.bash
ros2 run hardware_interface odrive_node
```

`Terminal 2:`
```
. install/setup.bash
ros2 run hardware_interface zed_publisher
```

`Terminal 3:`
```
python3 drive_interface.py
```
+ Select option 1 first to calibrate
+ Then select option 3 to run it



# SETUP
	Neo
		Red on both ends 
		Black in middle

	Jumpers
		GND = Black
		Z = Green
		B = Yellow
		A = Blue
		5V = Red
		3.3V = UNUSED


# BRUSHLESS NEO OSIRIS

	Left Front
		Works on both
		didn't pass encoder calibration on odrive 4...? 

	Left Middle
		Works on both

	Left Back
		MotorError.UNBALANCED_PHASES

	Right Front
		EncoderError.ILLEGAL_HALL_STATE
		EncoderError.HALL_NOT_CALIBRATED_YET

		Passes calibration (for motor) without encoder plugged in(?)

		Need to research this

			odrv0.axis0.encoder.config.use_index = False
			odrv0.axis0.requested_state = AXIS_STATE_ENCODER_HALL_PHASE_CALIBRATION

	Right Middle
		Works on both

	Right Back
		MotorError.PHASE_RESISTANCE_OUT_OF_RANGE



# ODRIVES

	Odrive 1
		Works Flawless

	Odrive 2
		Works Flawless

	Odrive 3
		Works Flawless

	Odrive 4
		Is not discovered by computer
		
	Odrive 5
		Is not discovered by computer



#### Notes:
```
odrv0.axis0.config.encoder_bandwidth = 100
odrv0.hall_encoder0.config.enabled = True
odrv0.axis0.config.load_encoder = EncoderId.HALL_ENCODER0
odrv0.axis0.config.commutation_encoder = EncoderId.HALL_ENCODER0
odrv0.save_configuration()

# [wait for ODrive to reboot]

odrv0.axis0.requested_state = AxisState.ENCODER_HALL_POLARITY_CALIBRATION

# [wait for motor to stop]

odrv0.axis0.requested_state = AxisState.ENCODER_HALL_PHASE_CALIBRATION

# [wait for motor to stop]
```

============================================

```
odrv0.axis0.encoder.config.bandwidth = 100
#was 500.0


6 pin		jumper
red 	= 	red 
yellow 	= 	yellow
orange  =   blue
black   =  	black
green   =   green
```





UPDATED 10/7

	All tested on Odrive 5
	
	Right Middle
		Passed all Calibrations

	Left Middle
		Passed all Calibrations

	Right Front
		Passed all Calibrations

	Left Front
		Passed all Calibrations

	Right Back
		Passed all Calibrations

	Left Back
		MotorError.UNBALANCED_PHASES (on m0)
		Passed all Calibrations when on M1, with *RIGHT BACK* on M0




NOW TRYING ALL MOTORS AT ONCE, USING:
		 ODRIVE 5(LEFT BACK[M1] RIGHT BACK[M0])

		 ODRIVE 4(LEFT FRONT[M1] RIGHT FRONT[M0])
		 	ON THE POWER SUPPLY

		 ODRIVE 3(LEFT MIDDLE[M1] RIGHT MIDDLE[M0])

	Pre-test:
		Odrive5:
			
