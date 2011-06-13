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

BOM
----------
12x 0.22µF Capacitors (http://components.arrow.com/part/detail/41292784S7821294N7429)
16x 0.1µF  Capacitors (http://components.arrow.com/part/detail/42167798S7528926N7429)
2x  100µF  Electrolytic Capacitors (http://components.arrow.com/part/detail/41714593S9048589N1432)
2x  2-pin locking headers (0.1"/2.54mm) (http://components.arrow.com/part/detail/4703590S3494260N3303)
5x  4-pin locking headers (0.1"/2.54mm) (http://components.arrow.com/part/detail/4703601S3511738N3303)
1x  2x10 PIN header (http://components.arrow.com/part/detail/4690925S6170934N3303)
1x  5mm LED
8x  0.4 ohm current sense resistors (1W) (http://components.arrow.com/part/detail/37726611S6837442N1082)
5x  1.2k ohm resistors (http://components.arrow.com/part/detail/24590168S9688418N1082)
1x  IRF8714PBF MOSFET (surface mount) (http://components.arrow.com/part/detail/43467223S9550209N3340)
4x  A3992 Motor Controllers (http://components.arrow.com/part/detail/42804152S9226473N6817)

Total cost (in 1-board quantities): ~$30


TODO
----

* General cleanup of schematic
* Fabrication and testing (design still completely theoretical!)
* Use a standard 4-pin MOLEX connector from a PC power supply for both +5 and +12 power (? maybe)
