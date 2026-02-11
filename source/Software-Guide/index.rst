.. _software_guide:

#########################
Software Guide
#########################

.. toctree::
    :hidden:
    
    commutate
    save-data
    trigger

There are two compatible software programs to acquire Miniscope data. Both platforms are free, open-source, and widely adopted in the neuroscience
community.

..  grid::

    ..  grid-item-card:: Bonsai Package OpenEphys.Miniscope
        :link-type: ref
        :link: tutorial_intro
        :class-card: intro-card
        :img-top: /_static/images/bonsai-logo.png
        :img-alt: bonsai logo
        :class-img-top: software-card-img
        :columns: 5

        Acquire data from the Miniscope DAQ in Bonsai, a highly extensible visual programming language that enables collected data to interface with other hardware in real-time, and perform online software processing and experimental control with supported tools. This package was developed by Open Ephys.
        
        *Click to start browsing the tutorials.*

    ..  grid-item-card:: Miniscope-DAQ-QT-Software
        :link-type: url
        :link: https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/wiki
        :class-card: intro-card
        :img-top: /_static/images/miniscope-logo.png
        :img-alt: Miniscope-DAQ-QT-Software logo
        :class-img-top: software-card-img
        :columns: 5

        The original software developed by the UCLA Miniscope Team that enables data acquisition from the Miniscope v4 and the MiniCAM via the Miniscope DAQ, as well as webcams.
        
        It software is deprecated and not supported by Open Ephys.
        
        *Click to navigate to its documentation site.*

.. _tutorial_intro:

*********************************************
About the Tutorials
*********************************************

While not strictly required, it is highly recommended to study the `Bonsai Language Guide <https://bonsai-rx.org/docs/articles/observables.html>`__ before reading this Software Guide. 

The tutorials available in this section for the OpenEphys.Miniscope Bonsai package build on the :ref:`quickstartguide`, and progressively add more functionality, so it is recommended to follow them in order.

#. :doc:`/Software-Guide/commutate`

#. :doc:`Save image and orientation data to file </Software-Guide/save-data>`

#. :doc:`Trigger data acquisition with a trigger signal </Software-Guide/trigger>`

.. #. :doc:`View and process image and orientation data in real-time <>`

.. #. :doc:`Use a purpose-built GUI to operate the miniscope <>`

.. #. :doc:`Sync miniscope and behavioral camera frames via hardware <>`

