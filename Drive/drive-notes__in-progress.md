# NOT DONE FINISH WHEN DRIVE WORKY



# 0) Setup
get rid of build log install folders in drive directory

    cd drive
    rm -rf build log install

`setup.py/src/hardware_interface/hardware_interface/odrive_node.py`: 

In the function `def connect_odrive_callback`: 

 >if not changed yet, ~line 180: give the correct serial number for the specifc odrive you are using.

# 1) Changing serial Number for Odrive on odrivetool
To find serial number:
  ` odrivetool > odrive[num].serial_number`
  >ex: odrive0.serial_number

**Note: The number given by the command is in base 10, in pyfile the input needs to be in hex.**


---
repeat for every odrive.


# 2) Calibrating motorss

## Manual configs as of 10/12/22 (this should be plan z)

- run `python3 drive_interface.py`

  - Reconfigure: `1`
  >(requires restart of the program)

  - mash enter
  > (when prompted)
  
  - open `odrvtool`
  ---
  - run these individually (the calibratoins need tofniish before moving on to the next command. It won't work if you do them all at once):

- `odrv0`
```
odrv0.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv0.axis0.motor.config.pre_calibrated = True
```
```
odrv0.axis0.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv0.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv0.axis0.encoder.config.pre_calibrated = True
```
```
odrv0.axis0.controller.input_vel = 3
```
```
odrv0.axis0.requested_state = AXIS_STATE_CLOSED_LOOP_CONTROL
```
---
```
odrv0.axis1.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv0.axis1.motor.config.pre_calibrated = True
```
```
odrv0.axis1.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv0.axis1.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv0.axis1.encoder.config.pre_calibrated = True
```
---
---
- `odrv1`
```
odrv1.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv1.axis0.motor.config.pre_calibrated = True
```
```
odrv1.axis0.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv1.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv1.axis0.encoder.config.pre_calibrated = True
```
---
```
odrv1.axis1.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv1.axis1.motor.config.pre_calibrated = True
```
```
odrv1.axis1.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv1.axis1.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv1.axis1.encoder.config.pre_calibrated = True

```
---
---
- `odrv2`
```
odrv2.axis0.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv2.axis0.motor.config.pre_calibrated = True
```
```
odrv2.axis0.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv2.axis0.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv2.axis0.encoder.config.pre_calibrated = True
```
---
```
odrv2.axis1.requested_state = AXIS_STATE_MOTOR_CALIBRATION
```
```
odrv2.axis1.motor.config.pre_calibrated = True
```
```
odrv2.axis1.requested_state = AXIS_STATE_ENCODER_HALL_POLARITY_CALIBRATION
```
```
odrv2.axis1.requested_state = AXIS_STATE_ENCODER_OFFSET_CALIBRATION
```
```
odrv2.axis1.encoder.config.pre_calibrated = True
```



---
---
---
# Other Commands
- set velocity
>seems to not work doing all at once again
```
odrv0.axis0.controller.input_vel = 3
odrv0.axis1.controller.input_vel = 3
```
```
odrv1.axis0.controller.input_vel = 3
odrv1.axis1.controller.input_vel = 3
```
```
odrv2.axis0.controller.input_vel = 3
odrv2.axis1.controller.input_vel = 3
```

odrv0.axis1.requested_state = AXIS_STATE_CLOSED_LOOP_CONTROL
odrv0.axis0.requested_state = AXIS_STATE_CLOSED_LOOP_CONTROL



odrv0.erase_configuration()
odrv0.save_configuration()
odrv0.reboot()




//when it worked

In [2]: odrv0.axis0.motor.error
Out[2]: 0

In [3]: odrv0.axis0.encoder.error
Out[3]: 0


no errors






==============================================

All odrive usb were connected to Fenrir

using drive_interface.py (unchanged)
using 24v battery (from india's team)


Ros2 stuff:
  source /opt/ros/foxy/setup.bash
  cd drive
  colcon build
  . install/setup.bash

Then use pip install:
  pip install loguru
  pip install opencv-python
  pip install pygame


  . install/setup.bash
  ros2 run hardware_interface odrive_node

  . install/setup.bash
  ros2 run hardware_interface zed_publisher


  select option 3



=====
SETUP
=====

  Neo
    Red on both ends 
    Black in middle

  Jumpers
    GND  = Black
    Z    = Green
    B    = Yellow
    A    = Blue
    5V   = Red
    3.3V = UNUSED

====================
BRUSHLESS NEO OSIRIS
====================

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



=======
ODRIVES
=======

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



============================================

odrv0.axis0.encoder.config.bandwidth = 100
#was 500.0


6 pin   jumper
red   =   red 
yellow  =   yellow
orange  =   blue
black   =   black
green   =   green







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
      



Oct 8 update

  m0 left back
  m1 right back



CONFIGURATION THAT WORKED ON 10/10

  Odrive 5
    M0 => Right Middle
    M1 => Left Back

  Odrive 1
    M0 => Left Middle
    M1 => Left Front

  Odrive 2
    M0 => Right Back
    M1 => Right Front


Total Tests
  6 odrive by 2 axis by 6 neo => 180
