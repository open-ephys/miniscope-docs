#########################
Firmware Update
#########################

Follow this guide to update the drivers and firmware on your Miniscope DAQ.


Updating the Drivers
-------------------------------------------

Before attempting the firmware update, manually update the Miniscope DAQ drivers to ensure they are correctly installed.

#. Download the drivers from here xxx.

#. In the Device Manger, look for the Miniscope DAQ

- If the Miniscope DAQ was working properly, it should be listed as `MINISCOPE`, under `Cameras`.

    ..  image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
            :align: center
            :height: 250px

- If the Miniscope DAQ was not being recognized, it could be listed as `Cypress FX3 USB BootLoader Device` under `Universal Serial Bus controllers`:

    ..  image:: /_static/images/firmware/driver-update-1b-listed-bootloader.png
            :align: center
            :height: 250px

    or as `WestBridge` under `Other devices`, with a warning icon:

    ..  image:: /_static/images/firmware/driver-update-1c-listed-westbridge.png
            :align: center
            :height: 250px

#. Right-click on the listing that corresponds to the Miniscope DAQ and select Update driver.

    ..  image:: /_static/images/firmware/driver-update-2-updatedriver.png
            :align: center
            :height: 250px

#. Choose *Browse my computer for drivers*

    ..  image:: /_static/images/firmware/driver-update-3-browse.png
            :align: center
            :height: 250px

#. Browse for the folder into which you downloaded the driver files in Step 1.

    ..  image:: /_static/images/firmware/driver-update-4-browse.png
            :align: center
            :height: 250px

#. Check that `Cypress FX3 USB BootLoader Device` is listed, and click *Next*.

    ..  image:: /_static/images/firmware/driver-update-5-next.png
            :align: center
            :height: 250px

    You should see a success message.

    ..  image:: /_static/images/firmware/driver-update-6-success.png
            :align: center
            :height: 250px

Download the Updater Application
-------------------------------------------

#. Download the `EZ USB Suite <https://www.infineon.com/design-resources/development-tools/sdk/usb-controllers-sdk/ez-usb-fx3-software-development-kit>`__ which contains the Cypress Control Center we will use to update the firmware.

#. Follow the download instructions. The webpage requires you to create a login.

#. Double-click on the executable to install the application.

Download Firmware Image
-------------------------------------------

#. Download the firmware image from here xxx.

Configure the Hardware for Boot Mode
-------------------------------------------

*Required components: Miniscope DAQ, USB3.0 cable (Micro Type B ↔ Type A)*
*Required tools: 2.5 mm hex key for opening the screws on the Miniscope DAQ's enclosure*

#. Open the Miniscope-DAQ's enclosure by using the 2.5 mm hex key to unscrew all four fasteners. It might be necessary to apply gentle pressure on the nuts on the bottom of the DAQ to prevent them from turning when unscrewing the screws.

#.  With the PCB exposed, move the jumper on header J9 to close the header labeled K1 as shown in the picture below. The J9 header remains empty. This changes the board to "Boot from USB" mode.

    ..  image:: /_static/images/firmware/DAQ_board_Jumper_J9.jpeg
            :align: center
            :height: 250px

#. Connect the DAQ to the PC using a USB3.0 connection. The DAQ Power indicator LED will be on. It should be listed in the Device Manager as `Cypress FX3 USB BootLoader Device` under `Universal Serial Bus controllers`:

    ..  image:: /_static/images/firmware/driver-update-1b-listed-bootloader.png
            :align: center
            :height: 250px

Firmware Upload
-------------------------------------------

#. Access the *Cypress USB Control Center*.

    -  The most straightforward way is to search for *CyControl* in the Windows Applications Menu:

    ..  image:: /_static/images/firmware/fw-update-1a-cycontrolicon.png
            :align: center
            :height: 250px

    - You can also access the Cypress Control Center from the EZ USB Suite:

    If you opened the *EZ USB Suite* application,

    ..  image:: /_static/images/firmware/fw-update-1b-ezusbicon.png
            :align: center
            :height: 250px

    Navigate to the CY Tools Menu > Control Center:

    ..  image:: /_static/images/firmware/fw-update-1b-cytoolsmenu.png
            :align: center
            :height: 250px


#. The Miniscope DAQ should be listed on the left panel as "Cypress FX3 USB BootLoader Device". If not, revise the hardware was configured as explained in the previous section.

    ..  image:: /_static/images/firmware/fw-update-2-leftpane.png
            :align: center
            :height: 250px


#. Select the "Cypress FX3 USB BootLoader Device" and go to Program > I2C EEPROM.

    ..  image:: /_static/images/firmware/fw-update-3-i2c.png
            :align: center
            :height: 250px


#. Browse to the firmware .img file you downloaded earlier and click Open.

    ..  image:: /_static/images/firmware/fw-update-4-fw-image.png
            :align: center
            :height: 250px

#. The status bar at the bottom will indicate progress:

    ..  image:: /_static/images/firmware/fw-update-5-fw-progress.png
            :align: center
            :height: 250px

#. Wait for the programming to finish. The status bar at the bottom should indicate success:

    ..  image:: /_static/images/firmware/fw-update-6-fw-success.png
            :align: center
            :height: 250px

Configure the Hardware for Normal Use
-------------------------------------------

#.  With the PCB still exposed, move the jumper on header J9 to close the header labeled K1 as shown in the picture below. The J9 header remains empty. This changes the board to "Boot from USB" mode.

#.  Set the jumper back to the position on the J9 header, either Jack or USB according to which power source you would like to use. The K1 header remains empty.

#. Disconnect and re-connect the Miniscope DAQ to USB to booth the device.

#. Check the Device Manager. The Miniscope DAQ should be listed as `MINISCOPE`, under `Cameras`.

    ..  image:: /_static/images/firmware/driver-update-1a-listed-miniscope.png
            :align: center
            :height: 250px

#.  Replace the four fasteners to close the Miniscope DAQ. 