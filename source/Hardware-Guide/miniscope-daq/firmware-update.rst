#########################
DAQ Firmware Upload
#########################

Follow this guide to upload firmware onto your Miniscope DAQ.

Uploading firmware to the device is required only occasionally, in two different situations:

- when a new firmware version is released, to update a device that is working properly.
- when the flash memory (EEPROM) on the DAQ has corrupted and the system no longer recognizes the device as MINISCOPE, to fix the issue.

It is helpful to understand how the device works to understand the firmware upload procedure.

The Miniscope DAQ has two boot modes: boot from EEPROM (for normal operation) and boot from USB controller (to upload firmware to the device).

To force a working device to boot from the USB controller in order to upload new firmware, one must physically move a jumper on the PCB inside the DAQ.

Devices with a corrupt flash memory boot from the USB controller regardless of the jumper position, so the firmware update procedure can sometimes be carried out without opening the device to configure the hardware to load in bootloader mode.

In all cases in which communication with the USB controller is required, the corresponding drivers for the Miniscope DAQ Bootloader (Cypress USB) have to be installed on the PC for Windows to recognize the bootloader device. These drivers are not required during normal operation, and therefore must be installed separately on each PC that will be used for the firmware update procedure.

The state of the Miniscope DAQ is apparent by checking the Device Manager, and corresponding courses of action are summarized in the following diagram:

