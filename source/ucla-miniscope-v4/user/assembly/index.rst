
########
Assembly
########

..  note::  Proceed to the :doc:`/ucla-miniscope-v4/user/data-acq/index` guide if your UCLA Miniscope v4/s is/are already assembled.

The UCLA Miniscope v4 can be thought of as comprised from four modules.

..  image:: /_static/images/ucla-miniscope-v4-submodules.webp
    :alt:   image of modules (photographs and schematics)

To contextualize the assembly process, a breakdown of each module is provided. For a broader overview of how the UCLA Miniscope v4 functions, refer to the :ref:`ucla-miniscope-v4/index:UCLA Miniscope v4 Working Principle` section of this documentation.

..  todo:: fix the images so that they're more uniform?

.. dropdown:: Breakdowns of UCLA Miniscopes v4's Modules

    .. tab-set::

        .. tab-item:: Excitation module

            ..  image:: /_static/images/excitation-module.webp
                :alt:   image of excitation module
                :align: center

            Mounts the excitation filter against the excitation light source which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesired light not from the sample

        ..  tab-item:: Objective module

            ..  image:: /_static/images/objective-module.webp
                :alt:   image of objective module
                :align: center

            Mounts a combination of off-the-shelf achromatic lenses which can be swapped out to adjust the the field-of-view/magnification, working distance, spatial resolution, and effective NA. These lenses:

            *   Illuminate the sample with excitation light from the excitation light source

            *   Collect emmision light from the sample and roughly collimates it into the excitation module  

        .. tab-item:: Emission module

            ..  image:: /_static/images/emission-module.webp
                :alt:   image of excitation module
                :align: center

            Mounts the emission filter against the sensor which blocks wavelengths of light that could pollute the UCLA Miniscope v4's sensor with undesired light not from the sample

            Mounts the dichroic mirror which reflects excitation light into the objective module and transmits emission light into the imaging sensor

            Mounts 3mm half ball lens which alters the illumination profile at the imagining sample

            Mounts 4mm , 10mm focal length lens to ___

        .. tab-item:: PCB

            ..  image:: /_static/images/pcb-module.webp
                :alt:   image of pcb module
                :align: center

            Mounts the various electronics for controlling the sensor, ETL, LED and communication with the data acquisition hardware

The following assembly instructions are divided into distinct steps according to the UCLA Miniscope v4's four modules in addition to a :doc:`/ucla-miniscope-v4/user/assembly/preparation` step and a :doc:`/ucla-miniscope-v4/user/assembly/validate-finish` step.

..  todo::
    fix the stuff under here

..  warning::

    *   For the filters and dichroic, the coated surface faces the incoming light

    *   The arrows on the diagram point towards the coated surface and you must keep to this orientation. The arrows on the side of the filter/dichroic should point towards the coated surface

    *   The coated surface has a more opaque/mirror-like appearance than the uncoated surface. The uncoated surface through which you are able to see the edges of the cube of glass

    *   Avoid working on metal tables

    *   Use electrostatic gloves

When assembling and using the Miniscope, please take care with the printed circuit board (PCB). The circuitry is exposed on the outside of the scope and can be damaged by electrostatic charges. Prevent this damage by never placing the scope on metal or other conductive surfaces and wearing electrostatic-safe gloves if possible.


..  toctree::
    :hidden:

    preparation
    excitation
    objective
    emission
    pcb
    validate-finish
