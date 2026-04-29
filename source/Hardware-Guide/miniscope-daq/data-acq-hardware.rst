
#########################
Miniscope DAQ
#########################
..  image:: /_static/images/miniscope-daq.webp
    :alt:   image of miniscope-daq
    :align: center

The `Miniscope-DAQ <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__ is the data acquisition hardware developed by the UCLA Miniscope team for acquiring miniscope data. It connects to the PC through USB 3.0. It supports sync output, input trigger, and data acquisition from a single Miniscope v4 or MiniCAM. It optionally accepts an external power supply for more power-intensive applications. The Miniscope-DAQ is supported by Bonsai and the Miniscope-DAQ-QT-Software (deprecated), as detailed in the :doc:`/Software-Guide/index`. To acquire miniscope or MiniCAM data with the Miniscope-DAQ, refer to the :ref:`quickstartguide` and :doc:`/User-Guide/index`. To learn more about the Miniscope-DAQ, refer to the `UCLA Miniscope v4 Wiki <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__. 

Miniscope-DAQ Functionality
===========================

I/O
---

The I/O on the Miniscope DAQ operate at a 3.3V logic level and the inputs are 5V tolerant. Miniscope DAQs with the :doc:`latest firmware </Hardware-Guide//miniscope-daq/firmware-update>`. from Open Ephys have the following input and output ports:

*   **Input Trigger:** a digital input channel that can be used to log events, gate data acquisition, recording to file, LED on/off state, etc. The functionality is defined by the software configuration. This trigger does not serve as a frame trigger for individual frames and is not recommended for syncing data.
   
*   **Sync Output:** a digital output channel in which every rising and falling edge indicates a new frame captured by the connected device. This output is recommended for synchronization of multiple hardware with an external acquisition device with a hardware clock.

*   **Aux Input:** an additional digital input channel that can be used to log events, gate data acquisition, recording to file, LED on/off state, etc. The functionality is defined by the software configuration.

.. _externalpower:

External Power
--------------

By default, the Miniscope-DAQ is set to use USB power. However, it can be set to use an external power source for particularly power-intensive applications in which USB3.0 cannot provide sufficient power. To use an external power source instead of USB3.0:

#.  Unscrew all four fasteners that fasten the Miniscope-DAQ's enclosure. It might be necessary to apply gentle pressure on the nuts on the bottom of the DAQ to prevent them from turning when unscrewing the screws.

#.  Set the jumper according to which power source you would like to use, either Jack or USB following to the silk screen:

    ..  image:: /_static/images/miniscope-daq-jump.webp
        :alt:   power jumper animation
        :align: center

#.  Replace the four fasteners. 

..  note::  If the Miniscope DAQ is set to use external power, the barrel jack must be plugged in to use the device. Conversely, when the Miniscope DAQ is set to USB power, the barrel jack has no effect.

Recommended specifications for an external power supply are as follows:

*   Output voltage

    .. warning:: Do not exceed 9.0 VDC at the external power jack to the Miniscope DAQ. Exceeding this voltage can damage the device.

    To dial in the ideal power supply voltage for your application, you can use an adjustable power supply to power the DAQ and monitor the voltage at the miniscope as described in :ref:`measure_voltage` to stay within the operating voltage range of the miniscope and the DAQ. If you don't have a variable power supply, in most cases a `6V power adapter <https://open-ephys.org/power-supplies/oeps-5906>`__ is sufficient to account for the voltage drop. 
    
*   Output current

    Power adapters up to 1A are used even though the current draw by the devices is less.

*   Center-positive polarity

*   Round barrel plug of 2.5 mm ID and 5.5 mm OD


LED Indicators
--------------

Miniscope-DAQs have the following green LED indicators:

*   **DAQ Power:** This LED indicates the Miniscope-DAQ is receiving power. Establishing the USB connection between the Miniscope-DAQ and your PC toggles this LED on.

*   **Scope Power:** This LED indicates the Miniscope-DAQ is forwarding power to the device that is connected to the Miniscope port.

    *   If the power jumper is set to USB, the LED turns on after establishing the USB connection

    *   If the power jumper is set to Jack, the LED turns on after establishing the USB connection *and* the external power source connection

*   **Data Link:** This LED indicates the Miniscope-DAQ communication is established between the Miniscope-DAQ and the connected device.

..  note::  If the Miniscope-DAQ is set to use external power, the barrel jack must be plugged in for the **Scope Power** LED to toggle on.

Syncing Data
============

For strict data syncing requirements, best practice involves using a combination of the UCLA Miniscope v4's sync output and software timestamps. 

Software timestamps are accurate to within a few milliseconds which is insufficient for stricter data syncing requirements. Though the sync output is accurate to within microseconds, it alone is also insufficient because it is possible for frames to drop on the way from the Miniscope-DAQ to the PC. Therefore, it is to corroborate sync output data with software timestamps to ensure that a sync output frame corresponds a frame received by the PC.

The effect of a dropped frame is a larger inter-frame interval. If you are struggling with dropped frames, try changing USB ports, USB drivers, and removing other devices that are sharing the USB bus. Dropped frames are due to limited USB bandwidth and timing constraints. On a proper setup, expect a dropped frame every few thousand frames.

The input trigger involves 10-100ms latency so relying on it for syncing data is also not recommended.

.. toctree::
    :hidden:
    :maxdepth: 1
    :titlesonly:

    firmware-update