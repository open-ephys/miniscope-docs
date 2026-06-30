
##########################################
Troubleshooting Guide
##########################################

Here is a guide to help you troubleshoot common error scenarios that can occur when using the Miniscope system. It is focused on the UCLA Miniscope v4 with the Open Ephys Miniscope DAQ, and Bonsai usage in Windows.

If issues persist after following this guide, the scenario you encountered is not in this guide, or you believe your Miniscope and/or DAQ needs repair, please reach out as detailed under :ref:`help`.

General recommendations
###################################

- Keep the software and packages updated to the latest version.
- Keep the Miniscope DAQ firmware updated to the latest version.
- Keep an eye out for warnings in the software during operation.

.. _troubleshooting:

Initial troubleshooting steps
###################################

1. Check the hardware USB connection
*************************************************

Always use a USB 3.0-compatible port on your computer using the high-speed USB cable provided. USB 3.0-compatible port are usually indicated by a blue color and are often at the back of PCs. Ensure you establish a reliable USB connection by connecting directly to the port instead of through a hub or extension.

*All three indicator lights on the DAQ and the red LED on the miniscope body itself must be continuously on.*

2. Check that the DAQ is recognized properly by the Operating System
***************************************************************************

After making sure to follow step 1., the Miniscope DAQ should be recognized by the Operating System. Go to :code:`Start Menu > Settings > Devices > Bluetooth & other devices` and check that the DAQ is listed as *Connected to USB3.0*, with no additional warnings.

..  image:: /_static/images/connectedtousb.png
    :width: 60%
    :align: center

If not, refer to :ref:`getting-started/index:connecting the hardware` for additional details.


USB Configuration
***********************
The Miniscope DAQ works via USB, and the PC's power management both in laptops and desktops can interfere with USB communication. This can be experienced as a sudden interruption during an otherwise stable period acquisition that can be traced back to USB communication errors and not a hardware disconnection.
Always ensure that the USB settings are configured to avoid suspension.

3. Check that the DAQ is recognized properly in the Device Manager
***************************************************************************

If the Miniscope DAQ is working normally, it should be listed as `UCLA/Open Ephys Miniscope DAQ v3`, under `Cameras`.

..  image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
    :width: 60%
    :align: center

If not, refer to the :ref:`daq_firmware_details` section of this documentation.

4. Check your cable, coaxial tether and connectors
******************************************************

Always ensure that all connectors on the DAQ, miniscope and commutator (if using one) are fully seated. Inspect the USB cable, the coaxial tether and its connector, and the miniscope connector for any signs of damage, debris or wear.

5. Review order of operations
********************************************
After disconnecting all components and closing the software, reconnect the system in the following order: first, plug the coaxial tether into the miniscope. Then connect the miniscope to the DAQ. Next, connect the DAQ to your computer.
Only once all three light on the DAQ and the red LED on the miniscope are on should you open the software.

Refer to :ref:`getting-started/index:connecting the hardware` for additional details.

Horizontal stripes
###################################

Connection errors occur when the DAQ detects a powered device but is unable to receive continuous signal from it. Problems like dropped frames, inconsistent frame rate and stripes artifacts indicate that there is a connection issue. 

This typically indicates a communication problem between the miniscope and the DAQ.

.. image:: /_static/images/badconnection.gif
    :width: 40%
    :align: center

Horizontal stripes appear when there is a mismatch between frames coming to the DAQ. These issues are commonly caused by connectors that are not fully seated, a damaged coaxial tether, or an unstable USB connection.

To resolve this, disconnect and reconnect the miniscope, restart the software and ensure the DAQ USB connection is also reconnected.

Follow the :ref:`troubleshooting` above to identify and resolve the source of the connection issue.

Horizontal banding artifacts
###################################

Using the DAQ via USB can only supply 5V. Depending on your setup and settings such as cable length, type of cable, commutation and LED Brightness, the USB supply may not provide sufficient power to operate the miniscope reliably.

Horizontal banding artifacts can occur due to insufficient or unstable power delivery and are typically more pronounced at higher LED intensity settings. You can check that no other devices are drawing significant power from the same USB ports.

.. image:: /_static/images/banding.gif
    :width: 40%
    :align: center

