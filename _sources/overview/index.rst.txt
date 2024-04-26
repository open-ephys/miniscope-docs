
##################
Miniscope Overview
##################

*********************
Miniscope Description
*********************

Miniscopes are compact microscopes that are mounted on the heads of freely-moving animals. For imaging neural activity, the animal contains a Ca\ :sup:`2+`-dependent fluorescent molecule. As the name suggests, it only fluoresces when bound to Ca\ :sup:`2+` ions. Action potentials involve large influxes of Ca\ :sup:`2+` ions into the cell so fluorescence of these indicators can be used a proxy for neural activity.

Miniscopes confer the benefit of enabling animals to behave more naturally and explore physical space while acquiring neural data. Many miniscopes have been developed since their inception in 2011. [#]_

..  figure:: /_static/images/various-miniscopes.webp
    :alt:   image of miniscopes
    :align: left

    Open-source miniscopes released in the public domain as of 2018. (A) https://github.com/gardner-lab/FinchScope, image credit: W.A. Liberti III. (B) https://github.com/giovannibarbera/miniscope_v1.0. (C) http://www.miniscope.org. (D) https://github.com/jf-lab/chendoscope, image credit: A. Jacob, Josselyn lab. [#]_

The above figure displays some miniscopes developed as of 2018. Since then, many more miniscopes have been developed with better specs all-around (i.e. lower mass, better sensors, larger FoVs, etc.). Two-photon miniscopes have even started becoming more viable, though most miniscopes are still wide-field/epifluorescent due to prohibitevly expensive two-photon lasers and data-acquisition equpiment. To learn more about fluorescent microscopes and miniscopes, refer to the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

*************************************
Typical Full-Stack Miniscope Solution
*************************************

:doc:`/overview/data-acq-hardware` and :doc:`/overview/data-acq-software` are required to acquire data in addition to the miniscope itself (not including the Wireless UCLA Miniscope v3). Miniscope :doc:`/overview/accessories` include:

*   The :ref:`overview/accessories:Open Ephys Coaxial Commutator` prevents wired connections between a freely-moving animal and a stationary data acquisition system  

*   The :ref:`overview/accessories:MiniCAM` is prevents wired connections between 

Below is a diagram of a typical full-stack solution for acquiring data with the UCLA Miniscope v4.

..  image:: /_static/images/miniscope-hardware-software-stack.webp
    :alt:   image of hardware software stack
    :align: center

..  [#] Aharoni, D., & Hoogland, T. M. Circuit investigations with open-source miniaturized microscopes: Past, present and future. Frontiers (2019). https://www.frontiersin.org/articles/10.3389/fncel.2019.00141 

..  [#] Aharoni, D., Khakh, B.S., Silva, A.J. et al. All the light that we can see: a new era in miniaturized microscopy. Nat Methods 16, 11–13 (2018). https://doi.org/10.1038/s41592-018-0266-x

.. toctree::
    :hidden:

    miniscopes
    data-acq-hardware
    data-acq-software
    accessories
..    glossary