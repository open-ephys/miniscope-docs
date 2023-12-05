
###########################
Modify Lenses Configuration
###########################

..  warning::   Performing this modification voids any active Open Ephys warranty

The UCLA Miniscope v4's working distance (WD), Field-of-View (FOV), spatial resolution, and effective numerical aperture (NA) can be adjusted by reconfiguring on the combination of lenses used when assembling the Miniscope.

*******************
Lens Configurations
*******************

..  figure::     /_static/images/tube-lens-objective-lens-schematic.webp
    :alt:       image from https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/img/Lens_Cross_Section.PNG
    :scale:     50%
    :align:     center
    
    Cross-sectional schematic of tube lens/objective optical assembly [1]_

..  list-table::    Optical Properties for Three Optical Configurations
    :header-rows:   1

    *   -   Lens Configuration
        -   FoV (mm)
        -   WD (µm)

    *   -   :ref:`1 <ucla-miniscope-v4/developer/common-mods/lenses-combo:Lens Configuration 1>`
        -   1.0 × 1.0
        -   675 ± 250

    *   -   :ref:`2 <ucla-miniscope-v4/developer/common-mods/lenses-combo:Lens Configuration 2>`
        -   1.1 × 1.2
        -   975 ± 340

    *   -   :ref:`3 <ucla-miniscope-v4/developer/common-mods/lenses-combo:Lens Configuration 3>`
        -   1.3 × 1.4
        -   2010 ± 400

Lens Configuration 1
=====================

*   **FoV:** 1mm × 1mm

*   **WD:** 675um ± 250um

..  figure::    /_static/images/usaf-lens-config-1.webp
    :alt:       image of USAF target taken with lens config 1
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 1 [1]_

This is considered to be the standard UCLA Minsicope v4 lens configuration. It balances spatial resolution, FoV, WD, and NA. It is capable of deep imaging through a relay GRIN lenses and shallow imaging through a thin cranial windows.

..  list-table::    Lens Configuration 1 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   `45-089 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   `45-089 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   `63-691 <https://www.edmundoptics.com/p/4mm-dia-x-10mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/18408/>`__
        -   4mm diameter, 10mm FL achromat used in the emission module

Lens Configuration 2
====================

*   **FoV:**  1.1mm × 1.2mm

*   **WD:** 975um ± 340um

..  figure:: /_static/images/usaf-lens-config-2.webp
    :alt:       image of USAF target taken with lens config 2
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 2 [1]_

Compared to lens configuration 1, lens configuration 2 extends the WD which can facilitate imaging through a cranial window and enlargens the FoV which can potentially image more cells. The trade off is a reduction in spatial resolution and NA.

..  list-table::    Lens Configuration 2 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   `45-090 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   `45-089 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   `63-691 <https://www.edmundoptics.com/p/4mm-dia-x-10mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/18408/>`__
        -   4mm diameter, 10mm FL achromat used in the emission module

Lens Configuration 3
====================

*   **FoV:** 1.3mm × 1.4mm

*   **WD:** 2010um ± 400um

..  figure:: /_static/images/usaf-lens-config-3.webp
    :alt:       image of USAF target taken with lens config 3
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 3 [1]_

Compared to lens configuration 2, lens configuration 3 extends the WD which can facilitate imaging through a cranial window and enlargens the FoV which can potentially image more cells. The trade off is a reduction in spatial resolution and NA.

..  list-table::    Lens Configuration 3 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   `45-090 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   `45-090 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   `63-691 <https://www.edmundoptics.com/p/4mm-dia-x-10mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/18408/>`__
        -   4mm diameter, 10mm FL achromat used in the emission module

********************
How To Modify Lenses
********************

Since the tube lens doesn't change and only the lenses in the objective module do change in all three of the above configurations, it is easier having a separate objective module for each desired lens combination than trying to swap the lenses in the objective module whenever you want to reconfigure the lens combination

#.  Procure the lenses you desire to use and and an empty objective module

#.  Follow the steps outlined in the :doc:`/ucla-miniscope-v4/user/assembly/objective` section of the Assembly Guide using the lenses you desire instead of the default ones 

..  [1] https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Lens-Configurations