This can be resolved by externally powering the DAQ. Refer to the :ref:`externalpower` section for instructions on how to connect and use an external power source, while carefully monitoring the voltage at the miniscope.

No image signal
###################################

If your miniscope index is set incorrectly, image acquisition will fail and no signal will be received.

.. image:: /_static/images/wrongindex.png
    :width: 30%
    :align: center

Make sure the ``UCLAMiniscopeV4 operator``’s ``Index`` property matches the index assigned to your miniscope. Refer to :ref:`getting-started/index:testing the miniscope's functionality` section.

Runtime Error messages
###################################

1. Stopped receiving frames

.. .. image:: /_static/images/frametimeout.png
    :width: 30%
    :align: center

This error points to a connection issue, indicating that the communication with the miniscope has been lost, most commonly due to a disconnected or loose USB or coaxial tether connection. Follow the :ref:`troubleshooting` above to identify and resolve the source of the connection issue.

2. Invalid quaternion value

This error points to a connection issue, indicating that the communication with the miniscope has been lost, most commonly due to a disconnected or loose USB or coaxial tether connection. Follow the :ref:`troubleshooting` above to identify and resolve the source of the connection issue.

.. 3. Error acquiring frames

.. .. image:: /_static/images/erroracquiringframes.png
    :width: 30%
    :align: center

EWL focus not functioning
###################################

1. Inspect your PCB and EWL connection.

Check whether the flex PCB is bent or damaged near the EWL and verify that the objective module is properly tightened.
An impact to the miniscope can cause the PCB to move slightly, preventing proper contact between the EWL and the PCB. Ensure the screws are secure and that the circular contact pads on the PCB are correctly seated within the objective module and making firm contact with the EWL.


2. EWL driver component.

The focus issue can be related to the power switch/driver responsible for controlling the EWL. If this component isn't functioning properly, it can cause the focus to stop working, vertical line artifacts, and in some cases, heating of the PCB. 
This failure is typically caused by a crack or physical damage to the component. Such damage is usually not visible to the naked eye and requires inspection under a microscope.

Inspect the component to look for any cracks or signs of damage, particularly around the corners to check for a chipped edge or fine fracture lines.
This component is located on the outside of the PCB, on the LED PCB side, circled in red in the image below. It is on the opposite side of the miniscope from the coaxial tether connector.

.. image:: /_static/images/ewldriver.png
    :width: 50%
    :align: center

Also check if this area of the PCB is generating noticeable heat.

If the component is cracked or damaged, the recommended solution is to replace the PCB. You can follow our :ref:`disassembly` guide and :ref:`miniscope_assembly_guide` guide for step-by-step instructions to complete the replacement. Alternatively, the component can sometimes be replaced without changing the entire PCB. For more details, you can contact us regarding our repair services.

Radial pixelation artifacts
###################################
Radial pixelated artifacts indicate a defect on the PCB. This issue is commonly caused by damage to the flexPCB between the image sensor and the serializer, which leads to corrupted or missing bits in the pixel data stream.

.. image:: /_static/images/radialbanding.png
    :width: 100%
    :align: center

The solution for this is to replace the PCB. You can follow our :ref:`disassembly` guide and :ref:`miniscope_assembly_guide` guide for step-by-step instructions to complete the replacement.

Excess power
###################################

We always recommend using a variable power supply and closely monitor the voltage delivered to the miniscope to avoid damage. Refer to the :ref:`externalpower` section for details.

Using an incorrect supply (e.g., 9V, 12V, or higher) exceeds the operating limits and is likely to damage the miniscope. In such cases, the miniscope may fail to connect or may not function properly. If this occurs, the PCB may be damaged and require replacement.

You can follow our :ref:`disassembly` guide and :ref:`miniscope_assembly_guide` guide for step-by-step instructions to complete the replacement.

The DAQ itself is powered via USB even when external power is connected, so it should not be affected or damaged by higher voltages applied to the external power input.

.. _help:

How to ask for help
###################################

1. Make sure that you have read through this guide.
2. Check for any errors or warnings.
3. Write to our `support channel <https://open-ephys.org/contact>`_ with the following information:

- Details of your hardware setup and all hardware connections.
- A photo or a screen video capture showing the issue.
- A description of what happened as the issue occurred.