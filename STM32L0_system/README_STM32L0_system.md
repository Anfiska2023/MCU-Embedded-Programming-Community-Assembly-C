# STM32L0 Modular Development & Prototyping Platform

Full embedded hardware and software project based on the STM32L0 family.

This repository section contains a reusable STM32L0 development platform, a DB37 connection / breakout board, STM32 firmware, a Windows configuration terminal, and project documentation.

The platform was designed for firmware development, peripheral testing, sensor integration, analog and digital experiments, and rapid prototyping.

---

## Project Overview

The system is built around an STM32L0 microcontroller board and a separate DB37 connection board.

The main controller board provides:

- STM32L062K8T6 MCU
- SWD programming and debugging
- USB
- UART / USART
- SPI
- I2C
- GPIO / EXTI
- ADC inputs
- DAC output
- Motion sensor input
- IR receiver interface
- I2C GPIO expansion
- Configurable jumpers
- 12 V input and local 3.3 V regulation
- DB37 expansion connection

The DB37 connection board breaks the MCU and peripheral signals out to accessible terminal blocks and connectors for laboratory work and prototyping.

---

## Repository Contents

```text
STM32L0_system/
│
├── CONNBOARD/
│   └── Connection-board project files
│
├── ST32L062/
│   └── Main STM32L0 board project files
│
├── 0621.pdf
│   └── Main STM32L0 board schematic
│
├── CONN_BOARD.pdf
│   └── DB37 connection-board schematic, pinout and jumper information
│
├── STM32L0_Modular_Development_Platform_Complete_Project_WITH_PHOTOS.docx
│   └── Full editable project documentation
│
├── STM32L0_Modular_Development_Platform_Complete_Project_WITH_PHOTOS.pdf
│   └── Full project documentation in PDF format
│
├── TerminalVS2019.zip
│   └── Windows C# / Visual Studio serial configuration and diagnostic terminal
│
└── firmwarestm32L062.zip
    └── STM32L062 embedded firmware
```

---

## Hardware Architecture

```text
External Sensors / Peripherals
            |
            v
   STM32L0 Main Board
            |
       DB37 Interface
            |
            v
 Connection / Breakout Board
            |
            +--> GPIO
            +--> ADC / DAC
            +--> UART
            +--> SPI
            +--> I2C
            +--> SWD
            +--> USB
            +--> Power / Test Connections
```

The goal is to keep the MCU board reusable while allowing external circuits and test equipment to be connected through the dedicated connection board.

---

## Embedded Firmware

The included STM32 firmware is an independent project developed for this platform.

Main functions include:

- Motion detection using EXTI
- Configurable motion logic
- DAC output control
- High / low operating levels
- RTC-based hold timer
- STM32L0 Data EEPROM storage
- 32-bit device ID storage
- UART command interface
- Heartbeat / SystemTick control
- Motion-event message control
- DAC test functions
- Runtime configuration through serial commands

Example UART commands:

```text
<,INFO,>
<,HELP,>

<,SETID,NNNNNNNN,>
<,GETID,>
<,EERESET,>

<,SETDUR,MM,>
<,GETDUR,>

<,SETHI,PP,>
<,GETHI,>

<,SETDIM,PP,>
<,GETDIM,>

<,MOTION,MODE,INV,SAVE,>
<,MOTION,MODE,NORM,SAVE,>
<,GETMOTION,>

<,TRIG,>
<,TRIGH,>
<,TRIGL,>

<,DAC,PP,>
<,DACTEST,TT,>

<,GETREMAIN,>
<,PRINTCFGLN,>
```

---

## Windows Configuration Terminal

`TerminalVS2019.zip` contains the Windows PC application developed in C# / Visual Studio.

The application communicates with the STM32 through a serial COM port and provides a graphical interface for configuration and diagnostics.

Main features include:

- COM-port selection
- Baud-rate, parity, stop-bit and data-bit configuration
- Text and Hex modes
- Console display
- Manual command transmission
- Predefined command groups
- Read / Write configuration controls
- Device ID read / write
- High-level setting
- Low-level setting
- Motion hold-time setting
- Diagnostic handshake with the MCU
- Log saving
- Console clear
- Text zoom
- UART response parsing

The PC application does **not** flash firmware into the STM32.  
It configures and reads operating parameters through the UART command protocol.

---

## Typical System Flow

```text
Motion Sensor / External Input
            |
            v
        STM32L0
            |
      Embedded Firmware
            |
      UART Command Protocol
            |
        USB-UART / COM
            |
            v
   Windows C# Terminal
```

The terminal can modify parameters that are stored in the MCU's internal Data EEPROM, allowing configuration to remain available after power cycling.

---

## Hardware Documentation

The PDF and Word documentation include:

- Project overview
- System architecture
- Main STM32L0 board description
- DB37 expansion concept
- Main-board schematic
- Connection-board schematic
- Connection-board pinout
- Jumper configuration
- Firmware overview
- PC-terminal overview
- Photographs of the assembled hardware

For a quick overview, start with:

```text
STM32L0_Modular_Development_Platform_Complete_Project_WITH_PHOTOS.pdf
```

---

## Assembled Hardware

The hardware has been designed, manufactured, assembled, and used as a working development platform.

The complete system consists of:

1. Main STM32L0 controller board
2. DB37 connection / breakout board
3. Embedded STM32 firmware
4. Windows serial configuration terminal

---

## Development Purpose

This project was created as a reusable embedded development platform rather than a single-purpose demonstration board.

It can be used for experiments and development involving:

- GPIO
- EXTI
- ADC
- DAC
- UART
- SPI
- I2C
- USB
- Motion sensors
- External modules
- Firmware testing
- Serial configuration tools

---

## Source-Code Note

The firmware included in this repository is an independent public project.

A different version of this hardware platform has also been used in a real engineering application. Any employer-related or proprietary firmware is intentionally excluded from this repository.

Only source code and documentation that are safe to publish are included here.

---

## Suggested Starting Point

If you are reviewing the project for the first time:

1. Open the full project PDF.
2. Review `0621.pdf` for the main STM32L0 schematic.
3. Review `CONN_BOARD.pdf` for the breakout-board design and pinout.
4. Open `firmwarestm32L062.zip` to review the STM32 firmware.
5. Open `TerminalVS2019.zip` to review the Windows configuration tool.
6. Use the DB37 pinout and jumper documentation before connecting external hardware.

---

## Project Classification

**Full Embedded Project**

STM32L0 Modular Development & Prototyping Platform  
Hardware + Firmware + UART Protocol + Windows PC Configuration Tool

---

## Status

Current public version includes:

- Completed hardware
- Assembled boards
- STM32 firmware
- C# configuration terminal
- Schematics
- Pinout documentation
- Jumper documentation
- Project PDF / Word documentation

Further examples and firmware modules can be added without redesigning the core hardware platform.
