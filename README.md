# ODrive Breakout Board

## Overview
A custom breakout PCB designed in KiCad to interface the ODrive S1 motor controller with Toronto MetRobotics' electrical system. The ODrive's native 30-pin header uses a connector type that didn't match the team's standard wiring, so this board resolves that mismatch while also consolidating 3 separate encoder interfaces and dual CAN bus connections onto a single unified header — standardizing encoder integration across the robot's motor subsystems. This was an independent (solo) design, built to conform to the team's existing enclosure and mounting constraints for drop-in compatibility.

## Objectives
- Interface the ODrive S1's 30-pin header with the team's standard connector types
- Consolidate multiple encoder interfaces onto a single unified IO header
- Fit within the robot's existing enclosure and mounting footprint without requiring mechanical redesign
- Validate all connections before team-wide deployment

## Key Components
- **Motor Controller Interface** — ODrive S1 (S30B-PUDSS-1, 30-pin connector)
- **Encoder Interfaces** — RIBO Hall encoder, NEO BLDC V1.1 encoder, AMT212B-V absolute encoder (RS485)
- **CAN Bus** — dual CAN connections (CAN 1 / CAN 2)
- **Thermistor Sensing** — dedicated THERM+/THERM- test pins

## Connectors
- **RIBO Hall Encoder** — 5-pin (5V, GND, HALL_A, HALL_B, HALL_C)
- **NEO BLDC Encoder** — 6-pin (GND, HALL_C, HALL_B, HALL_A, THERMISTOR+, 5V)
- **AMT212B-V Absolute Encoder** — 4-pin (5V, RS485_A, RS485_B, GND)
- **CAN 1 / CAN 2** — CAN_H / CAN_L pairs
- **Unified IO Header** — 30-pin, mirrors the ODrive S1's native connector pinout (SPI, RS485, Hall/encoder signals, thermistor, UART, error, direction/step/PWM, dual CAN)
- **Test Pins** — 30-pin 2.54mm header duplicating all unified header signals for bench testing

## Files
- `ODrive_S1_Breakout_Board.kicad_pro` — project file
- `ODrive_S1_Breakout_Board.kicad_sch` — full schematic (encoder connectors, CAN connectors, unified IO header, test pins)
- `ODrive_S1_Breakout_Board.kicad_pcb` — PCB layout
- `gerbers/` — fabrication output (Gerber, drill files)
- `ODrive_S1_Breakout_Board_3D.png` — 3D rendered board preview

## Design Notes
- **Connector Consolidation**: The board maps the RIBO Hall, NEO BLDC, and AMT212B-V encoder connectors, along with both CAN buses, onto a single 30-pin unified header matching the ODrive S1's native connector layout — allowing any of the three encoder types to be swapped in without rewiring the ODrive side.
- **Mechanical Fit**: Board outline and mounting hole placement were designed against the team's existing enclosure, so the board drops directly into the robot's chassis without modification.
- **Test Access**: A duplicate 30-pin test header breaks out every unified header signal for bench-level multimeter/continuity testing before final installation.
- **Status**: Soldered and tested using multimeter and continuity testing prior to team-wide deployment — all connections confirmed reliable.

## Version
- **Board Revision**: V1.2
- **Designed by**: Tristan Hsiung, Toronto MetRobotics
