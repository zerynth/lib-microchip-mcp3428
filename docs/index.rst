****************************
Microchip MCP3426/3427/3428
****************************
.. _MCP3426: http://www.microchip.com/wwwproducts/en/MCP3426
.. _MCP3427: http://www.microchip.com/wwwproducts/en/MCP3427
.. _MCP3428: http://www.microchip.com/wwwproducts/en/MCP3428

The MCP3426/3427/3428 devices are multichannel low-noise, high accuracy delta-sigma
Analog-to-Digital Converters (ADC) with differential inputs and up to 16 bits of resolution.
The devices feature an on-board precision 2.048 V reference voltage, a Programmable Gain Amplifier (PGA) 
and use a two wire I2C serial interface.

MPC3426 and MCP3427 devices have two differential input channels and the MCP3428 has four differential input channels.
All electrical properties of these three devices are the same except the differences in number of input channels
and I2C address selection options. More information at Microchip dedicated pages MCP3426_, MCP3427_, MCP3428_.

===================
 Technical Details
===================

* 16-bit resolution
* 2 (MCP3426, MCP3427) or 4 (MCP3428) differential input channels
* On-Board Voltage Reference
* On-Board PGA, gains of 1, 2, 4 or 8
* Programmable Date Rate
* Supply Voltage (Vdd): from 2.7 V to 5.5 V
* Temperature range: -40°C to +125°C

Here below, the Zerynth driver for the Microchip MCP3426/3427/3428.

.. include:: __toc.rst
