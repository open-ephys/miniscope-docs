##############################
Miniscope-DAQ Data Acquisition
##############################

***********************
Miniscope-DAQ Tutorials
***********************

The User Guide contains following tutorials:

*   :doc:`View and save image and orientation/quarternion data in real-time </ucla-miniscope-v4/user/miniscope-daq/save-data/index>`

*   :doc:`Commutate the UCLA Miniscope's tether using the on-board IMU </ucla-miniscope-v4/user/miniscope-daq/commutate/index>`

***************************
Miniscope-DAQ Functionality
***************************

I/O
===

Miniscope-DAQs from Open Ephys have the following I/O:

*   **Input trigger:** a digital input to initiate and terminate data acquisition

    *   A rising edge initiates data acquisition

    *   A falling edge terminates data acquisition

*   **Sync output:** a digital output in which every rising or falling edge indicates a new frame

The I/O operate at a 3.3V logic level. The input is 5V tolerant.

The aux input is not currently supported in software.

External Power
==============

The Miniscope-DAQ can accept an external power source and forward it to a connected device for particularly power-intensive applications in which USB3.0 cannot provide enough power. Using an external power source is required for the MiniCAM and recommended for the UCLA Miniscope v4. For more information on symptoms related to insufficient power, refer to the Troubleshooting (coming soon) guide. To use an external power source instead of USB3.0:



Recommended specifications for an external power supply are as follows:

*   5-6V

    *   To dial in the ideal power supply voltage for your setup (in particular for your tether), use an adjustable power supply (e.g. ) and probe the following pads while adjusting the voltage. The ideal voltage at those pads is about 4V. This voltage is high enough to maximize reliability of the UCLA Miniscope v4 acquisition and low enough to minimize unnecesary heat generation.

*   2A, though this value is not critical. The MiniCAM with an attached IR LED ring requires more current than the UCLA Miniscope v4

*   Center-positive polarity

LED Indicators
==============

Miniscope-DAQs have the following green LED indicators:

*   **DAQ Power:** This LED indicates the Miniscope-DAQ is receiving power. Establishing the USB connection between the Miniscope-DAQ and your PC toggles this LED on.

*   **Scope Power:** This LED indicates the Miniscope-DAQ is forwarding power to the device that is connected to the Miniscope port.

    *   If the power jumper is set to , the LED turns on after establishing the USB connection

    *   If the power jumper is set to , the LED turns on after establishing the USB connection *and* the external power source connection

*   **Data Link:** This LED indicates the Miniscope-DAQ communication is established between the Miniscope-DAQ and the connected device.

************
Syncing Data
************

For strict data syncing requirements, best practice involves using a combination of the UCLA Miniscope v4's sync output and software timestamps. 

Software timestamps are accurate to within a few milliseconds which is insufficient for stricter data syncing requirements. Though the sync output is accurate to within microseconds, it alone is also insufficient. This is because it is possible for frames to drop on the way from the Miniscope-DAQ to the PC. Therefore, best practice is to corroborate sync output data with software timestamps to ensure that a sync output frame corresponds a frame that was received by the PC.

The effect of a dropped frame is a larger inter-frame interval. If you are struggling with dropped frames, try changing USB ports, USB drivers, and other devices that are sharing the USB bus. Dropped frames are due to limited USB bandwidth and timing constraints. Expect a dropped frame every few thousand frames on a proper setup. 

The input trigger involves 10-100ms latency so relying on it for syncing data is also not recommended.

.. toctree::
    :hidden:
    
    save-data/index
    trigger/index
    commutate/index
