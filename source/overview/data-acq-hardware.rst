
#########################
Data Acquisition Hardware
#########################

The :ref:`overview/data-acq-hardware:Miniscope-DAQ` is the most common hardware for acquiring data from miniscopes derived from the UCLA Miniscope v4 and the v4 itself.

.. note:: Wireless miniscopes with on-board loggers such as the UCLA Miniscope v3 Wireless do not require data-acqusition hardware.
..
    ****
    ONIX
    ****

    ONIX is the data acquisition hardware designed by Open Ephys. It is compatible with a large array of Open Ephys hardware including electrophysiology headstages and miniscopes for Ca/ :sup:`2+` imaging. It supports several digital/analog GPIO, simultaneous data acquisition from up to two headstages/miniscopes, and many more features. To learn more about ONIX, refer to the `ONIX documentation <https://open-ephys.github.io/onix-docs/Hardware%20Guide/index.html>`__ and `ONIX store webpage <https://open-ephys.org/onix>`__. To learn how to acquire miniscope data with ONIX, refer to the ONIX *Quick Start Guide* for your respective miniscope:

    *   :doc:`UCLA Miniscope v4 </ucla-miniscope-v4/quick-start/onix1-quick>`

*************
Miniscope-DAQ
*************

..  image:: /_static/images/miniscope-daq.webp
    :alt:   image of miniscope-daq
    :align: center

The `Miniscope-DAQ <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__ is the data acquisition hardware developed by the UCLA Miniscope team for acquiring miniscope data. It accepts an external power supply for more power-intensive applications and plugs into a PC through a USB cable. It supports sync output, input trigger, and data acquisition from a UCLA Miniscope v4, MiniCAM, and other miniscopes derived from the UCLA Miniscope v4. The Miniscope-DAQ is supported by :ref:`overview/data-acq-software:Bonsai` and :ref:`overview/data-acq-software:Miniscope-DAQ-QT-Software`. To acquire miniscope or MiniCAM data with the Miniscope-DAQ, refer to the corresponding :doc:`/ucla-miniscope-v4/quick/index` and :doc:`/ucla-miniscope-v4/user/index`. To learn more about the Miniscope-DAQ, refer to the `UCLA Miniscope v4 Wiki <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__. 

Miniscope-DAQ Functionality
===========================

I/O
---

Miniscope-DAQs from Open Ephys have the following I/O:

*   **Input trigger:** a digital input to initiate and terminate data acquisition

    *   A rising edge initiates data acquisition

    *   A falling edge terminates data acquisition

*   **Sync output:** a digital output in which every rising or falling edge indicates a new frame

The I/O operate at a 3.3V logic level. The input is 5V tolerant.

The aux input is not currently supported in software.

External Power
--------------

The Miniscope-DAQ can accept an external power source and forward it to a connected device for particularly power-intensive applications in which USB3.0 cannot provide sufficient power or voltage. Using an external power source is required for the MiniCAM and recommended for the UCLA Miniscope v4. For more information on symptoms related to insufficient power, refer to the Troubleshooting (coming soon) guide. To use an external power source instead of USB3.0:

#.  Unscrew all four fasteners that fasten the Miniscope-DAQ's enclosure. It might be necessary to apply gentle pressure on the nuts on the bottom of the DAQ to prevent them from turning when unscrewing the screws.

#.  Set the jumper according to which power source you would like to use following to the silk screen:

    ..  image:: /_static/images/miniscope-daq-jump.webp
        :alt:   power jumper animation
        :align: center

#.  Replace the four fasteners. 

..  note::  If the Miniscope-DAQ is set to use external power, the barrel jack must be plugged in to use the connected miniscope/minicam.

Recommended specifications for an external power supply are as follows:

*   5-6V

    *   To dial in the ideal power supply voltage for your setup (in particular for your tether), use an adjustable power supply (e.g. ) and probe the following pads while adjusting the voltage. The ideal voltage at those pads is about 4V. This voltage is high enough to maximize reliability of the UCLA Miniscope v4 acquisition and low enough to minimize unnecesary heat generation.

*   2A, though this value is depedent on your miniscope/camera device. The MiniCAM with an attached IR LED ring requires more current than the UCLA Miniscope v4, for instance.

*   Center-positive polarity

By default, the Miniscope-DAQ is set to use USB power. 

LED Indicators
--------------

Miniscope-DAQs have the following green LED indicators:

*   **DAQ Power:** This LED indicates the Miniscope-DAQ is receiving power. Establishing the USB connection between the Miniscope-DAQ and your PC toggles this LED on.

*   **Scope Power:** This LED indicates the Miniscope-DAQ is forwarding power to the device that is connected to the Miniscope port.

    *   If the power jumper is set to , the LED turns on after establishing the USB connection

    *   If the power jumper is set to , the LED turns on after establishing the USB connection *and* the external power source connection

*   **Data Link:** This LED indicates the Miniscope-DAQ communication is established between the Miniscope-DAQ and the connected device.

..  note::  If the Miniscope-DAQ is set to use external power, the barrel jack must be plugged in for the **Scope Power** LED to toggle on.

Syncing Data
============

For strict data syncing requirements, best practice involves using a combination of the UCLA Miniscope v4's sync output and software timestamps. 

Software timestamps are accurate to within a few milliseconds which is insufficient for stricter data syncing requirements. Though the sync output is accurate to within microseconds, it alone is also insufficient because it is possible for frames to drop on the way from the Miniscope-DAQ to the PC. Therefore, it is to corroborate sync output data with software timestamps to ensure that a sync output frame corresponds a frame received by the PC.

The effect of a dropped frame is a larger inter-frame interval. If you are struggling with dropped frames, try changing USB ports, USB drivers, and removing other devices that are sharing the USB bus. Dropped frames are due to limited USB bandwidth and timing constraints. On a proper setup, expect a dropped frame every few thousand frames.

The input trigger involves 10-100ms latency so relying on it for syncing data is also not recommended.


Miniscope-DAQ Variants
======================

MiniDAQ
-------

..  image:: /_static/images/minidaq.webp
    :alt:   image of minidaq
    :align: center

..  todo:: remove background of and color-correct these photos, or take new photos

The MiniDAQ is a simplified, more compact, and more affordable version of the Miniscope-DAQ. It plugs directly into a PC through its on-board USB cable. It supports data acquisition from a single UCLA Miniscope v4 with a short tether. Unlike the Miniscope-DAQ, the MiniDAQ does not accept an external supply or support sync output or input trigger functions. The MiniDAQ is compatible with :ref:`overview/data-acq-software:Bonsai` and :ref:`overview/data-acq-software:Miniscope-DAQ-QT-Software`. To acquire miniscope, follow the same user guides as the Miniscope-DAQ.

NINscope-DAQ
------------

..  image:: /_static/images/ninscope-daq.webp
    :alt:   image of ninscope-daq
    :align: center

..  todo:: color-correct this photo so it matches miniscope-daq photo

The NINscope-DAQ is like the Miniscope-DAQ except the NINscope-DAQ is also compatible with the `NINscope <https://github.com/ninscope>`__. It accepts an external power supply for more power-intensive applications and plugs into a PC through a USB cable. It supports sync output, input trigger, and data acquisition from a single NINscope. The NINscope is compatible with `custom NINscope software <https://github.com/ninscope/Software/wiki/NINscope-software>`__ from the NINscope developers. To learn more about the NINscope, refer to the `NINscope hardware wiki <https://github.com/ninscope/Hardware/>`__ from the NINscope developers.
