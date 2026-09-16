A dedicated controller board for ProjectMM, designed to drive 16 LED strips with audio-reactive effects.

The board is based on an ESP32-S3-WROOM-3 and combines audio input, LED control, flexible power input, and an additional relay output in a compact controller.

Features
🎛️ ESP32-S3-WROOM-3 controller
🎤 2× I²S microphone inputs for audio-reactive lighting
💡 16 independent LED outputs
PWM_1 – PWM_16
Designed for controlling 16 LED strips
🔌 USB-C input
Power and USB connectivity
USB 2.0 interface
⚡ 12 V screw-terminal power input
On-board protection fuse
Reverse/transient protection
🔋 On-board voltage regulation
12 V → 5 V
5 V → 3.3 V
🔁 5 V relay output
Controlled from GPIO38
Useful for switching external equipment or accessories
🔘 Reset button
🔘 Boot button
🧪 Exposed test/programming interfaces
🛡️ Power filtering and protection components
LED Outputs

The controller provides 16 outputs for LED strips:

Output	GPIO
PWM_1	GPIO2
PWM_2	GPIO3
PWM_3	GPIO4
PWM_4	GPIO5
PWM_5	GPIO6
PWM_6	GPIO7
PWM_7	GPIO8
PWM_8	GPIO9
PWM_9	GPIO10
PWM_10	GPIO11
PWM_11	GPIO12
PWM_12	GPIO13
PWM_13	GPIO14
PWM_14	GPIO15
PWM_15	GPIO16
PWM_16	GPIO17

The outputs are intended to be used by ProjectMM for independently controlling the connected LED strips.

Audio

The board includes two I²S microphone connections, allowing ProjectMM to use audio input for reactive lighting effects.

This makes it possible to build effects based on things such as:

Volume
Bass / low frequencies
Mid frequencies
Treble / high frequencies
Beat detection
Stereo or dual-channel audio processing

The exact microphone configuration and software support depend on the ProjectMM firmware.

Power

The controller supports two primary power/connection methods.

12 V screw terminal

A screw terminal provides the main external power input.

The 12 V input passes through protection and regulation circuitry before being converted to the voltages required by the controller and peripherals.

USB-C

USB-C provides an alternative power and USB connection for development and configuration.

Important: The USB-C and external power input should be treated carefully when powering the board simultaneously. Check the hardware design and intended power configuration before connecting multiple power sources.

Relay

A 5 V relay is connected to:

GPIO38

The relay can be controlled by ProjectMM and can be used for external 5 V switching applications.

The relay interface is isolated from the ESP32 GPIO through the board's transistor driver circuitry.

ESP32

The main controller is an ESP32-S3-WROOM-3.

It provides:

Wi-Fi
Bluetooth LE
USB
Hardware PWM
I²S
Multiple GPIOs
Sufficient processing power for real-time LED and audio processing
ProjectMM

This hardware is intended specifically as a controller platform for ProjectMM.

A typical setup is:

                 ┌─────────────────────┐
                 │     ProjectMM       │
                 │                     │
                 │     ESP32-S3        │
                 └──────────┬──────────┘
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          I²S MIC        I²S MIC       GPIO/PWM
             │              │              │
             ▼              ▼              ▼
          Audio L         Audio R      16 LED Outputs
                                           │
                    ┌──────────────────────┼───────┐
                    ▼       ▼       ▼      ▼       ▼
                   LED1    LED2    LED3   ...    LED16
Hardware

The schematic includes:

ESP32-S3-WROOM-3
USB-C connector
16 LED control outputs
Dual I²S microphone interface
12 V input terminal
USB-C power input
5 V buck regulator
3.3 V regulator
Relay driver
5 V relay
Reset and Boot buttons
Input/output filtering
Power protection
Status

🚧 Hardware / ProjectMM controller

This repository contains the hardware design for the ProjectMM controller. Firmware support and additional documentation can be added as the project develops.

Disclaimer

This is a custom hardware design. Verify the power requirements, LED-strip current, connector wiring, and relay load ratings before connecting hardware.

In particular, the controller's 12 V input and the current required by 16 LED strips should be sized appropriately for the intended installation. The PCB should not be assumed to supply the total LED-strip current unless the power path and connectors have been designed for that load.
