# odrv0
---
### odrv0.vbus_voltage
[float], the current DC power supply voltage, the unit is [V]

### odrv0.serial_number
[uint64_t], ODrive hardware serial number

### odrv0.hw_version_major
[uint8_t], hardware major version number

### odrv0.hw_version_minor
[uint8_t], hardware minor version number

### odrv0.hw_version_variant
[uint8_t], hardware variant version, used to subdivide the hardware voltage version, such as 56v voltage version this value is 56, 24v voltage version this value is 24

### odrv0.fw_version_major
[uint8_t], the main firmware version number

### odrv0.fw_version_minor
[uint8_t], the firmware minor version number

### odrv0.fw_version_revision
[uint8_t], firmware revision version number

### odrv0.fw_version_unreleased
[uint8_t], whether the firmware version is officially released, if it is an official release version, the value is 0, otherwise it is 1

### odrv0.user_config_loaded
[bool], used to check whether the configuration is loaded correctly after startup, if the configuration is loaded correctly, this value is True, otherwise it is False

### odrv0.brake_resistor_armed
[bool], used to indicate whether the current braking resistor control signal is enabled

### odrv0.test_property
[uint32_t], used for testing, used to test whether the reading and writing of attributes is normal

### odrv0.test_function(delta: int32_t)
Used for testing, used to test whether the function is executed normally, the return value is the internal static variable plus the delta value of the function input

### odrv0.get_oscilloscope_val(index: int)
Get the value corresponding to the index of the current virtual oscilloscope array. The default in the firmware is to collect DC voltage. If you want to collect other data, you need to modify the firmware source code yourself. The index range is [0~127]

### odrv0.get_adc_voltage(gpio: int)
Get the voltage collected by GPIO port, the unit is [v], and only support ADC input on GPIO port 1, 2, 3, 4

### odrv0.save_configuration()
Save configuration to internal FLASH

### odrv0.erase_configuration()
Erase the configuration in FLASH, and all configurations will become the default configuration after the next restart

### odrv0.reboot()
Restart ODrive hardware

### odrv0.enter_dfu_mode()
Put ODrive into DFU mode

# odrv0.config
### odrv0.config.brake_resistance
[float], the resistance of the braking resistor, the unit is [ohm], if the braking resistor is not used or connected, set it to 0

### odrv0.config.enable_uart
[bool], whether to enable uart

### odrv0.config.enable_i2c_instead_of_can
[bool], whether to enable i2c instead of can

### odrv0.config.enable_ascii_protocol_on_usb
[bool], whether to enable USB communication to support ascii control protocol

### odrv0.config.dc_bus_undervoltage_trip_level
[float], set the low voltage alarm threshold, when the DC voltage is lower than this value, it will stop and report an error

### odrv0.config.dc_bus_overvoltage_trip_level
[float], set the overvoltage alarm threshold, when the DC voltage is higher than this value, it will stop and report an error

# odrv0.config.gpio1_pwm_mapping
### odrv0.config.gpio1_pwm_mapping.endpoint
Set GPIO 1 as the mapping between the PWM input and the controlled variable. If you want the PWM input to control the axis0 motor speed input odrv0.config.gpio1_pwm_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to unmapping, you can enter odrv0.config.gpio1_pwm_mapping.endpoint = None

### odrv0.config.gpio1_pwm_mapping.min
Mapping the minimum value of the controlled variable, when the PWM duty is 1 ms, the controlled variable is this value

### odrv0.config.gpio1_pwm_mapping.max
Mapping the maximum value of the controlled quantity, when the PWM duty is 2 ms, the controlled quantity is this value

# odrv0.config.gpio2_pwm_mapping
### odrv0.config.gpio2_pwm_mapping.endpoint
Set GPIO 2 as the mapping between the PWM input and the controlled variable. If you want the PWM input to control the axis0 motor speed input odrv0.config.gpio2_pwm_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to unmapping, you can enter odrv0.config.gpio2_pwm_mapping.endpoint = None

### odrv0.config.gpio2_pwm_mapping.min
Mapping the minimum value of the controlled variable, when the PWM duty is 1 ms, the controlled variable is this value

### odrv0.config.gpio2_pwm_mapping.max
Mapping the maximum value of the controlled quantity, when the PWM duty is 2 ms, the controlled quantity is this value

# odrv0.config.gpio3_pwm_mapping
### odrv0.config.gpio3_pwm_mapping.endpoint
Set GPIO 3 as the mapping between the PWM input and the controlled variable. If you want the PWM input to control the axis0 motor speed input odrv0.config.gpio3_pwm_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to unmapping, you can enter odrv0.config.gpio3_pwm_mapping.endpoint = None

