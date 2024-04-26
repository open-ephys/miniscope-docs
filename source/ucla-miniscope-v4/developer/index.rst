
###############
Developer Guide
###############

The developer guide is intended to acquaint the user with the miniscope's design and production files.

All the design and production files for the UCLA Miniscope v4 PCB are available for download in the UCLA Miniscope v4's official GitHub repository: https://github.com/Aharoni-Lab/Miniscope-v4. To find design and production files of the or learn about the optomechanical design, navigate to one of the two following guides:

*   :ref:`ucla-miniscope-v4/developer/index:Optomechanical Design`

*   :ref:`ucla-miniscope-v4/developer/index:Electrical Design`

The developer guide also contains information about common :doc:`/ucla-miniscope-v4/developer/mods` to configure the UCLA Minisope v4 for your experiment.

*********************
Optomechanical Design
*********************

Optomechanical Overview
=======================

..  image:: /_static/images/miniscope-working-principle-schematic.webp
    :alt:   image of excitation light and emission light through the UCLA Miniscope v4's optical system
    :align: center
    
The UCLA Miniscope v4 is a miniaturized epifluorescent/widefield microscope. An LED serves as the excitation light source. The excitation filter filters the excitation light to prevent undesired wavelengths from entering the miniscope. Excitation light is reflected by the dichroic mirror and refracted by a series of lenses such that it illuminates the imaging target sufficiently uniformly. Fluoresced (emission) light is collected by the miniscope's objective, refracted by the tube lense, and transmitted through the dichroic mirror to form an image of the specimen's fluoresced light on the miniscope's sensor. The electro-tunable lens ETL (sometimes also referred to as electrowetting lens, EWL) is a lens formed by fluid in a membrane that changes shape according to the average voltage applied across the membrane, providing dynamic imaging depth adjustment.

For a more comprehensive description of the UCLA Miniscope v4's constituent parts and optomechanical design, visit the `Parts List <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Parts-List>`__ from the UCLA Miniscope v4 GitHub wiki. 

For more information, please refer to the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

Design and Production Files
===========================

All the design and production files for the UCLA Miniscope v4 PCB are available for download in the UCLA Miniscope v4's official GitHub repository: https://github.com/Aharoni-Lab/Miniscope-v4. For quick-and-easy access, direct links to optomechanical design and production files are below.

*   `Body files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2>`__

*   `Baseplate files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Mounting_Variation_2>`__

Some operating systems come with free software that can be used to visualize STEP or STL files. There are also online viewers for these kinds of files. Common MCAD software for editing these kinds of files include Solidworks and Autodesk.

The UCLA Miniscope v4 body parts can be produced in-house with a Formlabs SLA printer or outsourced to a 3D printing services. In either case, ensure the miniscope is printed with black, non-fluorescent resin. The baseplate parts are milled from aluminum. 

For more information about procuring parts for building your own miniscope, visit the `Parts Procurement page <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Part-Procurement>`__ from the UCLA Miniscope v4 GitHub wiki.

..
    The UCLA Miniscope v4 mechanics can be thought of as comprised from four modules.
    ..  image:: /_static/images/ucla-miniscope-v4-submodules.webp
        :alt:   image of modules (photographs and schematics)

    .. dropdown:: UCLA Miniscopes v4 Modules

        .. tab-set::

            .. tab-item:: Excitation Module

                ..  image:: /_static/images/excitation-module.webp
                    :alt:   image of excitation module
                    :align: center

                *   Mounts the excitation filter against the excitation light source which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesirable light

            ..  tab-item:: Objective Module

                ..  image:: /_static/images/objective-module.webp
                    :alt:   image of objective module
                    :align: center

                *   Mounts a combination of off-the-shelf achromatic lenses which can be swapped out to adjust the field-of-view/magnification, working distance, spatial resolution, and effective NA of the microscope. The roles of this module is to:

                    *   Help illuminate the sample with excitation light from the excitation light source

                    *   Collect emmision light from the sample and roughly collimate it into the excitation module  

            .. tab-item:: Emission Module

                ..  image:: /_static/images/emission-module.webp
                    :alt:   image of excitation module
                    :align: center

                *   Mounts the emission filter against the sensor which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesirable light

                *   Mounts the dichroic mirror which reflects excitation light into the objective module and transmits emission light into the imaging sensor

                *   Mounts 3mm half ball lens which improves the illumination profile at the imaging sample

                *   Mounts 4mm diameter, 10mm focal length lens to operate as a tube lens

            .. tab-item:: PCB

                ..  image:: /_static/images/pcb-module.webp
                    :alt:   image of pcb module
                    :align: center

                *   Mounts and electrically connects the various electronics for controlling the sensor, ETL, LED and communication with the data acquisition hardware

*****************
Electrical Design
*****************

..  image:: /_static/images/ucla-miniscope-v4-layers-separate.svg
    :alt:   image of pcb layers
    :align: center

..  todo:: fix styles for drop down:format coming out dum

