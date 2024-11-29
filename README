# Water Reservoir System Controller for Irrigation
## Overview
This project involves designing an Embedded System Controller for a terraced vineyard irrigation system that prioritizes energy efficiency. The controller manages a water reservoir, a pump, and a system of valves to distribute water to three irrigation zones at varying elevations. The system also monitors the reservoir's water depth and provides user control through a UART terminal interface.

This README outlines the key functionality, operation modes, and requirements for implementing and demonstrating the system.

## System Components
1. Water Reservoir

- Capacity: 94,000 gallons
- Filled via an inlet pipe from an underground spring with a head of 40 feet.
Pump and Motor

Moves water from the reservoir to irrigation zones.
Controlled via a PWM signal for variable speeds.
Zones

Zone 1:
Elevation: 25 feet
Water required: 50,000 gallons/day
Minimum RPM: 70
Zone 2:
Elevation: 50 feet
Water required: 30,000 gallons/day
Zone 3:
Elevation: 60 feet
Water required: 14,000 gallons/day
Sensors

Ultrasonic sensor: Measures reservoir depth and displays percentage (0–99%).
Servo Valve System

Directs water to one zone or inlet at a time.
LED Indicators

Green LED: Indicates operating mode (ON = RUN, Flashing = Setup Mode ready).
RGB LED: Displays specific colors for different pipeline operations:
Purple: Inlet pipe
Other colors: Zone pipelines
User Controls

UART Terminal: Inputs configuration and displays system status.
Potentiometer: Allows manual control of motor speed in Run Mode if enabled.
Operation Modes
1. Setup Mode
Entered by resetting the MCU (Nucleo board).
Green LED: OFF during configuration.
Pump: Remains OFF.
Tasks:
Set Motor Speed PWM
For each connection (Inlet, Zone 1, Zone 2, Zone 3):

Select one of the following PWM options:
0: Manual control via potentiometer
1: 60% PWM
2: 80% PWM
3: 99% PWM
Set Wall Clock Times

Input start and stop times for:
Inlet pipe operation.
Irrigation for each zone.
Ensure times do not overlap (except where one stop time equals the next start time).
Demo Scaling

The 24-hour day is scaled to 2.4 real-time minutes.
Each "hour" equals 6 seconds in real-time.
Transition to Run Mode:
Once configuration is complete, the system flashes the Green LED.
Press the Blue B1 Button to enter Run Mode.
2. Run Mode
Green LED: Remains ON during operation.
Pump operation follows the sequence of wall clock times configured in Setup Mode.
Tasks:
Inlet Pipe Operation

Fill reservoir using the inlet pipe first.
Stop filling when reservoir reaches maximum depth.
Irrigation Sequence

Direct water to each zone in the configured order and time intervals.
Adjust pump speed (RPM) based on the zone's head and selected PWM.
Monitor Reservoir Depth

Display water depth percentage on a seven-segment display.
Stop the pump if the reservoir depth reaches 0%.
Terminal Updates

Display the following information at each wall clock update or special event:
mathematica
Copy code
Wall-Clock Time | Zone/Inlet | Motor Speed %PWM | Motor RPM | Reservoir Depth (%)
Special Events:
Reservoir Empty:
Stop the pump immediately.
Indicate "RESERVOIR EMPTY" on the terminal.
RGB LED cycles through RED, GREEN, BLUE.
Green LED: OFF.
System halts until a reset is performed.
Key Features
Energy Efficiency: Optimizes motor speed based on the head requirements of each zone.
Safety: Prevents pump operation when the reservoir is empty.
Scalability: Configurable wall clock scheduling and PWM settings allow testing of different scenarios.
Visualization: Real-time status updates via UART and seven-segment displays.
Demo Requirements
Setup Mode

Configure PWM settings and wall clock times for each connection.
Ensure logical sequencing of operations.
Run Mode

Demonstrate scaled 24-hour operation within 2.4 minutes.
Show proper transitions between inlet filling and irrigation.
Monitor and display system status updates on the terminal.
Special Event Handling

Test the system’s response to an empty reservoir scenario.
Additional Notes
System Curves and RPM: The RPM for each zone must align with the required head and flow rates to ensure water reaches the intended elevation efficiently.
Scaled Time: Ensure all timing logic reflects the 24-hour-to-2.4-minute scaling factor during the demo.
Code Implementation: Write modular and well-documented code to facilitate debugging and system maintenance.
