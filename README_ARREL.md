
Top view looking down at the Creality 4.2.2 mainboard 10 pin IDC display connector:
--------    -------
|  2  4  6  8 10  |
|  1  3  5  7  9  |
-------------------

Pin  1: 5V   5V
Pin  2: GND  0V
Pin  3: UART1 3.3V
Pin  4: UART1 3.3V
Pin  5: BEEP 0V
Pin  6: 3.3V (Low current)
Pin  7 PA4: ENC Phase A 0.87V
Pin  8 PA5: ENC Button 3.3V
Pin  9 PA6: ENC Phase B 1.0V
Pin 10: NC 1.0V


Measured Voltages at display connector with no display connected 
--------    -------
|  2  4  6  8 10  |
|  1  3  5  7  9  |
-------------------
Pin  1: 5V ( was power for display)
Pin  2: 0V
Pin  3: 3.3V
Pin  4: 3.3V
Pin  5: 0V
Pin  6: 3.3V
Pin  7: 0.87V
Pin  8: 3.3V
Pin  9: 1.0V
Pin 10: 1.0V


Based on voltage measurements and the Creality 4.2.2 technical layout, here is the complete mapping of the physical pins to their Microcontroller (MCU) assignments:

Creality 4.2.2 10-Pin Display Header (EXP3)
Pin #	Voltage	| MCU Pin	Functional Name	| Stock Printer Purpose
Pin 1	5.00V	VCC	+5V Rail	Main Display Power
Pin 2	0.00V	GND	Ground	System Common Ground
Pin 3	3.30V	PB11	UART2_RX	Serial Input (Now G-Code In)
Pin 4	3.30V	PB10	UART2_TX	Serial Output (Now G-Code Out)
Pin 5	0.00V	PB0	BEEPER	Piezo Buzzer Signal
Pin 6	3.30V	VCC	+3.3V Rail	Logic Power (Low Current)
Pin 7	0.87V	PA4	ENC_A	Rotary Encoder Phase A
Pin 8	3.30V	PA5	ENC_BTN	Encoder Push Button (Pull-up)
Pin 9	1.00V	PA6	ENC_B	Rotary Encoder Phase B
Pin 10	1.00V	NC	NC	Not Connected (Floating)

DO NOT CONNECT CONSOLE MONITOR AND EXPECT OCTOPRINT TO CONNECT - default esp32c3 console (monitor) uses UART0 as well as Serial Port (octoprint). 

# octoprint log from a custom stm32 firmware connecting via wifi bridge using default uart before making headless:
From file: /home/arrel/.octoprint1/logs/octoprint.log
2026-03-04 21:09:37,541 - octoprint.server - INFO - Serial port list was updated, refreshing the port list in the frontend
2026-03-04 21:09:45,319 - octoprint.util.comm - INFO - Changing monitoring state from "Offline" to "Opening serial connection"
2026-03-04 21:09:45,320 - octoprint.util.comm - INFO - Connecting to port /home/arrel/EnderBridge1, baudrate 115200
2026-03-04 21:09:45,327 - octoprint.util.comm - INFO - Changing monitoring state from "Opening serial connection" to "Connecting"
2026-03-04 21:09:45,329 - octoprint.util.comm - INFO - M110 detected, setting current line number to 0
2026-03-04 21:09:45,364 - octoprint.util.comm - INFO - M110 detected, setting current line number to 0
2026-03-04 21:09:45,367 - octoprint.util.comm - INFO - Changing monitoring state from "Connecting" to "Operational"
2026-03-04 21:09:45,387 - octoprint.util.comm - INFO - M110 detected, setting current line number to 0
2026-03-04 21:09:45,480 - octoprint.util.comm - INFO - Printer reports firmware name "Marlin bugfix-2.1.x (Mar  4 2026 21:05:22)"
2026-03-04 21:09:45,480 - octoprint.util.comm - INFO - Firmware info line: FIRMWARE_NAME:Marlin bugfix-2.1.x (Mar  4 2026 21:05:22) SOURCE_CODE_URL:github.com/MarlinFirmware/Marlin PROTOCOL_VERSION:1.0 MACHINE_TYPE:Creality3D KINEMATICS:Cartesian EXTRUDER_COUNT:1 UUID:cede2a2f-41a2-4748-9b12-c55c62f367ff
2026-03-04 21:09:45,482 - octoprint.plugins.firmware_check - INFO - Your printer's firmware is a development build of Marlin (build date 20260304). It might be more unstable than a release version and should be kept up-to-date.. More information at https://faq.octoprint.org/warning-firmware-development
2026-03-04 21:09:45,493 - octoprint.util.comm - INFO - Firmware states that it supports temperature autoreporting
2026-03-04 21:09:45,549 - octoprint.util.comm - INFO - Firmware sent the following capability report:
  SERIAL_XON_XOFF: not supported
  BINARY_FILE_TRANSFER: not supported
  EEPROM: not supported
  VOLUMETRIC: supported
  AUTOREPORT_POS: not supported
  AUTOREPORT_TEMP: supported
  PROGRESS: not supported
  PRINT_JOB: supported
  AUTOLEVEL: not supported
  RUNOUT: not supported
  Z_PROBE: not supported
  LEVELING_DATA: not supported
  BUILD_PERCENT: not supported
  SOFTWARE_POWER: not supported
  TOGGLE_LIGHTS: not supported
  CASE_LIGHT_BRIGHTNESS: not supported
  EMERGENCY_PARSER: not supported
  HOST_ACTION_COMMANDS: supported
  PROMPT_SUPPORT: supported
  SDCARD: not supported
  REPEAT: not supported
  SD_WRITE: not supported
  AUTOREPORT_SD_STATUS: not supported
  LONG_FILENAME: not supported
  LFN_WRITE: not supported
  CUSTOM_FIRMWARE_UPLOAD: not supported
  EXTENDED_M20: not supported
  THERMAL_PROTECTION: supported
  MOTION_MODES: not supported
  ARCS: supported
  BABYSTEPPING: not supported
  EP_BABYSTEP: not supported
  CHAMBER_TEMPERATURE: not supported
  COOLER_TEMPERATURE: not supported
  MEATPACK: not supported
  CONFIG_EXPORT: not supported
2026-03-04 21:09:45,573 - octoprint.server - INFO - Autorefresh of serial port list stopped
2026-03-04 21:14:13,176 - octoprint.server.heartbeat - INFO - Server heartbeat <3
