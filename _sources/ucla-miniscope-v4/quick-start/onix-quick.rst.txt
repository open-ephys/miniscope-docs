########################
ONIX & UCLA Miniscope v4
########################

..  todo::  replace with image of ONIX 2.0 once that exists

.. image:: /_static/images/onix_ucla-miniscope-v4.webp
    :alt: photograph of ucla miniscope v4 & onix

This guide serves as quick hardware-validation and familiarization with the UCLA Miniscope v4 and ONIX Data Acquisition hardware. 

..  include::   includes.rst
    :start-line:    2
    :end-line:      4

.. todo:: Complete this section after ONIX 2.0

..
    ****************
    Connect Hardware
    ****************

    #.  If you haven't already done so, open your PC and insert the ONIX host PCIe board into a PCIe slot. Confirm that the retention clip on your motherboard PCIe slot is clicked into position such that it retains the PCIe ONIX board and maintains electrical continuity. Fasten the PCIe ONIX board into your PC’s case for additional mechanical stability.

    #.  Disconnect any previously connected hardware from ONIX and UCLA Miniscope v4. Connect only the following hardware for this guide:

        *   Connect ONIX to the UCLA Miniscope v4 using the provided coaxial SMA plug ↔ MMCX plug tether:
            
            .. image:: /_static/images/sma-plug_mmcx-plug_cable.webp
                :alt: photograph of provided coaxial SMA plug ↔ MMCX plug cable

            *   Insert the cable’s SMA plug into the ONIX breakout board’s SMA jack labeled `A`. Gently hand-tighten the SMA connector with light-force until you are no longer able to turn the connector

                .. image:: /_static/images/cable-sma-plug_onix-sma-jack.webp
                    :alt: photograph of sma plug going into miniscope-daq sma jack

            *   Insert the cable’s MMCX plug into the UCLA Miniscope v4’s MMCX jack. Confirm that a click is felt and heard before proceeding from this step.

                .. image:: /_static/images/cable-mmcx-plug_ucla-miniscope-v4-mmcx-jack.webp
                    :alt: photograph of sma plug going into miniscope-daq sma jack

        *   Connect the ONIX breakout board to the ONIX host PCIe board (already installed in your computer) using the provided SDR plug ↔ SDR plug cable:

            .. image:: /_static/images/sdr-plug_sdr-plug_cable.webp
                :alt: photograph of provided coaxial SMA plug ↔ MMCX plug cable

            *   Insert one of the cable’s SDR plugs into the ONIX breakout board's SDR jack.

                .. image:: /_static/images/cable-sdr-plug_onix-breakout-sdr-jack.webp
                    :alt: photograph of sdr plug going into onix breakout sdr jack

            *   Insert the cable’s other SDR plug into the ONIX host PCIe board's SDR jack.

                .. image:: /_static/images/cable-sdr-plug_onix-host-sdr-jack.webp
                    :alt: photograph of sdr plug going into onix host sdr jack

    #.  Confirm that the __ indicators on the ONIX breakout board are illuminated before proceeding from this step as indicated in the below potos. If not _, refer to troubleshoot.

        ..  todo::  fix the above visual confirmation of lock

    **************************************
    Download, Install and Configure Bonsai
    **************************************

    *   If you have not already done so, 
        
        *   `Download and Install Bonsai <https://bonsai-rx.org/docs/articles/installation.html>`_

        *   `Install the necessary Bonsai Packages: <https://bonsai-rx.org/docs/articles/packages.html>`_

            *   Bonsai.StarterPack

            *   Bonsai.ONIX

    *   Download and open the following Bonsai workflow:

        ..  Note::  You will not be able to open the workflow if ONIX is not already properly installed and connected

    **************************************************
    Interact with the UCLA Miniscope v4 through Bonsai
    **************************************************

    #.  Start the Bonsai workflow and test the various features:

    .. todo::   this will be filled out once we are closer to releasing onix. this can probably borrow content from miniscope-daq docs, but it will remain empty for now because the specifics will change
