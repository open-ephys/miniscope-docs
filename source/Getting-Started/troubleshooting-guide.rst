
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


Initial troubleshooting steps
###################################

1. Check the hardware USB connection
******************************************************************

- Always use a USB 3.0-compatible port on your computer using the high-speed USB cable provided. USB 3.0-compatible port are usually indicated by a blue color and are often at the back of PCs. Ensure you establish a reliable USB connection by connecting directly to the port instead of through a hub or extension. USB cables longer than 2 meters are not recommended.

*All three LEDs on the DAQ and the red LED on the miniscope body itself must be continuously on.*

2. Check that the DAQ is recognized properly by the Operating System
*******************************************************************************



Connection problems
###################################

Connection errors occur when the DAQ detects a powered device but is unable to receive continuous signal from it. This typically indicates a communication problem between the miniscope and the DAQ.

Errors like *Warning: Miniscope retrieve frame failed. Attempting to reconnect.*, horizontal stripes and inconsistent frame rate indicate that there is a connection issue.

.. image:: /_static/images/stripes.png
    :width: 40%
    :align: center

This might be due to connectors that are not fully seated, a damaged coaxial tether or an unstable USB connection.

Follow the troubleshooting steps above to identify and resolve the source of the connection issue.


.. _help:

How to ask for help
###################################

1. Make sure that you have read through this guide.
.. 2. Check that the software application, the Bonsai package and the firmware are all updated to the latest version.
.. 3. Check the software console log for any errors or warnings.
.. 4. Write to our `support channel <https://open-ephys.org/contact>`_ with the following information:

.. - Details of your hardware setup and all hardware connections.
.. - A photo, screenshot or screen capture showing the issue.
.. - A description of what happened as the issue occurred.