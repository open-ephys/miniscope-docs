.. _daq_firmware_update:

##################################################
Firmware Update
##################################################

Follow these steps to update the firmware on your Miniscope DAQ. 

..  important:: 
    These instructions assume the device is currently working normally (e.g. 
    listed as ``MINISCOPE`` in Windows Device Manager). If this is not the case 
    or you would like more in-depth instructions, please refer to the 
    :ref:`firmware manual <daq_firmware_details>`.

**Required Materials**

#. Miniscope DAQ
#. USB3.0 cable (Micro Type B ↔ Type A)
#. 2.5 mm hex key

Step 1: Configure the Hardware for Bootloader Mode
----------------------------------------------------

#. Disconnect the Miniscope DAQ from the PC.

#. Open the enclosure using the 2.5 mm hex key to unscrew the four fasteners.

#. Move the jumper on header **J9** to close header **K1**. The J9 header
   remains empty.

   *(v3.4 DAQ only: also move the jumper on the bottom left of the PCB to the
   right-most position to disable EEPROM write protect.)*

   ..  image:: /_static/images/firmware/DAQ_bootloader_mode_labelled.png
       :align: center
       :width: 600px

#. Reconnect the DAQ to the PC. It should appear in Windows Device Manager as
   ``Cypress FX3 USB BootLoader Device`` under ``Universal Serial Bus
   controllers``.

   .. note::
        If it appears as ``WestBridge`` instead, you must install the bootloader
        driver before continuing. See the :ref:`daq_firmware_details` for instructions.

Step 2: Upload the Firmware
-----------------------------

#. Download and unzip the firmware uploader:

   .. list-table::
      :widths: 45 15 15
      :header-rows: 1

      * - Resource
        - Version
        - Release Date
      * - :download:`Miniscope Firmware Uploader </_static/downloads/OpenEphys.Miniscope.Uploader.1.1.4.zip>`
        - 1.1.4
        - 2026.04.20

#. Run the executable and allow it when prompted.

#. Confirm ``Cypress FX3 USB BootLoader Device`` is selected in the drop-down,
   then click **Program**.

#. Wait for programming to complete. A success message will appear when done.

#. Disconnect the DAQ from the PC.

Step 3: Restore Normal Operation
----------------------------------

#. Move the jumper on header **K1** back to its original position on the **J9**
   header. The K1 header remains empty.

   *(v3.4 DAQ only: also move the jumper on the bottom left of the PCB back to
   the left-most position to re-enable EEPROM write protect.)*

   ..  image:: /_static/images/firmware/DAQ_usb_power_labelled.png
       :align: center
       :width: 600px

#. Replace the four fasteners to close the enclosure.

#. Reconnect the DAQ to the PC. It should appear in Device Manager as
   ``UCLA/Open Ephys Miniscope DAQ v3`` under ``Cameras``.

The DAQ is ready for use.