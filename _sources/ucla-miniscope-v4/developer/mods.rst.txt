#############
Modifications
#############

..  warning::   Performing any of these modifications voids any active Open Ephys warranty for this product.

The user can perform the following modifications to adapt the UCLA miniscope v4 to their respective experiment: 

*   An :ref:`ucla-miniscope-v4/developer/mods:Objective Lens Modification` to adjust magnification/field-of-view, working distance, spatial resolution, and effective NA (emission light collection efficiency).

*   A :ref:`ucla-miniscope-v4/developer/mods:Spectral Modification` to image a fluorophore that is excited by and/or emits bands of light that are not compatible with the UCLA Miniscope v4's standard LED/dichroic mirror/filters configuration. 

***************************
Objective Lens Modification
***************************

..  warning::   Performing this modification requires realigning the ETL rings between the objective module and the emission module. This step can be tricky - refer to the assembly guide before attempting.

Credit for all the measurements and images on this page go to the UCLA Miniscope team. [1]_

The UCLA Miniscope v4's working distance (WD), Field-of-View (FoV), spatial resolution, and numerical aperture (NA) can be adjusted by reconfiguring on the combination of lenses used when assembling the Miniscope. 

An approximate :math:`NA` is calculated as :math:`sin(arctan(D/(2*WD)))` where :math:`D=2.7mm` for all of these lenses (for example, refer to the *Clear Aperture* field for `45-089 <https://www.edmundoptics.com/p/3mm-dia-x-6mm-fl-mgfsub2sub-coated-achromatic-doublet-lens/5580/>`__).

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

    *   -   :ref:`1 <ucla-miniscope-v4/developer/mods:Lens Configuration 1>`
        -   1.0 × 1.0
        -   675 ± 250
        -   0.89

    *   -   :ref:`2 <ucla-miniscope-v4/developer/mods:Lens Configuration 2>`
        -   1.1 × 1.2
        -   975 ± 340
        -   0.81

    *   -   :ref:`3 <ucla-miniscope-v4/developer/mods:Lens Configuration 3>`
        -   1.3 × 1.4
        -   2010 ± 400
        -   0.56

..  todo:: spatial resolution? on this table and for the three tables below

Lens Configuration 1
====================

*   **FoV:** 1 × 1mm

*   **WD:** 675 ± 250µm

*   **NA:** 0.89

..  figure::    /_static/images/usaf-lens-config-1.webp
    :alt:       image of USAF target taken with lens config 1
    :scale:     50%
    :align:     center

    Image of USAF target taken with lens configuration 1 [1]_

This is the standard UCLA Minsicope v4 lens configuration. It balances spatial resolution, FoV, WD, and NA. It is capable of deep imaging through a relay GRIN lenses and shallow imaging through a thin cranial windows.

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

How To Modify Objective Lens
============================

For all three lens configurations, the differences are contained within the objective module. It is easier and recommended having multiple objective modules each with its own lens configuration than trying to remove one set of lenses and reinserting a different set of lenses into the same objective module. The latter option increases the risk of damaging the lenses and ending up with a broken objective module.

#.  Procure the lenses you desire to use and an empty objective module

#.  Follow the steps outlined in the Objective Module section (coming soon) of the *Assembly Guide* (coming soon) using the lenses you desire instead of the default ones 

..  [1] https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Lens-Configurations

*********************
Spectral Modification
*********************

The UCLA Miniscope v4 as sold by Open Ephys is compatible with green indicators e.g. GCaMP6f (:ref:`ucla-miniscope-v4/developer/mods:Standard`) or red indicators e.g. jRGECO1a (:ref:`ucla-miniscope-v4/developer/mods:Lime`), though it can also be modified for :ref:`other <ucla-miniscope-v4/developer/mods:Other>` fluorophores as well.

Standard
========

470nm (blue) LED excitation light source (`LXZ1-PB01 <https://lumileds.com/wp-content/uploads/files/DS105.pdf>`__) to image a green indicator e.g. `GCaMP6f <https://www.fpbase.org/protein/gcamp6f/>`__: 

.. figure:: /_static/images/gcamp6f.svg
    :alt:   plot of emission/excitation spectra of GCaMP6f

*   1 `ET470/40x <https://www.chroma.com/products/parts/et470-40x>`__ (4x4x1 mm) excitation filter

*   1 `ET525/50m <https://www.chroma.com/products/parts/et525-50m>`__ (4x4x1 mm) emission filter

*   1 `T495lpxr <https://www.chroma.com/products/parts/t495lpxr>`__ (4x6x1 mm) dichroic mirror

..  figure:: /_static/images/spectraviewer-standard-config.webp
    :alt:   plot of standard emission/excitation filters and dichroic mirror transmission spectra

    `All three transmission spectra on a single plot <https://www.chroma.com/spectra-viewer?parts=25332,26210,25281>`__.

    +-------------+-----------+-----------+-----------+
    | **Filter**  | ET470/40x | ET525/50m | T495lpxr  |
    +-------------+-----------+-----------+-----------+
    | **Color**   | Blue      | Red       | Black     |
    +-------------+-----------+-----------+-----------+

The standard UCLA Miniscope v4 is sold by Open Ephys in DIY kits and already assembled with LED (already soldered), filters, and dichroic mirror included.

Lime
====

