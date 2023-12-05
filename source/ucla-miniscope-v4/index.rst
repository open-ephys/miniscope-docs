
#################
UCLA Miniscope V4
#################

..  image:: /_static/images/ucla-miniscope-v4-rotating.webp
    :alt:   image of ucla miniscope rotating and example data

To understand the full feature set of the UCLA Miniscope v4, refer to the :ref:`overview/miniscopes:Comparison Chart`.

***********************************
UCLA Miniscope v4 Working Principle
***********************************

To understand the miniscope concept broadly, refer to the :ref:`overview/index:What Is a Miniscope?` section.

The UCLA Miniscope v4 is a miniaturized epiflourescent (1P) microscope. An LED serves as the excitation light source. Excitation light is reflected by the dichroic mirror and refracted by a series of lenses into the specimen of interest. Flouresced (emission) light is collected by the miniscope's objective, transmitted by the dichroice mirror, and refracted by a series of lenses to form an image of the specimen's flouresced light on the miniscope's sensor.

.. todo:: does this schematic look blurry?

..  image:: /_static/images/miniscope-working-principle-schematic.webp
    :alt:   image of excitation light and emission light through the UCLA Miniscope v4's optical system

Two filters and a dichroic mirror are utilized to ensure that that minimal excitation light contaminates the data. Ideally, the only light present at the sensor is emission light from the sample. The electro-tunable lens ETL (sometimes also referred to as electrowetting lens EWL) is a lens formed by water whose meniscus  changed according to the voltage applied to the water, effectively changing the imaging depth.

A more in-depth description of the UCLA Miniscope v4's working principle is outside of the scope of this documentation. For more information, please refer to https://github.com/Aharoni-Lab/Miniscope-v4 and the relevant parts of the 2021 Miniscope Workshop video `Imaging principles & Miniscope design <https://www.youtube.com/watch?v=bHA08xrshHo>`__.

.. toctree::
    :hidden:

    quick-start/index
    user/index
    developer/index
    faq-troubleshoot/index
