
#########################################
Modify LED/Dichroic/Filters Configuration
#########################################

..  warning::   Performing this modification voids any active Open Ephys warranty for this product

The UCLA Miniscope v4 as sold by Open Ephys is compatible with green indicators (e.g. GCAMP6f) or red indicators (e.g. RCaMP): :ref:`standard <ucla-miniscope-v4/developer/common-mods/led-filters-dichroic-combo:Standard>` and :ref:`lime <ucla-miniscope-v4/developer/common-mods/led-filters-dichroic-combo:Lime>`, though it can also be modified for :ref:`other <ucla-miniscope-v4/developer/common-mods/led-filters-dichroic-combo:Other>` fluorophores as well with sufficient know-how.

***********************************
LED/Dichroic/Filters Configurations
***********************************

Standard
========

470nm (blue) LED excitation light source (`LXZ1-PB01 <https://lumileds.com/wp-content/uploads/files/DS105.pdf>`__) to image a green indicator e.g. `GCaMP6f <https://www.fpbase.org/protein/gcamp6f/>`__: 

*   1 `ET470/40x <https://www.chroma.com/products/parts/et470-40x>`__ (4x4x1 mm) excitation filter

*   1 `ET525/50m <https://www.chroma.com/products/parts/et525-50m>`__ (4x4x1 mm) emission filter

*   1 `T495lpxr <https://www.chroma.com/products/parts/t495lpxr>`__ (4x6x1 mm) dichroic mirror

..  figure:: /_static/images/spectraviewer-standard-config.webp
    :alt:   plot of standard emission/excitation filters and dichroic mirror transmission spectra

    `All three transmission spectra on a single plot <https://www.chroma.com/spectra-viewer?parts=25332,26210,25281>`__.

    +-----------+-------+
    | Filter    | Color |
    +===========+=======+
    | ET470/40x | Blue  |
    +-----------+-------+
    | ET525/50m | Red   |
    +-----------+-------+
    | T495lpxr  | Black |
    +-----------+-------+    

The standard UCLA Miniscope v4 is sold by Open Ephys with *LED (already soldered), filters, and dichroic mirror **included***.

Lime
====

560nm (yellow-green) LED excitation light source (`LXZ1-PB01 <https://lumileds.com/wp-content/uploads/files/DS105.pdf>`__) to image a red indicator e.g. `RCaMP <https://www.fpbase.org/protein/rcamp/>`__:

*   1 `ET560/40x <https://www.chroma.com/products/parts/et560-40x>`__ (4x4x1 mm) excitation filter

*   1 `ET630/75m <https://www.chroma.com/products/parts/et630-75m>`__ (4x4x1 mm) emission filter

*   1 `T585lpxr <https://www.chroma.com/products/parts/t585lpxr>`__ (4x6x1 mm) dichroic mirror

..  figure:: /_static/images/spectraviewer-lime-config.webp
    :alt:   plot of lime emission/excitation filters and dichroic mirror transmission spectra

    `All three spectra on a single plot <https://www.chroma.com/spectra-viewer?parts=25291,24194,25292>`__

    +-----------+-------+
    | Filter    | Color |
    +===========+=======+
    | ET560/40x | Blue  |
    +-----------+-------+
    | ET630/75m | Red   |
    +-----------+-------+
    | T585lpxr  | Black |
    +-----------+-------+    

The lime UCLA Miniscope v4 is sold by Open Ephys with *LED (already soldered) **included*** and *filters and dichroic mirror **excluded***. The filters and dichroic mirror must be acquired separately.

Other
=====

Is it also possible to adapt the UCLA Miniscope v4 to a fluorophore other than one that shares spectral characteristics of GCAMP6f or RCaMP. Refer to `Chroma <https://www.chroma.com/>`__ (a `worker coop <https://www.chroma.com/company>`__ from which Open Ephys sources its filters) to look at your options for swapping out the filters and dichroic mirror. They produce and sell a variety of `off-the-shelf filters/dichroic mirrors <https://www.chroma.com/products/optical-filters>`__ and also help in producing `custom solutions <https://www.chroma.com/custom-oem-filter-design/>`__ for your experiments. If you would like to configure your UCLA Miniscope v4 for a different fluorophore, consider the wavelength-dependent sensor sensitivity and wavelength-dependent tissue scattering/absorption.

***************************************
How To Reconfigure LED/Dichroic/Filters
***************************************

To reconfigure the LED/Dichroic/Filters combination, follow the :doc:`/ucla-miniscope-v4/user/assembly/index` instructions while substituting standard excitation/emissions filters and dichroic mirror with the ones you'd like to use. It is easier to perform this modification starting with an unassembled UCLA Miniscope v4 than starting with an already-assembled UCLA Miniscope v4.