560nm (yellow-green) LED excitation light source (`LXZ1-PX01 <https://lumileds.com/wp-content/uploads/files/DS105.pdf>`__) to image a red indicator e.g. `jRGECO1a <https://www.fpbase.org/protein/jrgeco1a/>`__:

.. figure:: /_static/images/jrgeco1a.svg
    :alt:   plot of emission/excitation spectra of jRGECO1a

*   1 `ET560/40x <https://www.chroma.com/products/parts/et560-40x>`__ (4x4x1 mm) excitation filter

*   1 `ET630/75m <https://www.chroma.com/products/parts/et630-75m>`__ (4x4x1 mm) emission filter

*   1 `T585lpxr <https://www.chroma.com/products/parts/t585lpxr>`__ (4x6x1 mm) dichroic mirror

..  figure:: /_static/images/spectraviewer-lime-config.webp
    :alt:   plot of lime emission/excitation filters and dichroic mirror transmission spectra

    `All three spectra on a single plot <https://www.chroma.com/spectra-viewer?parts=25291,24194,25292>`__

    +---------------+-----------+-----------+-----------+
    | **Filter**    | ET560/40x | ET630/75m | T585lpxr  |
    +---------------+-----------+-----------+-----------+
    | **Color**     | Blue      | Red       | Black     |
    +---------------+-----------+-----------+-----------+

The lime UCLA Miniscope v4 is sold by Open Ephys in DIY kits with LED (already soldered) included. **Filters and dichroic mirror are excluded and must be acquired separately.**

Other
=====

Is it also possible to adapt the UCLA Miniscope v4 to fluorophores with spectral characteristics that aren't compatible with standard or lime configurations. Refer to `Chroma <https://www.chroma.com/>`__ (a `worker coop <https://www.chroma.com/company>`__ from which Open Ephys sources its filters) to look at your options for swapping out the filters and dichroic mirror. They produce and sell a variety of `off-the-shelf filters/dichroic mirrors <https://www.chroma.com/products/optical-filters>`__ and also assist in producing `custom solutions <https://www.chroma.com/custom-oem-filter-design/>`__ for your experiments. The process of choosing the best set of light source, filters, and dichroic is often an iterative balancing process that attempts to maximize emission light into the sensor, minimize excitation light into the sensor, and maximize excitation light into the sample. This maximizes SNR and minimizes heat dissipation from the LED/LED driver. 

.. all this commented-out text below is too much text, but could be useful at some point.

..
    Consider the following bullet points in the process of choosing your custom spectral UCLA Miniscope v4:

    *   When selecting a fluorophor, consider the wavelength-dependent sensor sensitivity and wavelength-dependent tissue scattering/absorption.

    also consider extinction ratio, brightness, quantum yield, blablabla

    *   When selecting an excitation light source for your particular fluorophore:

        *   Confirm that the LED's footprint matches the footprint of the standard/lime LED to maximize solderability onto the UCLA Miniscope v4 PCB. For example, the LEDs in the `LUXEON Z Color Line series <https://lumileds.com/wp-content/uploads/files/DS105.pdf>`__ span a range of transmission spectra and are drop-in replacements for the ones that are on the UCLA Miniscope v4.

        *   The transmission spectrum of the selected excitation light source should:

            *   maximize the area under the product of itself and the fluorophore's excitation spectrum. Ideally, its peak is centered around the fluorophore's excitation spectrum's peak.
        
            *   minimize the area under the product of itself and the fluorophore's emission spectrum. Ideally, it does not overlap with the fluorophre's emission epectrum.

            .. note:: Attempting simultaneous optimization of both above bullet points is a contradictory process because there is often significant overlap between a fluorophore's excitation spectrum and its emission spectrum. If in doubt, prioritize the second bullet point. It is likely more detrimental to the experiment to filter out emission light (which might end up happening if your excitation light source's transmission spectrum bleeds into the flourophore's emission spectrum) than to filter out excitation light. After all, it is also possible to increase the intensity of excitation light to compensate for filtered-out excitation light as long as heat dissipation doesn't become an issue. 

    *   When selecting an excitation filter for your particular fluorophore, confirm that its upper-bound cut-off wavelength transmits as much excitation light as possible into the sample while being below the emission filter's lower-bound cut-off wavelength. Ideally, the filter's bandpass spectrum spans the entire range in which the excitation light source's transmission spectrum is significantly more than zero.

    *   When selecting an emission filter for your particular fluorophore, confirm that its lower-bound cut-off wavelength transmits as much emission light as possible into the sensor while being above the the excitation filter's upper-bound cut-off wavelength. Ideally, the filter's bandpass spans the entire range in which the fluorophor's emission transmission spectrum is significantly more than zero.

    *   When selecting a dichroic filter for your particular fluorophore, confirm its cut-off wavelength is between the exictation filter's upper cut-off wavelength and emission filter's lower cut-off wavelength. To comply with the UCLA Miniscope v4's optical layout, choose a high-pass dichroic filter.

How To Modify LED/Dichroic/Filters
==================================

To reconfigure the LED/Dichroic/Filters combination, follow the *Assembly Guide* (coming soon) instructions while substituting standard excitation/emission filters and dichroic mirror with the ones you'd like to use. It is easier and recommended to perform this modification starting with an unassembled UCLA Miniscope v4 than starting with an already-assembled UCLA Miniscope v4.

Note that if you desire to use an LED that is not included in the lime or standard configurations, you must solder it yourself which requires additional materials and know-how during the assembly process.