.. mermaid::

   flowchart
               A("Firmware update required")
               A -->C
               C{"How is the Miniscope DAQ listed in the Windows Device Manager?"}
               C -->|"MINISCOPE"| D["`Configure the hardware
               for bootloader mode`"]
               D --> C
               C -->|"Westbridge"| E["Install bootloader driver"]
               C -->|"Cypress FX3 USB BootLoader Device"| F["Use Cypress Control Center to upload firmware"]
               E --> C
               F --> H["_If required_, re-configure the hardware for normal use"]
               H --> I["Power cycle"]
               I --> J("Firmware updated. Device ready to use listed as MINISCOPE in Windows Device Manager")


The instructions to perform all operations are detailed below, including physically configuring the hardware and installing the bootloader driver even though they might not always be necessary.

*Required components: Miniscope DAQ, USB3.0 cable (Micro Type B ↔ Type A)*

*Tools that can be required: 2.5 mm hex key for opening the screws on the Miniscope DAQ's enclosure*

Check the Windows Device Manager
----------------------------------------------

#. Connect the Miniscope DAQ to the PC using a USB3.0 connection and check the Windows Device Manager.

   - If the Miniscope DAQ is working normally, it should be listed as `MINISCOPE`, under `Cameras`.

   ..  image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
         :align: center

   - If the Miniscope DAQ was having issues, it might already be in bootloader mode and can either be listed as `Cypress FX3 USB BootLoader Device` under `Universal Serial Bus controllers` (if the bootloader is installed):

   ..  image:: /_static/images/firmware/driver-update-1b-listed-bootloader.png
         :align: center

   or as `WestBridge` under `Other devices`, with a warning icon (if the bootloader driver is not installed):

   ..  image:: /_static/images/firmware/driver-update-1c-listed-westbridge.png
         :align: center

   - If the Miniscope DAQ is not listed in the Device Manager, check the hardware connections.

Configure the Hardware for Bootloader Mode
--------------------------------------------

To proceed with the firmware update, the Miniscope DAQ must be in bootloader mode. If not already in that mode, configure the hardware to force the DAQ to load from the bootloader as follows:

#. Open the Miniscope-DAQ's enclosure by using the 2.5 mm hex key to unscrew all four fasteners. It might be necessary to apply gentle pressure on the nuts on the bottom of the DAQ to prevent them from turning when unscrewing the screws.

#. With the PCB exposed, move the jumper on header J9 to close the header labeled K1 as shown in the picture below. The J9 header remains empty. This changes the board to "Boot from USB" mode.

   ..  image:: /_static/images/firmware/DAQ_board_Jumper_J9.jpeg
         :align: center
         :width: 400px

#. Connect the DAQ to the PC using a USB3.0 connection. Only the DAQ Power indicator LED will be on. It should be listed in the Device Manager as `Cypress FX3 USB BootLoader Device` under `Universal Serial Bus controllers`:

   ..  image:: /_static/images/firmware/driver-update-1b-listed-bootloader.png
         :align: center

Install the Miniscope DAQ Bootloader Driver
----------------------------------------------

To proceed with the firmware update, the Miniscope DAQ should be listed as `Cypress FX3 USB BootLoader Device` under `Universal Serial Bus controllers`. If, instead, it is listed as `WestBridge` under `Other devices`, the bootloader driver needs to be installed:

#. Download the :download:`Miniscope DAQ Bootloader Driver </_static/downloads/CyUSB3_1.3.0.3_Win11_Win10_Logo_Certified.zip>`.

.. apparently they are downloaded with the EZ-USB suite, in C:\Program Files (x86)\Cypress\EZ-USB FX3 SDK\1.3\driver\bin\Win10\x64

#. Unzip the folder and examine its contents.

#. Right-click the `.inf` file and select Install.

   ..  image:: /_static/images/firmware/driver-update-2-install.png
         :align: center

#. Follow the instructions to install the driver. You should see a success message once the process is finished.

Download the Firmware Uploader Application
-------------------------------------------

#. Download the `EZ USB Suite <https://www.infineon.com/design-resources/development-tools/sdk/usb-controllers-sdk/ez-usb-fx3-software-development-kit>`__ which contains the Cypress Control Center we will use to upload the firmware.

#. Follow the download instructions. The webpage requires you to create a login.

#. Double-click on the executable to install the application.

Firmware Upload
-------------------------------------------

#. Download the firmware image:

.. list-table::
   :widths: 15 60
   :header-rows: 1

   * - Firmware Image
     - Release Date
   * - `Original version <https://github.com/Aharoni-Lab/Miniscope-DAQ-Cypress-firmware/raw/refs/heads/master/Built_Firmware/Miniscope_DAQ_256K_EEPROM.img>`__
     - 2023.08.16

#. Access the *Cypress USB Control Center*.

   The most straightforward way is to search for *CyControl* in the Windows Applications Menu:

   ..  image:: /_static/images/firmware/fw-update-1a-cycontrolicon.png
         :align: center

   .. dropdown:: You can also access the Cypress USB Control Center from the EZ USB Suite application

      If you opened the *EZ USB Suite* application instead of *CyControl*,

      ..  image:: /_static/images/firmware/fw-update-1b-ezusbicon.png
            :align: center

      Navigate to the CY Tools Menu > Control Center to access the *Cypress USB Control Center*:

      ..  image:: /_static/images/firmware/fw-update-1b-cytoolsmenu.png
            :align: center  

#. In the *Cypress USB Control Center*, the Miniscope DAQ should be listed on the left panel as "Cypress FX3 USB BootLoader Device". If not, revise the hardware connections, that it is configured for bootloader mode and that the bootloader driver is installed as explained previously.

   ..  image:: /_static/images/firmware/fw-update-2-leftpane.png
         :align: center

#. Select the "Cypress FX3 USB BootLoader Device" and go to Program > FX3 > I2C EEPROM.

   ..  image:: /_static/images/firmware/fw-update-3-i2c.png
         :align: center

#. Browse to the firmware .img file you downloaded earlier and click Open.

   ..  image:: /_static/images/firmware/fw-update-4-fw-image.png
         :align: center

#. The status bar at the bottom will indicate progress:

   ..  image:: /_static/images/firmware/fw-update-5-fw-progress.png
         :align: center

#. Wait for the programming to finish. The status bar at the bottom should indicate success:

   ..  image:: /_static/images/firmware/fw-update-6-fw-success.png
         :align: center

Configure the Hardware for Normal Use
-------------------------------------------

#.  With the PCB still exposed, move the jumper on header K1 back to its original position on the J9 header, either Jack or USB according to which power source you would like to use. The K1 header remains empty. This changes the board to "Boot from EEPROM" mode.

#. Disconnect and re-connect the Miniscope DAQ to USB to boot the device. Both the DAQ Power and the Scope Power indicator LEDs will be on.

#. Check the Device Manager. The Miniscope DAQ should be listed as `MINISCOPE`, under `Cameras`.

   .. image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
      :align: center

#.  Replace the four fasteners to close the Miniscope DAQ. 