..
    Electrical Overview
    ===================

    ..  todo::  thicker board outlines 

    It is helpful to understand the working principle of the UCLA Miniscope v4's PCB if you desire to design your own. Explore the following drop-down menu to learn about the UCLA Miniscope v4's PCB modules. 

    ..  dropdown::  UCLA Miniscopes v4 PCB Modules

        ..  tab-set::

            ..  tab-item::  Modules Overview

                ..  image:: /_static/images/ucla-miniscope-v4-sch-hierarchy.svg
                    :alt:   image of pcb schematic (serializer-power)
                    :align: center

                *   The PCB is organized into the following modules: serializer-power module, Python480 (camera sensor) module, microcontroller module, LED-EWL module, and IMU module

                *   These modules are each a self-contained flap in the flex-rigid UCLA Miniscope v4 PCB and connect through copper traces embedded in the flex-PCB material

            ..  tab-item::  Serializer-Power Module

                ..  image:: /_static/images/ucla-miniscope-v4-sch-serpow.svg
                    :alt:   image of pcb schematic (serializer-power)
                    :align: center

                *   The serializer with its peripheral circuitry (some passives and an oscillator) serialize parallel data from the camera sensor so that it can be sent to the data acquisition hardware via coax. The serializer also converts commands from the data acquisition hardware (which forwards commands from the PC) to i2c for processing by other hardware on the PCB.

                *   The bottom circuit filters the main supply rail.

                *   The U.FL connector enables a coaxial connection that carries data between the data acquisition hardware and the UCLA Miniscope v4 PCB.

            ..  tab-item::  Python480 (Camera Sensor) Module

                ..  image:: /_static/images/ucla-miniscope-v4-sch-python480.svg
                    :alt:   image of pcb schematic (python480)
                    :align: center

                *   The Python480 with its peripheral circuitry (some passives and a voltage reference) collects light from the sample.

                *   The status LED and is toggled by the microcontroller via the Q1 transistor.

            ..  tab-item::  Microcontroller Module

                ..  image:: /_static/images/ucla-miniscope-v4-sch-mcu.svg
                    :alt:   image of pcb schematic (microcontroller)
                    :align: center

                *   The microcontroller with its peripheral circuitry (some passives) process commands from Bonsai or Miniscope-DAQ-QT-GUI which are forwarded to the serializer through the data acquisition hardware. Such commands are forwarded on the i2c bus and includes:

                    *   setting the Python480's registers to control exposure, frame rate, gain, and LED timing by operating as an SPI master.

                    *   setting the operation of the LED driver.

                *   The pogo pads are for programming the microcontroller and reading SPI data.

            ..  tab-item::  LED-EWL Module

                ..  image:: /_static/images/ucla-miniscope-v4-sch-ledewl.svg
                    :alt:   image of pcb schematic (led/ewl drivers)
                    :align: center

                *   The LED driver with its peripheral circuitry (some passives and a digital potentiometer that is set by i2c commands from the serializer) controls the excitation light intensity.

                *   The electrotunable/electrowetting lens (ETL/EWL) driver with its peripheral circuitry (i.e. passives and an i2c buffer IC to convert the 1.8V i2c bus to a 3.3V i2c bus for compatibility with the EWL driver) drives the lens that operates as the UCLA Miniscope v4's dynamic focusing mechanism. It is configured by i2c directly by the serializer.

            ..  tab-item::  IMU Module

                ..  image:: /_static/images/ucla-miniscope-v4-sch-imu.svg
                    :alt:   image of pcb schematic (imu)
                    :align: center

                *   The BNO055 with its peripheral circuitry sense orientation and send quarternion data to the serializer over i2c 

Design & Production Files
=========================

All the design and production files for the UCLA Miniscope v4 PCB are available for download in the UCLA Miniscope v4's official GitHub repository: https://github.com/Aharoni-Lab/Miniscope-v4. For quick-and-easy access, direct links to electrical design and production files are below.

Design Files
------------

*   Schematic files (`pdf <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Rigid-Flex/KiCad/PDF/Miniscope-v4-Rigid-Flex_4_41.pdf>`__, `sch <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Rigid-Flex/KiCad/Miniscope-v4-Rigid-Flex.sch>`__)

*   `PCB file <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Rigid-Flex/KiCad/Miniscope-v4-Rigid-Flex.kicad_pcb>`__

The .sch and .kicad_pcb files above can be opened in `KiCAD <https://www.kicad.org/>`__, a user-friendly, free, and open-source eCAD software (`KiCAD download <https://www.kicad.org/download/>`__). A .pdf file is also available for inspecting the schematic without KiCAD.

Production files
----------------

*   `BoM file <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Rigid-Flex/KiCad/Output/BOM/Miniscope-v4-Rigid-Flex_bom_4_41.csv>`__    

*   `Gerbers files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Rigid-Flex/KiCad/Output/Gerbers_4_41>`__

*   `Pick-and-Place (PnP) files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Rigid-Flex/KiCad/Output/PnP/PnP_v_4_41>`__

The Bill of Material (BoM) file is a csv file. Any text editor can be used to open a csvs file, but a spreadsheet software is recommended. The Gerber files are inspectable using most eCAD softwares or online Gerber viewers. PCB fabricators typically require Gerber files to produce a custom PCB. The PnP files are also csv files. PCB assemblers typically require PnP files to place and solder all the components onto your PCB. It is also possible to assemble your own UCLA Miniscope v4 PCB, but that is outside of the scope of this guide.

..  todo::  does /_static/images/miniscope-working-principle-schematic.webp look blurry? need better module images

..  todo::  compact optomech BoM: ETL, two filters, dichroic, 3 achromats, 1 half ball, get screw type

..  toctree::
    :hidden:

    mods