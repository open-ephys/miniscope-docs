#################
UCLA Miniscope V4
#################

..  todo:: redo this figure - it bothers me how it freezes. also the miniscope's phase isn't monotonically increasing (look close at first 10-20 frames)

..  image:: /_static/images/ucla-miniscope-v4-rotating.webp
    :alt:   image of ucla miniscope rotating and example data
    :align: center


.. The miniscope....

To learn about concept of a miniscope, refer to the :doc:`/overview/index`.

To quickly start using the UCLA Miniscope v4, refer to the :doc:`/ucla-miniscope-v4/quick/index`

To start acquiring data with the UCLA Miniscope v4, refer to the :doc:`/ucla-miniscope-v4/user/index`

To learn how the UCLA Miniscope v4 works, refer to the :doc:`/ucla-miniscope-v4/developer/index`.

***************************************
UCLA Miniscope v4 Features & Properties
***************************************

..  todo::  format this better

Mechanical Properties:

*   **Mass:** <3g

*   **Dimensions:** 14.5 × 18 × 22.5mm

Optical Properties:

*   **FoV:** 1 × 1mm

*   **WD:** 675 ± 250µm

    *   The dimension following the ± symbol refers to the WD's dynamic range from the UCLA Miniscope v4's electrotunable lens

*   The above specifications can be adjusted by reconfiguring the objective module

*   **GRIN Lens Compatiblity:** relay GRIN lenses (i.e. :math:`pitch = 0.5n, n=1, 2, 3...`)

*   **Spectral Compatiblity:** 
    
    *   Common green fluorophores such as GCaMP 
    
    *   Common red fluorophores such as jRGECO

Sensor (Python480) Features:

*   **Adjustable Frame Rate:** 10, 15, 20, 25, or 30 fps

*   **Adjustable Exposure:** three discrete levels (low, medium, and high) 

*   **Bit Depth:** 10

*   **Sensor Pixel Dimensions:** 608 pixels × 608 pixels

Software Features:

*   **GUI Compatibility:** Bonsai GUI (recommended) or UCLA-Miniscope-DAQ-Software (deprecated)

*   Sensor settings and imaging depth adjustable through software

*   Real-time visualization and logging of orientation and image data

**Additional Features:**

*   On-board orientation sensor (BNO055)

.. toctree::
    :hidden:

    quick/index
    user/index
    developer/index
    faq-troubleshoot-resources/index
