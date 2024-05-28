
##################
Miniscope Overview
##################

*********************
Miniscope Description
*********************

Miniscopes are miniaturized fluorescent microscopes that can be mounted on the heads of freely-moving animals. For imaging neural activity, the animal contains a Ca\ :sup:`2+`-dependent fluorescent molecule. As the name suggests, it only fluoresces when bound to Ca\ :sup:`2+` ions. Action potentials involve influxes of Ca\ :sup:`2+` ions into the cell so fluorescence of these indicators can be used a proxy for neural activity. Miniscopes confer the benefit of enabling animals to behave more naturally and explore physical space while acquiring neural data. Many miniscopes have been developed since their inception in 2011. [#]_ [#]_ 

..  figure:: /_static/images/various-miniscopes.webp
    :alt:   image of miniscopes
    :align: left

    A selection of open-source miniscopes developed as of 2018. (A) https://github.com/gardner-lab/FinchScope, image credit: W.A. Liberti III. (B) https://github.com/giovannibarbera/miniscope_v1.0. (C) http://www.miniscope.org. (D) https://github.com/jf-lab/chendoscope, image credit: A. Jacob, Josselyn lab. [#]_

Many more miniscopes have been developed that specialize in certain features such decreased mass, incrased FoVs, etc. To learn more about fluorescent microscopes and miniscopes, refer to the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

************************
Typical Miniscope System
************************

A typical miniscope data acquisition system based on the UCLA Miniscope design includes :doc:`/overview/data-acq-hardware` and :doc:`/overview/data-acq-software` in addition to the miniscope itself. Optional :doc:`/overview/accessories` include:

*   An :ref:`overview/accessories:Open Ephys Coaxial Commutator` to prevent twisting of wired connections between a freely-moving animal and a stationary data acquisition system  

*   A :ref:`overview/accessories:MiniCAM` is to record animal movement

The diagram below depicts a typical system for acquiring data with the UCLA Miniscope v4.

..  image:: /_static/images/miniscope-hardware-software-stack.webp
    :alt:   image of hardware software stack
    :align: center

..  [#] Ghosh, K., Burns, L., Cocker, E. et al. Miniaturized integration of a fluorescence microscope. Nat Methods 8, 871–878 (2011). https://doi.org/10.1038/nmeth.1694

..  [#] Aharoni, D., & Hoogland, T. M. Circuit investigations with open-source miniaturized microscopes: Past, present and future. Frontiers (2019). https://www.frontiersin.org/articles/10.3389/fncel.2019.00141 

..  [#] Aharoni, D., Khakh, B.S., Silva, A.J. et al. All the light that we can see: a new era in miniaturized microscopy. Nat Methods 16, 11–13 (2018). https://doi.org/10.1038/s41592-018-0266-x

.. toctree::
    :hidden:

    data-acq-hardware
    data-acq-software
    accessories
..    glossary