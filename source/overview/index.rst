
##################
Miniscope Overview
##################

********************
What Is a Miniscope?
********************

    Demonstration of a UCLA Miniscope v3 in action. (a) A mouse with a head-mounted miniscope. (b) Cross-sectional rendering of the Miniscope optical path. Blue, excitation path; green, emission optical path; GRIN, gradient-index lens. (c) Maximum projection of a 10-minute motion-corrected Miniscope recording of hippocampal CA1 pyramidal neurons labeled with GCaMP6f. (d) Spatial footprints of identified neurons from the recording in c. Scale bar in (d) applies to (c). [#]_

Miniscopes are compact microscopes that are mounted on the heads of freely-moving animals. For the purpose of imaging neural activity, the animal contains a Calcium-dependent flourescent indicator which are chemicals that only flouresce when bound to Calcium ions. Action potentials involve large influxes of Calcium ions into the cell so flourescence of these indicators can be used a proxy for neural activity.

Miniscopes confer the benefit of enabling animals to behave more naturally and explore physical space while acquiring neural data. Many kinds of miniscopes have been developed since the original by Mark Schnitzer. They were popularized by Daniel Aharoni and a collaboration of people at UCLA where the UCLA Miniscopes were developed. Though two-photon miniscopes are becoming more viable, miniscopes by and large are epifluorescent.  

To learn more about fluorescent microscopes and miniscopes, refer to the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

..  figure:: /_static/images/various-miniscopes.webp
    :alt:   image of miniscopes
    :align: left

    Open-source miniscopes released in the public domain as of 2018. (A) https://github.com/gardner-lab/FinchScope, image credit: W.A. Liberti III. (B) https://github.com/giovannibarbera/miniscope_v1.0. (C) http://www.miniscope.org. (D) https://github.com/jf-lab/chendoscope, image credit: A. Jacob, Josselyn lab. [#]_

..  note::  The Open Ephys Miniscope Documentation only contains information that is related to software, hardware, and miniscopes that Open Ephys sells or supports. Although the above brief description of the miniscope landscape mentions various other miniscopes, further information regarding those is outside the scope of this documentation.

****************************************
Additional Miniscope Hardware & Software
****************************************

In addition to the miniscope itself, :doc:`/overview/data-acq-hardware` and :doc:`/overview/data-acq-software` are both necessary to acquire data. :doc:`Other hardware commonly used with miniscopes </overview/accessories>` include:

*   The :ref:`overview/accessories:Open Ephys Coaxial Commutator` prevents wired connections between a freely-moving animal and a stationary data acquisition system  

*   The :ref:`overview/accessories:UCLA MiniCAM` is prevents wired connections between 

Below is a diagram of a typical full stack solution for acquiring data with the UCLA Miniscope v4 and a couple of Open Ephys accessories.

..  image:: /_static/images/miniscope-hardware-software-stack.webp
    :alt:   image of hardware software stack

..  [#] Aharoni, D., Khakh, B.S., Silva, A.J. et al. All the light that we can see: a new era in miniaturized microscopy. Nat Methods 16, 11–13 (2018). https://doi.org/10.1038/s41592-018-0266-x

..  [#] Aharoni, D., & Hoogland, T. M. Circuit investigations with open-source miniaturized microscopes: Past, present and future. Frontiers (2019). https://www.frontiersin.org/articles/10.3389/fncel.2019.00141 

.. toctree::
    :hidden:

    miniscopes
    data-acq-hardware
    data-acq-software
    accessories