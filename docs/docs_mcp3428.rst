.. module:: mcp3428

**************************
 MCP3426/3427/3428 Module
**************************
.. _datasheet: http://ww1.microchip.com/downloads/en/DeviceDoc/22226a.pdf

This module contains the driver for Microchip MCP3426/3427/3428 multichannel analog to digital converters with
I2C interface (datasheet_).

Example: ::
        
        from microchip.mcp3428 import MCP3428
        
        ...
        
        mcp = mcp3428.MCP3428(I2C0, addr = 0x6A)
        mcp.set(ch = 1, pga = 1)
        value1 = mcp.get_raw_data()
        
        mcp.set(ch = 2, pga = 2)
        value2 = mcp.get_raw_data()
    
    
===============
 MCP3428 class
===============


.. class:: MCP3428(i2cdrv, addr = 0x68, clk = 400000)

    Creates an instance of the MCP3428 class. This class allows the control of all MCP3426, MCP3427, and MCP3428 devices.
    
    :param i2cdrv: I2C Bus used '(I2C0, ...)'
    :param addr: Slave address, default 0x68
    :param clk: Clock speed, default 400 kHz
    


    
.. _set:

.. method:: set(cmode=0, rdy=0, ch=0, sps=2, pga=1)

    Sets the device's configuration register.

    **Parameters:**

    * **cmode** : sets the Conversion mode. Available values are:

        * ``0`` : Continuous Conversion Mode. The device performs data conversion continuously.
        
        * ``1`` : One-Shot Conversion Mode. The device performs a single conversion and enters a low power standby
          mode until it receives another command.

    * **rdy** : when in Continuous Conversion mode, the value of this parameter has no effect.
      When in One-Shot Conversion mode, setting this parameter to ``1`` initiates a new conversion.

    * **ch** : channel selection.

      ====== ====================================================================
       ch    selected channel
      ====== ====================================================================
       0      Channel 1
       1      Channel 2
       2      Channel 3 (MCP3248 only, treated as 0 by MCP3246/MCP3247)
       3      Channel 4 (MCP3248 only, treated as 1 by MCP3246/MCP3247)
      ====== ====================================================================
    
    * **sps** : Sample rate / resolution selection.

      ====== ===================  ======================
      sps     Samples per second   ADC resolution (bits)
      ====== ===================  ======================
       0      240                     12
       1      60                      14
       2      15                      16
      ====== ===================  ======================

    * **pga** : PGA Gain selection. Available values are `1`, `2`, `4`, and `8`. Passing an invalid value results in unity gain.

    
.. method:: get_raw_data()
    
    Return the conversion result as an n-bit signed integer, where n depends on last *sps* value used with :ref:`set() <set>`.
    
    =============   ======================  ==============   ===============
    Last sps set    ADC resolution (bits)   Minimum output   Maximum output
    =============   ======================  ==============   ===============
     0                    12                    -2048             2047
     1                    14                   -8192               8191
     2                    16                  -32768             32767
    =============   ======================  ==============   ===============
    
    
