# Introduction #

This section describes how the adapter can be physically built.

The adapter can be easily implemented on a bread board.

Parts you need
  * [Teensy](http://www.pjrc.com/) 2.0 (with pins if implementing on a breadboard)
  * DB15 female connector (game port)
  * 2 x 2.2k Ohm resistors
  * 220 Ohm resistors
  * 2 x 1 nF capacitors

and below is the full circuit diagram.

![http://adapt-ffb-joy.googlecode.com/files/adaptffbjoy-circuit.png](http://adapt-ffb-joy.googlecode.com/files/adaptffbjoy-circuit.png)

The above circuit diagram is also available as [TinyCad](http://sourceforge.net/projects/tinycad/) design file among the source code files.

The basic buildup is similar to [3DPVert](http://code.google.com/p/sw3dprousb) but there are some additions and modifications to it to get the new features in.

To free the UART TX-pin for sending the force feedback effect MIDI data to the joystick 3DP-Vert's button pins were moved to B0..B3 pins in the AVR. The prototype also has AD-conversion pins setup up for attaching four additional analog controls (potentiometers). They are seen as Rx, Ry and a slider - that combines two pedals (potentiometers).

Below are the pins to connect for the joystick.

| AVR | DB15 | Desc |
|:----|:-----|:-----|
| PB0 | 2    | Button1 |
| PB1 | 7    | Button2 |
| PB2 | 10   | Button3 |
| PB3 | 14   | Button4 |
| PB4 | 11   | X1 (with 2.2k Ohm resistor in series) |
| PB5 | 3    | X2 (with 2.2k Ohm resistor in series) |
| PD0 | 2    | Button1 (INT) |
| PD3 | 12   | MIDI out (with 220 Ohm resistor in series) |
| VCC | 1    | Vcc for joystick |
| GND | 4    | GND for joystick |

Then you likely need the two 1nF capacitors between AVR pins PB4 and PB5 and ground. Some configurations work better without or with different values of these two capacitors. For example, my breadboard setup worked only without them as seen in below picture. See comments-section below on people's experience on these as there seem to even be different versions of the joystick asking for different capacitor setups.

Then for the extra trim pots, connect PF0, PF1, PF4 and PF5 to each trim pot's center connector and GND and Vcc on the ends. These trim pots are completely optional and are not required to be connected for joystick to work. They only provide additional axis on top of the Sidewinder's own four axis.

| AVR | Desc |
|:----|:-----|
| PF0 | Y-rotation axis (Ry) |
| PF1 | X-rotation axis (Rx) |
| PF4 | Pedal1 (Slider-axis) |
| PF5 | Pedal2 (Slider-axis) |

The Pedal1 and Pedal2 are combined to form an axis called "Slider" for the joystick in Windows.

![http://adapt-ffb-joy.googlecode.com/files/adaptffbjoy-breadboard.jpg](http://adapt-ffb-joy.googlecode.com/files/adaptffbjoy-breadboard.jpg)