### odrv0.config.gpio3_pwm_mapping.min
Mapping the minimum value of the controlled variable, when the PWM duty is 1 ms, the controlled variable is this value

### odrv0.config.gpio3_pwm_mapping.max
Mapping the maximum value of the controlled quantity, when the PWM duty is 2 ms, the controlled quantity is this value

odrv0.config.gpio4_pwm_mapping
### odrv0.config.gpio4_pwm_mapping.endpoint
Set GPIO 4 as the mapping between the PWM input and the controlled variable. If you want the PWM input to control the axis0 motor speed input odrv0.config.gpio4_pwm_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to unmapping, you can enter odrv0.config.gpio4_pwm_mapping.endpoint = None

### odrv0.config.gpio4_pwm_mapping.min
Mapping the minimum value of the controlled variable, when the PWM duty is 1 ms, the controlled variable is this value

### odrv0.config.gpio4_pwm_mapping.max
Mapping the maximum value of the controlled quantity, when the PWM duty is 2 ms, the controlled quantity is this value

odrv0.config.gpio3_analog_mapping
### odrv0.config.gpio3_analog_mapping.endpoint
Set GPIO 3 as the mapping between the analog input and the controlled variable. If you want the analog input to control the axis0 motor speed input odrv0.config.gpio3_analog_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to cancel the mapping, you can enter odrv0.config.gpio3_analog_mapping.endpoint = None

### odrv0.config.gpio3_analog_mapping.min
Map the minimum value of the controlled quantity, when the input voltage is 0 v, the controlled quantity is this value

### odrv0.config.gpio3_analog_mapping.max
Map the maximum value of the controlled quantity, when the input voltage is 3.3 v, the controlled quantity is this value

# odrv0.config.gpio4_analog_mapping
### odrv0.config.gpio4_analog_mapping.endpoint
Set GPIO 4 as the mapping between the analog input and the controlled variable. If you want the analog input to control the axis0 motor speed input odrv0.config.gpio4_analog_mapping.endpoint = odrv0.axis0.controller._remote_attributes[‘vel_setpoint’]

If you want to unmapping, you can enter odrv0.config.gpio4_analog_mapping.endpoint = None

### odrv0.config.gpio4_analog_mapping.min
Map the minimum value of the controlled quantity, when the input voltage is 0 v, the controlled quantity is this value

### odrv0.config.gpio4_analog_mapping.max
Map the maximum value of the controlled quantity, when the input voltage is 3.3 v, the controlled quantity is this value

# odrv0.system_stats
### odrv0.system_stats.uptime
[uint32_t], the running time after the system is started, the unit is [ms]

