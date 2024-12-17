#####################
Spectral Modification
#####################

..  warning::   Performing this modification voids any active Open Ephys warranty for this product.

The UCLA Miniscope v4 as sold by Open Ephys is compatible with green indicators e.g. GCaMP6f (:ref:`ucla-miniscope-v4/developer/mods/spectral:Standard`) or red indicators e.g. jRGECO1a (:ref:`ucla-miniscope-v4/developer/mods/spectral:Lime`), though it can also be modified for :ref:`other <ucla-miniscope-v4/developer/mods/spectral:Other>` fluorophores as well.

********
Standard
********

470nm (blue) LED excitation light source (`LXZ1-PB01 <https://luxeonstar.com/wp-content/uploads/documentation/ds105.pdf>`__) to image a green indicator e.g. `GCaMP6f <https://www.fpbase.org/protein/gcamp6f/>`__: 

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

****
Lime
****

560nm (yellow-green) LED excitation light source (`LXZ1-PX01 <https://luxeonstar.com/wp-content/uploads/documentation/ds105.pdf>`__) to image a red indicator e.g. `jRGECO1a <https://www.fpbase.org/protein/jrgeco1a/>`__:

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

*****
Other
*****

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

************************************
How To Modify Spectral Compatibility
************************************

To reconfigure the spectral compatibility (e.g. the LED/Dichroic/Filters combination), follow the *Assembly Guide* (coming soon) instructions while substituting standard excitation/emission filters and dichroic mirror with the ones you'd like to use. It is easier and recommended to perform this modification starting with an unassembled UCLA Miniscope v4 than starting with an already-assembled UCLA Miniscope v4.

Note that if you desire to use an LED that is not included in the lime or standard configurations, you must solder it yourself which requires additional materials and know-how during the assembly process.