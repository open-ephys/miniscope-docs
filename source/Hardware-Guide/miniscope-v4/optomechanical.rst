#####################
Optomechanical Design
#####################

..  image:: /_static/images/miniscope-working-principle-schematic.webp
    :alt:   image of excitation light and emission light through the UCLA Miniscope v4's optical system
    :align: center

***********************
Optomechanical Overview
***********************

The UCLA Miniscope v4 is a miniaturized epifluorescent/widefield microscope. An LED serves as the excitation light source. The excitation filter filters the excitation light to prevent undesired wavelengths from entering the miniscope. Excitation light is reflected by the dichroic mirror and refracted by a series of lenses such that it illuminates the imaging target sufficiently uniformly. Fluoresced (emission) light is collected by the miniscope's objective, refracted by the tube lense, and transmitted through the dichroic mirror to form an image of the specimen's fluoresced light on the miniscope's sensor. The electro-tunable lens ETL (sometimes also referred to as electrowetting lens, EWL) is a lens formed by fluid in a membrane that changes shape according to the average voltage applied across the membrane, providing dynamic imaging depth adjustment.

For a more comprehensive description of the UCLA Miniscope v4's constituent parts and optomechanical design, visit the `Parts List <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Parts-List>`__ from the UCLA Miniscope v4 GitHub wiki. 

For more information, please refer to the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

..  todo:: better pictures. better descriptions

The UCLA Miniscope v4 mechanics can be thought of as comprised from four modules.

..  image:: /_static/images/ucla-miniscope-v4-submodules.webp
    :alt:   image of modules (photographs and schematics)

.. dropdown:: UCLA Miniscopes v4 Optomechanical Modules

    .. tab-set::

        .. tab-item:: Excitation Module

            ..  image:: /_static/images/excitation-module.webp
                :alt:   image of excitation module
                :align: center
                :height:    200

            *   Mounts the excitation filter against the excitation light source which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesirable light

        ..  tab-item:: Objective Module

            ..  image:: /_static/images/objective-module.webp
                :alt:   image of objective module
                :align: center
                :height:    200

            *   Mounts a combination of off-the-shelf achromatic lenses which can be swapped out to adjust the field-of-view/magnification, working distance, spatial resolution, and effective NA of the microscope. The roles of this module is to:

                *   Help illuminate the sample with excitation light from the excitation light source

                *   Collect emmision light from the sample and roughly collimate it into the excitation module  

        .. tab-item:: Emission Module

            ..  image:: /_static/images/emission-module.webp
                :alt:   image of excitation module
                :align: center
                :height:    200

            *   Mounts the emission filter against the sensor which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesirable light

            *   Mounts the dichroic mirror which reflects excitation light into the objective module and transmits emission light into the imaging sensor

            *   Mounts 3mm half ball lens which improves the illumination profile at the imaging sample

            *   Mounts 4mm diameter, 10mm focal length lens to operate as a tube lens

        .. tab-item:: PCB

            *   Mounts and electrically connects the various electronics for controlling the sensor, ETL, LED and communication with the data acquisition hardware

..            ..  image:: /_static/images/pcb-module.webp
                :alt:   image of pcb module
                :align: center
                :height:    200


***************************
Design and Production Files
***************************

All the design and production files for the UCLA Miniscope v4 PCB are available for download in the UCLA Miniscope v4's official GitHub repository: https://github.com/Aharoni-Lab/Miniscope-v4. For quick-and-easy access, direct links to optomechanical design and production files are below.

*   `Body files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2>`__

*   `Baseplate files <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Mounting_Variation_2>`__

Some operating systems come with free software that can be used to visualize STEP or STL files. There are also online viewers for these kinds of files. Common MCAD software for editing these kinds of files include Solidworks and Autodesk.

The UCLA Miniscope v4 body parts can be produced in-house with a Formlabs SLA printer or outsourced to a 3D printing services. In either case, ensure the miniscope is printed with black, non-fluorescent resin. The baseplate parts are milled from aluminum. 

For more information about procuring parts for building your own miniscope, visit the `Parts Procurement page <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Part-Procurement>`__ from the UCLA Miniscope v4 GitHub wiki.

..  todo::  does /_static/images/miniscope-working-principle-schematic.webp look blurry?

..  todo::  compact optomech BoM: ETL, two filters, dichroic, 3 achromats, 1 half ball, get screw type
