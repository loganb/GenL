'GenL' Electronics
=================

Introduction
------------

While waiting for the Generation 6 electronics to be in stock again, I decided to working on a motor controller board for my Prusa Mendel, I decided to work on my own design as a practice exercise. Based around the Allegro 3992 motor controller, this board is the result. 

The end design will consist of two boards: A motor/heater controller board and a Teensy 2.0-based controller board. The two are connected via a 20-pin IDC ribbon cable. The USB connector on the Teensy provides +5 to the entire system. 

For board and schematic screenshots, see: https://github.com/loganb/GenL/wiki

For more information, see the GenL blog: http://genl.posterous.com/

Advantages
----------

* Per-Driver Software Current Control: The a3992 has an internal current limiter based off an (optionally) external voltage reference. This board exposes each driver's  external Vref pin to the driving microcontroller via an RC network so that it may be accurately set (within 1%) via PWM on the microcontroller. Thus, this board does not need trim pots to set the motor currents; it can be done entirely in software. 
* Fewer boards than Generation 3 electronics: This is a two board solution, one motor driver board and one microcontroller board. While the Gen 6 electronics do fit on a single board, this solution uses less PCB space than the Gen 3 electronics but is still editable with the free version of Eagle CAD. For Gen 6 sized boards, small batch fabrication costs jump from ~$3/board to ~$10/board. 
* Low distinct part count: Only 11 distinct parts are needed and there are fewer than 60 total parts on the motor controller board
* Microstepping: The a3992 supports 64 microsteps for low noise and precise operation. This yields a theoretical accuracy of ~9 microns on X and Y
* SPI interface: Easily interfaces with microcontrollers via SPI
* Through Hole Layout: Easily assembly by the hobbyist
* Improved heat dissipation (?): This board has more area devoted to heat dissipation; I believe it will have better thermal perf than other boards, and the motor controllers should last longer and be able to run at higher currents
* Interconnection safety: 20-pin microcontroller connector can be connected in either direction and function properly, reducing the risk damage due to user error
* USB bus powered for low voltage electronics

BOM (Driver)
------------
* 20x 0.22µF Capacitors (http://components.arrow.com/part/detail/41292784S7821294N7429)
* 8x 0.1µF  Capacitors (http://components.arrow.com/part/detail/42167798S7528926N7429)
* 2x  100µF  Electrolytic Capacitors (http://components.arrow.com/part/detail/41714593S9048589N1432)
* 1x  Screw Terminal (http://components.arrow.com/part/detail/29554647S5460692N3303)
* 2x  2-pin locking headers (0.1"/2.54mm) (http://components.arrow.com/part/detail/4703590S3494260N3303)
* 5x  4-pin locking headers (0.1"/2.54mm) (http://components.arrow.com/part/detail/4703601S3511738N3303)
* 1x  2x10 pin header (http://components.arrow.com/part/detail/4690939S2927515N3303)
* 4x  5mm LED
* 8x  0.4 ohm current sense resistors (1W) (http://components.arrow.com/part/detail/37726611S6837442N1082)
* 6x  1.2k ohm resistors (http://components.arrow.com/part/detail/47563839S3426682N1174)
* 2x  IRF8714PBF MOSFET (surface mount) (http://components.arrow.com/part/detail/43467223S9550209N3340)
* 4x  A3992 Motor Controllers (http://components.arrow.com/part/detail/42804152S9226473N6817)

Total cost (in 1-board quantities): ~$30

BOM (Controller)
----------------

* 1x Teensy 2.0 (http://www.pjrc.com/store/teensy_pins.html)
* 4x 1.2k ohm resistors
* 4x 2µF Capacitors (http://components.arrow.com/part/detail/41357791S7970027N1024)
* 3x 0.22µF Capacitors, Axial (http://components.arrow.com/part/detail/41292784S7821294N7429)
* 3x 270 ohm resistors (http://components.arrow.com/part/detail/44289058S9568004N5665)
* 2x 100k ohm resistor (http://components.arrow.com/part/detail/24613340S2290496N1082)
* 2x 4.7k ohm resistor
* 3x 5-pin locking headers (http://components.arrow.com/part/detail/3064683S8031236N5665)
* 2x 2-pin locking headers (http://components.arrow.com/part/detail/4703590S3494260N3303)
* 1x 2x10 pin header (http://components.arrow.com/part/detail/4690939S2927515N3303)
* 3x Pin Socket (http://components.arrow.com/part/detail/2700795S3633656N1004)

Cost: ~$26

BOM (Not on PCB)
----------------
* 3x Optointerruptors (http://components.arrow.com/part/detail/690701S2637435N3506)
* 1x 20-conductor Ribbon (http://components.arrow.com/part/detail/2520919S3684624N3321)
* 2x 20-conductor Female Plugs (http://components.arrow.com/part/detail/1318974S3517474N3321)
* 2x Thermistor (http://components.arrow.com/part/detail/42078290S9672476N9769)
* 1x Power Resistor 8r
* 43x KK Female crimp contacts (http://components.arrow.com/part/detail/4779606S3155738N3303)
* 3x 5-pin KK locking housing (http://components.arrow.com/part/detail/4702036S3156044N3303)
* 5x 4-pin KK locking housing
* 4x 2-pin KK locking housing
* (More TBD: Misc Wire)

Cost: ~$8

NOTE: Ribbon cable is sold in rolls of 30m


Release Notes
-------------

New in v2:

* Completely new driver board layout with large ground planes on both sides for improved heat dissipation
* Redesigned boards now include connections for 2 thermistors and heating circuits for heated bed support
* Half the drivers are on a second SPI bus and connected to the Teensy's USART. Drivers can now be programmed two at a time
* Redesign of the inter-board connector to simplify (most) traces
* Larger and shorter power traces on the driver board
* NOTE: Driver/Board combinations are NOT pin-compatible across major version numbers


TODO
----

* Fabrication and testing (design still completely theoretical!)
* SMD layout for professional fabrication
* Find appropriate female connectors for the locking pin headers
* Find a replacement for the IRF8714PBF that is tolerant of +36V
