####################
Measuring Voltage
####################

.. _voltage_requirements:

The Miniscope v4 has a required operating voltage as specified in the following table. 

.. table::
    :widths: 50 80 50 50 50

    +------------------------+--------------------+----------+----------+----------+
    | Parameter              | Value              | Min      | Max      | Unit/    |
    |                        |                    |          |          | Type     |
    +========================+====================+==========+==========+==========+
    | Supply Voltage         | 4.2                | 4.2      | 6.0*     | Volts    |
    +------------------------+--------------------+----------+----------+----------+

.. warning:: \*Do not exceed 6.0 VDC at the coaxial input to the miniscope. Make
    sure you make this measurement at the miniscope as explained below to
    account for a potential voltage drop in the tether. Exceeding this voltage can
    permanently damage the miniscope.

.. note:: The lowest voltage that provides stable functionality should be used to avoid excessive heating of the electronic components. 

The supply voltage required at the Miniscope DAQ to maintain the miniscope within its operating range depends on the user's setup and settings configuration such as tether length and diameter and LED brightness. The 5V supplied by USB power should be sufficient in standard calcium imaging applications with the standard 1.1 mm diameter mini-coax tether of 1.5 m in length supplied by Open Ephys. Longer or thinner :ref:`tethers <tethers>`, or non-standard settings such as high LED brightness can require externally adjusting the power supplied to the Miniscope DAQ, as discussed in the :ref:`externalpower` section, while carefully monitoring the voltage at the miniscope as explained below.

.. _measure_voltage:

To determine the supply voltage reaching the miniscope, power the miniscope and use a multimeter to probe the two points of either set of ground and voltage supply pads marked below. The first set of pads around the connector are larger but can be hard to access once the tether is attached to the miniscope, so the second set of pads on the side are a good alternative. These side pads sit at approximately 0.2 V lower than the pads around the connector. 

..  image:: /_static/images/measure_voltage_miniscopev4.png
    :alt:   image identifying voltage measuring points
    :align: center
    :height:    500px