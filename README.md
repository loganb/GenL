'GenL' Electronics
=================

Introduction
------------

While waiting for the Generation 6 electronics to be in stock again, I decided to working on a motor controller board for my Prusa Mendel, I decided to work on my own design as a practice exercise. Based around the Allegro 3992 motor controller, this board is the result. 

The end design will consist of two boards: A motor/heater controller board and a Teensy 2.0-based controller board. The two are connected via a 20-pin IDC ribbon cable. The USB connector on the Teensy provides +5 to the entire system. 

Advantages
----------

* Per-Driver Software Current Control: The a3992 has an internal current limiter based off an (optionally) external voltage reference. This board exposes each driver&quot;s  external Vref pin to the driving microcontroller via an RC network so that it may be accurately set (within 1%) via PWM. (no trim pots)
* Fewer boards than Generation 3 electronics: This is a two board solution, one motor driver board and one microcontroller board. While the Gen 6 electronics do fit on a single board, this solution uses less PCB space than the Gen 3 electronics but is still editable with the free version of Eagle CAD
* Low distinct part count: Only about 10 distinct parts are needed and there are fewer than 70 total parts on the motor controller board
* Microstepping: The a3992 supports 64 microsteps for low noise and precise operation
* SPI interface: Easily interfaces with microcontrollers via SPI
* Through Hole Layout: Easily assembly by the hobbyist (SMD layout likely forthcoming)
* Improved heat dissipation (?): This board has more area devoted to heat dissipation; I believe it will have better thermal perf than other boards
* Interconnection safety: 20-pin microcontroller connector can be connected in either direction and function properly, reducing the risk damage due to user error
* USB bus powered for low voltage electronics

TODO
----

* Label traces and general cleanup of schematic
* Board heater sub-module (need to fit MOSFET and connector onto the board)
* Proper power connectors (motor power is currently a pin header)
* Fabrication and testing (design still completely theoretical!)
* Use a standard 4-pin MOLEX connector from a PC power supply for both +5 and +12 power