### odrv0.system_stats.min_heap_space
[uint32_t], get the historical minimum value of unallocated memory heap, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_axis0
[uint32_t], get the historical minimum value of unallocated stack memory of axis0 thread, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_axis1
[uint32_t], get the historical minimum value of unallocated stack memory of axis1 thread, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_comms
[uint32_t], get the historical minimum value of unallocated stack memory of the communication thread, the unit is [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_usb
[uint32_t], get the historical minimum value of unallocated stack memory of the USB thread, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_uart
[uint32_t], get the historical minimum value of unallocated stack memory of the UART thread, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_usb_irq
[uint32_t], get the historical minimum unallocated stack memory of the USB IRQ thread, in [Bytes], used to debug stack allocation

### odrv0.system_stats.min_stack_space_startup
[uint32_t], get the historical minimum value of unallocated stack memory, in [Bytes], used to debug stack allocation

# odrv0.system_stats.usb
### odrv0.system_stats.usb.rx_cnt
[uint32_t], usb received packet count

### odrv0.system_stats.usb.tx_cnt
[uint32_t], USB send packet count

### odrv0.system_stats.usb.tx_overrun_cnt
[uint32_t], USB sending overload packet count

# odrv0.system_stats.i2c
### odrv0.system_stats.i2c.addr
[uint8_t], i2c address

### odrv0.system_stats.i2c.addr_match_cnt
[uint32_t], i2c address match count

### odrv0.system_stats.i2c.rx_cnt
[uint32_t], i2c packet reception count

### odrv0.system_stats.i2c.error_cnt
[uint32_t], i2c error count

# odrv0.can
### odrv0.can.node_id
[uint8_t], can bus node ID

### odrv0.can.TxMailboxCompleteCallbackCnt
[uint32_t], can send completed count

### odrv0.can.TxMailboxAbortCallbackCnt
[uint32_t], can send interrupt count

### odrv0.can.received_msg_cnt
[uint32_t], can receive data frame count

### odrv0.can.received_ack
[uint32_t], can receive ACK frame count

### odrv0.can.unexpected_errors
[uint32_t], can error count

### odrv0.can.unhandled_messages
[uint32_t], can count of lost data frames

# odrv0.axis0
### odrv0.axis0.error
[enum], axis0 error code

```
ERROR_NONE = 0x00,
ERROR_INVALID_STATE = 0x01, //<! an invalid state was requested
ERROR_DC_BUS_UNDER_VOLTAGE = 0x02,
ERROR_DC_BUS_OVER_VOLTAGE = 0x04,
ERROR_CURRENT_MEASUREMENT_TIMEOUT = 0x08,
ERROR_BRAKE_RESISTOR_DISARMED = 0x10, //<! the brake resistor was unexpectedly disarmed
ERROR_MOTOR_DISARMED = 0x20, //<! the motor was unexpectedly disarmed
ERROR_MOTOR_FAILED = 0x40, // Go to motor.hpp for information, check odrvX.axisX.motor.error for error value 
ERROR_SENSORLESS_ESTIMATOR_FAILED = 0x80,
ERROR_ENCODER_FAILED = 0x100, // Go to encoder.hpp for information, check odrvX.axisX.encoder.error for error value
ERROR_CONTROLLER_FAILED = 0x200,
ERROR_POS_CTRL_DURING_SENSORLESS = 0x400,
ERROR_WATCHDOG_TIMER_EXPIRED = 0x800,
```

### odrv0.axis0.step_dir_active
[bool], whether step/dir is enabled

### odrv0.axis0.current_state
[enum], the current status of axis0

```
AXIS_STATE_UNDEFINED = 0,           //<! will fall through to idle
AXIS_STATE_IDLE = 1,                //<! disable PWM and do nothing
AXIS_STATE_STARTUP_SEQUENCE = 2, 	//<! the actual sequence is defined by the config.startup_... flags
AXIS_STATE_FULL_CALIBRATION_SEQUENCE = 3,   //<! run all calibration procedures, then idle
AXIS_STATE_MOTOR_CALIBRATION = 4,   	//<! run motor calibration
AXIS_STATE_SENSORLESS_CONTROL = 5,  	//<! run sensorless control
AXIS_STATE_ENCODER_INDEX_SEARCH = 6, 	//<! run encoder index search
AXIS_STATE_ENCODER_OFFSET_CALIBRATION = 7, //<! run encoder offset calibration
AXIS_STATE_CLOSED_LOOP_CONTROL = 8,  	//<! run closed loop control
AXIS_STATE_LOCKIN_SPIN = 9,       		//<! run lockin spin
AXIS_STATE_ENCODER_DIR_FIND = 10,
```

### odrv0.axis0.requested_state
[enum], command axis0 to enter a state

```
AXIS_STATE_UNDEFINED = 0,           //<! will fall through to idle
AXIS_STATE_IDLE = 1,                //<! disable PWM and do nothing
AXIS_STATE_STARTUP_SEQUENCE = 2, 	//<! the actual sequence is defined by the config.startup_... flags
AXIS_STATE_FULL_CALIBRATION_SEQUENCE = 3,   //<! run all calibration procedures, then idle
AXIS_STATE_MOTOR_CALIBRATION = 4,   	//<! run motor calibration
AXIS_STATE_SENSORLESS_CONTROL = 5,  	//<! run sensorless control
AXIS_STATE_ENCODER_INDEX_SEARCH = 6, 	//<! run encoder index search
AXIS_STATE_ENCODER_OFFSET_CALIBRATION = 7, //<! run encoder offset calibration
AXIS_STATE_CLOSED_LOOP_CONTROL = 8,  	//<! run closed loop control
AXIS_STATE_LOCKIN_SPIN = 9,       		//<! run lockin spin
AXIS_STATE_ENCODER_DIR_FIND = 10,
```


### odrv0.axis0.loop_counter
[uint32_t], axis0 internal loop count

### odrv0.axis0.lockin_state
[enum], motor lock operation status
```
LOCKIN_STATE_INACTIVE = 0,
LOCKIN_STATE_RAMP = 1,
LOCKIN_STATE_ACCELERATE = 2,
LOCKIN_STATE_CONST_VEL = 3,

```
### odrv0.axis0.watchdog_feed()
axis0 watchdog manual feeding

# odrv0.axis0.config
### odrv0.axis0.config.startup_motor_calibration
[bool], used to set whether to automatically perform motor calibration after startup

### odrv0.axis0.config.startup_encoder_index_search
[bool], used to set whether to automatically search the encoder index after startup

### odrv0.axis0.config.startup_encoder_offset_calibration
[bool], used to set whether to automatically perform encoder offset calibration after startup

### odrv0.axis0.config.startup_closed_loop_control
[bool], used to set whether to enter closed loop control automatically after startup

### odrv0.axis0.config.startup_sensorless_control
[bool], used to set whether to automatically enter the sensorless control after startup

### odrv0.axis0.config.enable_step_dir
[bool], whether to enable step/dir

### odrv0.axis0.config.counts_per_step
[float], step/dir Each step corresponds to the moving distance of the motor, the distance unit is encoder count

### odrv0.axis0.config.watchdog_timeout
[float], internal watchdog timeout setting of axis0, the unit is [s]

### odrv0.axis0.config.step_gpio_pin
[uint16_t], the GPIO corresponding to axis0 step

### odrv0.axis0.config.dir_gpio_pin
[uint16_t], the GPIO corresponding to axis0 dir

# odrv0.axis0.config.calibration_lockin
### odrv0.axis0.config.calibration_lockin.current
[float], the motor current when the encoder is calibrated by rotating the motor in open loop, the unit is [A]

### odrv0.axis0.config.calibration_lockin.ramp_time
[float], the time required for the current to climb to the set motor current when the motor is open-loop rotating and calibrating the encoder, the unit is [s]

### odrv0.axis0.config.calibration_lockin.ramp_distance
[float], the distance the motor speed climbs when the encoder is calibrated by rotating the motor in open loop, the unit is [rad]

### odrv0.axis0.config.calibration_lockin.accel
[float], the acceleration of the speed climbing when the motor is open-loop rotating to calibrate the encoder, the unit is [rad/s^2]

### odrv0.axis0.config.calibration_lockin.vel
[float], the speed set when the motor is open-loop rotating to calibrate the encoder, the unit is [rad/s]

# odrv0.axis0.config.sensorless_ramp
### odrv0.axis0.config.sensorless_ramp.current
[float], the motor current for open-loop startup in the non-inductive mode of the motor, in [A]

### odrv0.axis0.config.sensorless_ramp.ramp_time
[float], the current climb time of the open loop start of the motor in non-inductive mode, the unit is [s]

### odrv0.axis0.config.sensorless_ramp.ramp_distance
[float], the climb distance of the open loop start of the motor in non-inductive mode, the unit is [rad]

### odrv0.axis0.config.sensorless_ramp.accel
[float], the acceleration of the open loop start of the motor in non-inductive mode, the unit is [rad/s^2]

### odrv0.axis0.config.sensorless_ramp.vel
[float], the target speed for open loop start of the motor in non-inductive mode, the unit is [rad/s]

### odrv0.axis0.config.sensorless_ramp.finish_distance
[float], the running distance of the open loop start of the motor in non-inductive mode, the unit is [rad]

### odrv0.axis0.config.sensorless_ramp.finish_on_vel
[bool], whether to reach the target speed as the open loop start end sign

### odrv0.axis0.config.sensorless_ramp.finish_on_distance
[bool], whether to reach the target distance as the open loop start end sign

# odrv0.axis0.config.general_lockin
### odrv0.axis0.config.general_lockin.current
[float], the motor current in open loop operation mode, the unit is [A]

### odrv0.axis0.config.general_lockin.ramp_time
[float], the current climb time in open loop operation mode, the unit is [s]

### odrv0.axis0.config.general_lockin.ramp_distance
[float], the speed climbing distance in open loop operation mode, the unit is [rad]

### odrv0.axis0.config.general_lockin.accel
[float], the speed climbing speed in open loop operation mode, the unit is [rad/s^2]

### odrv0.axis0.config.general_lockin.vel
[float], the speed in open loop operation mode, the unit is [rad/s]

### odrv0.axis0.config.general_lockin.finish_distance
[float], the running distance in open loop operation mode, the unit is [rad]

### odrv0.axis0.config.general_lockin.finish_on_vel
[bool], whether to reach the set speed as the end condition of the open loop operation mode

### odrv0.axis0.config.general_lockin.finish_on_distance
[bool], whether to reach the set running distance as the end condition of open loop running mode

### odrv0.axis0.config.general_lockin.finish_on_enc_idx
[bool], whether to detect the encoder index signal as the end condition of the open loop operation mode

# odrv0.axis0.motor
### odrv0.axis0.motor.error
[enum], motor error code
```
ERROR_NONE = 0,
ERROR_PHASE_RESISTANCE_OUT_OF_RANGE = 0x0001,
ERROR_PHASE_INDUCTANCE_OUT_OF_RANGE = 0x0002,
ERROR_ADC_FAILED = 0x0004,
ERROR_DRV_FAULT = 0x0008,
ERROR_CONTROL_DEADLINE_MISSED = 0x0010,
ERROR_NOT_IMPLEMENTED_MOTOR_TYPE = 0x0020,
ERROR_BRAKE_CURRENT_OUT_OF_RANGE = 0x0040,
ERROR_MODULATION_MAGNITUDE = 0x0080,
ERROR_BRAKE_DEADTIME_VIOLATION = 0x0100,
ERROR_UNEXPECTED_TIMER_CALLBACK = 0x0200,
ERROR_CURRENT_SENSE_SATURATION = 0x0400,
ERROR_INVERTER_OVER_TEMP = 0x0800,
ERROR_CURRENT_UNSTABLE = 0x1000
```

### odrv0.axis0.motor.armed_state
[enum], motor PWM output status
```
ARMED_STATE_DISARMED = 0,
ARMED_STATE_WAITING_FOR_TIMINGS = 1,
ARMED_STATE_WAITING_FOR_UPDATE = 2,
ARMED_STATE_ARMED = 3,
```
### odrv0.axis0.motor.is_calibrated
[bool], whether the motor has been calibrated

### odrv0.axis0.motor.current_meas_phB
[float], the current measured on phase B of the motor, in [A]

### odrv0.axis0.motor.current_meas_phC
[float], the current measured on phase C of the motor, in [A]

### odrv0.axis0.motor.DC_calib_phB
[float], the motor phase B current offset, the unit is [A]

### odrv0.axis0.motor.DC_calib_phC
[float], motor phase C current offset, the unit is [A]

### odrv0.axis0.motor.phase_current_rev_gain
[float], the reciprocal of DRV8301 current sampling operational amplifier magnification

### odrv0.axis0.motor.thermal_current_lim
[flaot], the current limit value automatically calculated due to temperature rise, the unit is [A]

### odrv0.axis0.motor.get_inverter_temp()
[float], get the temperature value near the axis0 mos tube, the unit is [℃]

odrv0.axis0.motor.current_control
### odrv0.axis0.motor.current_control.p_gain
[float], the P value of the current PI loop. This value is automatically calculated and generated according to the motor phase inductance and phase resistance. It can also be manually adjusted here, but it cannot be saved to FLASH. The manually set value will disappear after restarting

### odrv0.axis0.motor.current_control.i_gain
[float], the I value of the current PI loop. This value is automatically calculated and generated according to the motor phase inductance and phase resistance. It can also be manually adjusted here, but it cannot be saved to FLASH. The manually set value will disappear after restarting

### odrv0.axis0.motor.current_control.v_current_control_integral_d
[float], the integral term in the PI control of the direct axis current loop, generally used for viewing and debugging

### odrv0.axis0.motor.current_control.v_current_control_integral_q
[float], the integral term in the quadrature axis current loop PI control, generally used for viewing and debugging

### odrv0.axis0.motor.current_control.Ibus
[float], axis0 motor current, this value is Iq + Id, the unit is [A]

### odrv0.axis0.motor.current_control.final_v_alpha
[float], the final Valpha output to the SVM

### odrv0.axis0.motor.current_control.final_v_beta
[float], the final output to Vbeta of SVM

### odrv0.axis0.motor.current_control.Iq_setpoint
[float], the target quadrature axis current value of the current loop control input, the unit is [A]

### odrv0.axis0.motor.current_control.Iq_measured
[float], the quadrature axis current value obtained by current sampling, the unit is [A]

### odrv0.axis0.motor.current_control.Id_measured
[float], the direct axis current value obtained by current sampling, the unit is [A]

### odrv0.axis0.motor.current_control.I_measured_report_filter_k
[float], the current low-pass filter coefficient of the direct axis quadrature axis after the current sampling, the default is 1 and the low-pass filter is not enabled. Setting it to 0 will completely end. This value cannot be saved to FLASH. It will be restored to the default value 1 after restarting.

### odrv0.axis0.motor.current_control.max_allowed_current
[float], the current maximum allowable current automatically calculated according to the set maximum current value and current temperature, the unit is [A]

### odrv0.axis0.motor.current_control.overcurrent_trip_level
[float], the overcurrent threshold calculated according to the real-time calculated maximum allowable current and the set allowable fluctuation range, the unit is [A], exceeding this value will stop the motor and report an error ERROR_CURRENT_SENSE_SATURATION

# odrv0.axis0.motor.gate_driver
### odrv0.axis0.motor.gate_driver.drv_fault
[enum], axis0 DRV8301 chip internal error code

```
DRV8301_FaultType_NoFault  = (0 << 0),  //!< No fault
DRV8301_FaultType_FETLC_OC = (1 << 0),  //!< FET Low side, Phase C Over Current fault
DRV8301_FaultType_FETHC_OC = (1 << 1),  //!< FET High side, Phase C Over Current fault
DRV8301_FaultType_FETLB_OC = (1 << 2),  //!< FET Low side, Phase B Over Current fault
DRV8301_FaultType_FETHB_OC = (1 << 3),  //!< FET High side, Phase B Over Current fault
DRV8301_FaultType_FETLA_OC = (1 << 4),  //!< FET Low side, Phase A Over Current fault
DRV8301_FaultType_FETHA_OC = (1 << 5),  //!< FET High side, Phase A Over Current fault
DRV8301_FaultType_OTW      = (1 << 6),  //!< Over Temperature Warning fault
DRV8301_FaultType_OTSD     = (1 << 7),  //!< Over Temperature Shut Down fault
DRV8301_FaultType_PVDD_UV  = (1 << 8),  //!< Power supply Vdd Under Voltage fault
DRV8301_FaultType_GVDD_UV  = (1 << 9),  //!< DRV8301 Vdd Under Voltage fault
DRV8301_FaultType_GVDD_OV  = (1 << 10)  //!< DRV8301 Vdd Over Voltage fault
```

# odrv0.axis0.motor.config

### odrv0.axis0.motor.config.pre_calibrated
[bool], whether the motor has been calibrated, when set to True, the following motor parameters are considered valid and available, if you don’t want to recalibrate the motor parameters every time you restart, you can set it to True

### odrv0.axis0.motor.config.pole_pairs
[int32_t], the number of motor pole pairs, you can check the motor data sheet or count the number of permanent magnets to get the number of pole pairs, the number of pole pairs = the number of permanent magnets / 2

### odrv0.axis0.motor.config.calibration_current
[float], the current when the motor is calibrated, the unit is [A]

### odrv0.axis0.motor.config.resistance_calib_max_voltage
[float], the maximum voltage when the motor calibration automatically detects the phase resistance, the unit is [v]

### odrv0.axis0.motor.config.phase_inductance
[float], motor phase inductance, the unit is [H], this value will be automatically updated after the motor calibration is performed, if you have detailed motor parameters, you can manually set this value

### odrv0.axis0.motor.config.phase_resistance
[float], motor phase resistance, the unit is ### [Ohm], this value will be automatically updated after the motor calibration is performed, if you have detailed motor parameters, you can manually set this value

### odrv0.axis0.motor.config.direction
[int32_t], motor running direction, 0 is invalid, 1 is the same as the encoder direction -1 is opposite to the encoder direction, the direction needs to be manually set in the non-inductive mode, and it will be automatically set in the encoder calibration in the inductive mode

### odrv0.axis0.motor.config.motor_type
[enum], motor type
```
MOTOR_TYPE_HIGH_CURRENT = 0,
MOTOR_TYPE_GIMBAL = 2
```
### odrv0.axis0.motor.config.current_lim
[float], the maximum operating current of the motor, in [A]

### odrv0.axis0.motor.config.current_lim_tolerance
[float], exceed the tolerance of the motor's maximum operating current, such as: this value is set to 1.2 means that when the actual current reaches 1.2 times current_lim, the motor will stop and an error will be reported

### odrv0.axis0.motor.config.inverter_temp_limit_lower
[float], the lower limit of axis0 mos drive axle temperature range, the unit is [℃]. When the temperature is higher than this temperature, the maximum allowable current will start to decrease. According to this temperature and inverter_temp_limit_upper, the limit strength is calculated

### odrv0.axis0.motor.config.inverter_temp_limit_upper
[float], axis0 mos drive axle temperature range upper limit, unit is [℃], according to this temperature and inverter_temp_limit_lower, calculate the intensity of limiting motor current

### odrv0.axis0.motor.config.requested_current_range
[float], the current range of the motor running, the unit is [A], the gain of the current sampling op amp is automatically adjusted according to this value, and the configuration needs to be saved and restarted to take effect after setting

### odrv0.axis0.motor.config.current_control_bandwidth
[float], the control bandwidth of the current control loop, which is used to automatically calculate the PI parameters of the current loop. For motors with slower acceleration and deceleration, this parameter should be lower

# odrv0.axis0.controller
### odrv0.axis0.controller.error
[enum], axis0 controller error code
```
ERROR_NONE = 0,
ERROR_OVERSPEED = 0x01,
```
### odrv0.axis0.controller.pos_setpoint
[float], motor target position, the unit is encoder count as the unit, this value will be directly used as the input value in the position control loop

### odrv0.axis0.controller.vel_setpoint
[float], motor target speed, the unit is [rad/s], this value will be directly used as the input value in the speed control loop

### odrv0.axis0.controller.vel_integrator_current
[float], real-time error integral in the speed control loop

### odrv0.axis0.controller.current_setpoint
[float], motor target current, in [A], this value will be directly used as the input value in the current control loop

### odrv0.axis0.controller.vel_ramp_target
[float], the motor speed climb target, the unit is [rad/s], only valid when odrv0.axis0.controller.vel_ramp_enable is set to True

### odrv0.axis0.controller.vel_ramp_enable
[bool], whether to enable the speed ramp function, the speed ramp rate is set by odrv0.axis0.controller.config.vel_ramp_rate

### odrv0.axis0.controller.set_pos_setpoint(pos_setpoint: float, vel_feed_forward: float, current_feed_forward: float)
Set target position, pos_setpoint target position, vel_feed_forward speed feed forward, current_feed_forward current feed forward

### odrv0.axis0.controller.set_vel_setpoint(vel_setpoint: float, current_feed_forward: float)
Set target speed, vel_setpoint target speed, current_feed_forward current feed forward

### odrv0.axis0.controller.set_current_setpoint(current_setpoint: float)
Set target current, current_setpoint target current

### odrv0.axis0.controller.move_to_pos(pos_setpoint: float)
Rotate to the target position in trapezoidal trajectory mode, pos_setpoint target position, with encoder count as the unit

### odrv0.axis0.controller.move_incremental(displacement: float, from_goal_point: bool)
Rotation target distance in trapezoidal trajectory mode, displacement rotation distance, in encoder count as the unit, from_goal_point whether the last set target position is the starting point

### odrv0.axis0.controller.start_anticogging_calibration()
Start anticogg calibration, this function is currently unavailable and is in the verification stage

# odrv0.axis0.controller.config
### odrv0.axis0.controller.config.control_mode
[enum], control mode
```
CTRL_MODE_VOLTAGE_CONTROL = 0,
CTRL_MODE_CURRENT_CONTROL = 1,
CTRL_MODE_VELOCITY_CONTROL = 2,
CTRL_MODE_POSITION_CONTROL = 3,
CTRL_MODE_TRAJECTORY_CONTROL = 4
```

### odrv0.axis0.controller.config.pos_gain
[float], position loop gain

### odrv0.axis0.controller.config.vel_gain
[float], speed loop gain

### odrv0.axis0.controller.config.vel_integrator_gain
[float], velocity loop integral gain

### odrv0.axis0.controller.config.vel_limit
[float], the maximum speed, the unit is [counts/s], when the speed exceeds this value, an error will be reported ERROR_OVERSPEED

### odrv0.axis0.controller.config.vel_limit_tolerance
[float], the tolerance of the maximum speed fluctuation, such as: when this value is set to 1.2, it means that when the speed exceeds the set maximum speed by 1.2 times, it will trigger ERROR_OVERSPEED

### odrv0.axis0.controller.config.vel_ramp_rate
[float], the climb rate when the speed is climbing, the unit is [(counts/s) / s]

### odrv0.axis0.controller.config.setpoints_in_cpr
[bool], whether to enable circular control mode, this mode is useful for continuous incremental position movement. For example, a robot may roll indefinitely, or an extruder motor or conveyor belt may move indefinitely in controlled increments. In normal position mode,pos_setpointWill grow to very large values ​​and lose precision due to floating point rounding

# odrv0.axis0.encoder
### odrv0.axis0.encoder.error
[enum], encoder error code
```
ERROR_NONE = 0,
ERROR_UNSTABLE_GAIN = 0x01,
ERROR_CPR_OUT_OF_RANGE = 0x02,
ERROR_NO_RESPONSE = 0x04,
ERROR_UNSUPPORTED_ENCODER_MODE = 0x08,
ERROR_ILLEGAL_HALL_STATE = 0x10,
ERROR_INDEX_NOT_FOUND_YET = 0x20,
```

### odrv0.axis0.encoder.is_ready
[bool], is the encoder ready

### odrv0.axis0.encoder.index_found
[bool], whether the encoder index signal is detected

### odrv0.axis0.encoder.shadow_count
[int32_t], encoder accumulative count, when the encoder count increases or decreases, this value will accumulate the change of the encoder count

### odrv0.axis0.encoder.count_in_cpr
[int32_t], the value of the encoder cumulative count within the range of cpr

### odrv0.axis0.encoder.interpolation
[float], the current interpolation value of the encoder

### odrv0.axis0.encoder.phase
[float], the current electrical angle calculated by the encoder, the range is -pi~+pi

### odrv0.axis0.encoder.pos_estimate
[float], the current predicted position value, the unit is [counts]

### odrv0.axis0.encoder.pos_cpr
[float], the position value of the current constraint in the cpr range, the unit is [counts]

### odrv0.axis0.encoder.hall_state
[uint8_t], the current Hall signal state, indicated by bit code

### odrv0.axis0.encoder.vel_estimate
[float], the current estimated speed, in [count/s]

### odrv0.axis0.encoder.calib_scan_response
[float], the intermediate value when performing encoder offset calibration, used for debugging

### odrv0.axis0.encoder.set_linear_count(count: int)
Manually set the current encoder count value

# odrv0.axis0.encoder.config
### odrv0.axis0.encoder.config.mode
[enum], encoder type
```
MODE_INCREMENTAL = 0,
MODE_HALL = 1,
MODE_SINCOS = 2,
```

### odrv0.axis0.encoder.config.use_index
[bool], whether to use encoder index signal

### odrv0.axis0.encoder.config.find_idx_on_lockin_only
[bool], whether to detect the index signal only when the lockin is running at a constant speed

### odrv0.axis0.encoder.config.pre_calibrated
[bool], whether the encoder has been calibrated in advance

### odrv0.axis0.encoder.config.zero_count_on_find_idx
[bool], whether to set the index signal position to the position of encoder count 0

### odrv0.axis0.encoder.config.cpr
[int32_t], the number of pulses per revolution of the encoder, pay attention to distinguish it from the number of pulses per revolution (PPR) in the encoder manual, cpr = PPR * 4

### odrv0.axis0.encoder.config.offset
[int32_t], the phase difference between the electrical angle of the encoder and the rotor, this item is automatically updated after the encoder offset calibration

### odrv0.axis0.encoder.config.offset_float
[float], the floating-point part of the phase difference between the encoder and the electrical angle of the rotor, this item is automatically updated after the encoder offset calibration

### odrv0.axis0.encoder.config.enable_phase_interpolation
[bool], whether to enable interpolation of encoder phase based on speed

### odrv0.axis0.encoder.config.bandwidth
[float], encoder update bandwidth, it will take effect immediately after setting, the higher the resolution of the encoder used, the higher this item should be

### odrv0.axis0.encoder.config.calib_range
[float], the required accuracy is checked by the encoder cpr, which is used when the encoder offset calibration is performed, and the maximum error allowed between the movement distance calculated by the encoder's actual output and the motor open-loop step movement distance exceeds this Error will report ERROR_CPR_OUT_OF_RANGE

### odrv0.axis0.encoder.config.calib_scan_distance
[float], the rotation distance of the encoder during offset calibration, the unit is [rad], the larger the value, the higher the calibration accuracy, but the longer the calibration time is

### odrv0.axis0.encoder.config.calib_scan_omega
[float], the rotation speed of encoder offset calibration, the unit is [rad/s]

### odrv0.axis0.encoder.config.idx_search_unidirectional
[bool], whether to run index search only when the direction is set

### odrv0.axis0.encoder.config.ignore_illegal_hall_state
[bool], whether to detect wrong Hall signal

odrv0.axis0.sensorless_estimator
### odrv0.axis0.sensorless_estimator.error
[enum] Non-inductive observer error code
```
ERROR_NONE = 0,
ERROR_UNSTABLE_GAIN = 0x01,
```

### odrv0.axis0.sensorless_estimator.phase
[float], the output phase of the sensorless observer, the unit is [rad]

### odrv0.axis0.sensorless_estimator.pll_pos
[float], the output position of the phase-locked loop of the sensorless observer, the unit is [rad]

### odrv0.axis0.sensorless_estimator.vel_estimate
[float], the speed estimated by the non-inductive observer, the unit is [rad/s]

odrv0.axis0.sensorless_estimator.config
### odrv0.axis0.sensorless_estimator.config.observer_gain
[float], the gain of the sensorless observer, the unit is [rad/s]

### odrv0.axis0.sensorless_estimator.config.pll_bandwidth
[float], the bandwidth of the phase-locked loop of the sensorless observer, in [rad/s]

### odrv0.axis0.sensorless_estimator.config.pm_flux_linkage
[float], motor flux, the unit is [V / (rad/s)], the observer needs to use this parameter to observe, which can be calculated by the formula {5.51328895422 / (* <rpm/v>)}


# odrv0.axis0.trap_traj
# odrv0.axis0.trap_traj.config

### odrv0.axis0.trap_traj.config.vel_limit
[float], the maximum speed in trapezoidal trajectory control mode, the unit is [count/s]

### odrv0.axis0.trap_traj.config.accel_limit
[float], the acceleration when accelerating in trapezoidal trajectory control mode, the unit is [count/s^2]

### odrv0.axis0.trap_traj.config.decel_limit
[float], the acceleration during deceleration in trapezoidal trajectory control mode, the unit is [count/s^2]

### odrv0.axis0.trap_traj.config.A_per_css
[float], current feed forward during acceleration and deceleration in trapezoidal trajectory control mode, the unit is [A/(count/s^2)]

