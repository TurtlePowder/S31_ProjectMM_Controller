ProjectMM ESP32-S31 Controller

Custom controller board for ProjectMM, built around the ESP32-S31.

The board is designed for audio-reactive lighting applications, providing dual I²S microphone inputs and 16 independent outputs for LED strips.

Features
ESP32-S31 controller
2× I²S microphone inputs
16× LED strip outputs
USB-C connection
12 V screw-terminal power input
On-board 12 V → 5 V regulation
On-board 5 V → 3.3 V regulation
5 V relay controlled by GPIO38
Reset button
Boot button
Power input protection and filtering
USB 2.0 connection for programming and communication
LED Outputs

The board provides 16 outputs for controlling LED strips:

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

These outputs are intended to be used by ProjectMM for independently controlling up to 16 LED strips.

Audio Input

Two I²S microphone interfaces are provided for audio-reactive effects.

ProjectMM can use the audio input for effects such as:

Volume response
Beat detection
Frequency analysis
Bass response
Mid and high-frequency effects
Stereo/dual-channel processing
Power

The controller supports two power/connection options.

12 V Screw Terminal

External 12 V power can be connected through the screw terminal.

The board includes input protection and regulation for the required 5 V and 3.3 V rails.

USB-C

USB-C provides a connection for:

Programming
USB communication
Powering the controller during development

When using both USB-C and the external 12 V input, make sure the power configuration is suitable for the intended setup.

Relay Output

A 5 V relay is controlled through:

GPIO38

The relay is driven through a transistor stage, allowing ProjectMM to switch an external load.

Controller

The main MCU is an ESP32-S31, providing the processing and connectivity required for ProjectMM.

The controller handles:

LED output generation
Audio acquisition
Audio-reactive processing
ProjectMM communication
Relay control
USB communication
ProjectMM

This board was designed as a dedicated hardware controller for ProjectMM.

A typical setup looks like:

                    ProjectMM
                        |
                  ESP32-S31
                        |
        +---------------+---------------+
        |               |               |
      I²S MIC         I²S MIC        LED Outputs
        |               |               |
        +---------------+       +-------+-------+
                                |       |       |
                               LED1    LED2    ... LED16
                        
                        |
                     GPIO38
                        |
                     5V Relay
Power Architecture
12 V Input
    |
    +---- Protection
    |
    +---- 5 V Regulator ----> 5 V Relay
    |                     \
    |                      +--> USB / peripherals
    |
    +---- 3.3 V Regulator --> ESP32-S31
Hardware

The PCB includes:

ESP32-S31
USB-C connector
16 LED outputs
Dual I²S microphone interface
12 V screw-terminal input
5 V buck regulator
3.3 V regulator
5 V relay
Relay driver circuit
Reset and Boot buttons
Input protection
Power filtering
Status

Hardware designed for use with ProjectMM.

Firmware and ProjectMM integration are developed separately.

Disclaimer

Check the required power supply and total LED-strip current before connecting the controller to an installation. The power supply, PCB traces, connectors, and wiring must all be appropriately sized for the connected LED strips.
