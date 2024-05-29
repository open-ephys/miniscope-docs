###########################
Objective Lens Modification
###########################

..  warning::   Performing this modification voids any active Open Ephys warranty for this product.

..  warning::   Performing this modification requires realigning the ETL rings between the objective module and the emission module. This step can be tricky - refer to the assembly guide before attempting.

Credit for all the measurements and images on this page go to the UCLA Miniscope team. [1]_

The UCLA Miniscope v4's working distance (WD), Field-of-View (FoV), spatial resolution, and numerical aperture (NA) can be adjusted by reconfiguring on the combination of lenses used when assembling the Miniscope. 

An approximate :math:`NA` is calculated as :math:`sin(arctan(D/(2*WD)))` where :math:`D=2.7mm` for all of these lenses (for example, refer to the *Clear Aperture* field for 45-089).

The lens configurations are summarized in the table below:

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
        -   NA

    *   -   :ref:`1 <ucla-miniscope-v4/developer/mods/objective:Lens Configuration 1>`
        -   1.0 × 1.0
        -   675 ± 250
        -   0.89

    *   -   :ref:`2 <ucla-miniscope-v4/developer/mods/objective:Lens Configuration 2>`
        -   1.1 × 1.2
        -   975 ± 340
        -   0.81

    *   -   :ref:`3 <ucla-miniscope-v4/developer/mods/objective:Lens Configuration 3>`
        -   1.3 × 1.4
        -   2010 ± 400
        -   0.56

..  todo:: spatial resolution? on this table and for the three tables below

********************
Lens Configuration 1
********************

*   **FoV:** 1 × 1mm

*   **WD:** 675 ± 250µm

*   **NA:** 0.89

..  figure::    /_static/images/usaf-lens-config-1.webp
    :alt:       image of USAF target taken with lens config 1
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 1 [1]_

This is the standard UCLA Minsicope v4 lens configuration. It balances spatial resolution, FoV, WD, and NA. It is capable of deep imaging through a relay GRIN lenses and shallow imaging through a thin cranial windows.

.. edmund links don't work?


..  list-table::    Lens Configuration 1 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   45-089
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   45-089
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   63-691
        -   4mm diameter, 10mm FL achromat used in the emission module

********************
Lens Configuration 2
********************

*   **FoV:**  1.1 × 1.2mm

*   **WD:** 975 ± 340µm

*   **NA:** 0.81

..  figure:: /_static/images/usaf-lens-config-2.webp
    :alt:       image of USAF target taken with lens config 2
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 2 [1]_

Compared to lens configuration 1, lens configuration 2 extends WD which can facilitate imaging through a thicker cranial window and increases FoV which can potentially image more cells. The trade-off is a reduction in spatial resolution and NA.

..  list-table::    Lens Configuration 2 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   45-090
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   45-089
        -   3mm diameter, 6mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   63-691
        -   4mm diameter, 10mm FL achromat used in the emission module

********************
Lens Configuration 3
********************

*   **FoV:** 1.3 × 1.4mm

*   **WD:** 2010 ± 400µm

*   **NA:** 0.56

..  figure:: /_static/images/usaf-lens-config-3.webp
    :alt:       image of USAF target taken with lens config 3
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 3 [1]_

Compared to lens configuration 2, lens configuration 3 extends WD which facilitates imaging through a thicker cranial window and increases FoV which can potentially image more cells. The trade-off is a reduction in spatial resolution and NA.

..  list-table::    Lens Configuration 3 Optics
    :widths:        5 15 10 70
    :header-rows:   1

    *   -   Lens Number
        -   Vendor
        -   Part Number
        -   Description

    *   -   1
        -   Edmund Optics
        -   45-090
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   2
        -   Edmund Optics
        -   45-090
        -   3mm diameter, 9mm FL achromat used in the objective module

    *   -   3
        -   Edmund Optics 
        -   63-691
        -   4mm diameter, 10mm FL achromat used in the emission module

****************************
How To Modify Objective Lens
****************************

For all three lens configurations, the differences are contained within the objective module. It is easier and recommended having multiple objective modules each with its own lens configuration than trying to remove one set of lenses and reinserting a different set of lenses into the same objective module. The latter option increases the risk of damaging the lenses and ending up with a broken objective module.

#.  Procure the lenses you desire to use and an empty objective module

#.  Follow the steps outlined in the Objective Module section (coming soon) of the *Assembly Guide* (coming soon) using the lenses you desire instead of the default ones 

..  [1] https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Lens-Configurations
