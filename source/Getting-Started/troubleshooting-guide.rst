
##########################################
Troubleshooting Guide
##########################################

Here is a guide to help you troubleshoot common error scenarios that can occur when using the Miniscope system. It is focused on the UCLA Miniscope v4 with the OE DAQ, and Bonsai running on Windows.

If issues persist after following this guide, the scenario you encountered is not in this guide, or you believe your Miniscope or DAQ needs repair, please reach out as detailed under :ref:`help`.

General recommendations
###################################

- Keep the software and packages updated to the latest version.
- Keep the firmware updated to the latest version.
- Keep an eye out for warnings and errors in the software console during operation.

.. _troubleshooting:

Initial troubleshooting steps
###################################

1. Check the hardware USB connection
******************************************************************

Always use a USB 3.0-compatible port on your computer using the high-speed USB cable provided. USB 3.0-compatible port are usually indicated by a blue color and are often at the back of PCs. Ensure you establish a reliable USB connection by connecting directly to the port instead of through a hub or extension. USB cables longer than 2 meters are not recommended.

*All three LEDs on the DAQ and the red LED on the miniscope body itself must be continuously on.*

2. Check that the DAQ is recognized properly in the Device Manager
*******************************************************************************

If the Miniscope DAQ is working normally, it should be listed as `UCLA/Open Ephys Miniscope DAQ v3`, under `Cameras`.

..  image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
    :width: 60%
    :align: center

If not, refer to the :ref:`daq_firmware_details` section of this documentation.

3. Check your coaxial tether and connectors
*******************************************************************************

Always ensure that the connectors on both the DAQ and the miniscope are fully seated. Inspect the coaxial tether and its connector for any damage, dirt, or signs of wear.


Connection problems
###################################

Connection errors occur when the DAQ detects a powered device but is unable to receive continuous signal from it. This typically indicates a communication problem between the miniscope and the DAQ, or the DAQ.

Problems like dropped frames, inconsistent frame rate and banding artifacts indicate that there is a connection issue.

.. image:: /_static/images/banding2.png
    :width: 50%
    :align: center

These issues are commonly caused by connectors that are not fully seated, a damaged coaxial tether, or an unstable USB connection.

To resolve this, disconnect and reconnect the miniscope, restart the software and ensure the DAQ USB connection is reconnected.

Follow the :ref:`troubleshooting` above to identify and resolve the source of the connection issue.


Insufficient power
###################################

Depending on your settings and tether length, the USB supply may not provide sufficient power to operate the miniscope reliably.

Horizontal stripes artifacts can occur due to insufficient or unstable power delivery and are typically more pronounced at higher LED intensity settings.

.. image:: /_static/images/stripes.gif
    :width: 50%
    :align: center

This issue can usually be resolved by switching to an external power supply. Refer to the :ref:`externalpower` section for instructions on how to connect and use an external power source.

*Note: If the LED brightness is within the expected operating range, horizontal stripes should not occur even when powered via USB only. In this case, check that no other devices are drawing significant power from the same USB ports.*


EWL focus not functioning
###################################


Radial banding artifact
###################################
Radial banding artifacts indicate a defect on the PCB. This issue is commonly caused by damage to the flexPCB between the image sensor and the serializer, which leads to corrupted or missing bits in the pixel data stream.

.. image:: /_static/images/radialbanding.png
    :width: 100%
    :align: center

The solution for this is to replace the PCB. You can follow our :ref:`disassembly` guide and :ref:`miniscope_assembly_guide` guide for step-by-step instructions to complete the replacement.

Dust particles
###################################




.. _help:

How to ask for help
###################################

1. Make sure that you have read through this guide.
2. Check for any errors or warnings.
3. Write to our `support channel <https://open-ephys.org/contact>`_ with the following information:

- Details of your hardware setup and all hardware connections.
- A photo or a screen video capture showing the issue.
- A description of what happened as the issue occurred.