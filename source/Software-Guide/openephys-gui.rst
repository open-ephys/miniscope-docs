.. _openephys_gui:

####################################################################
Open Ephys Miniscope V4 GUI
####################################################################

.. toctree::
    :hidden:

    beta-downloads
    installing-and-using-the-gui
    gui-reference
    recording

..  important::

    .. include:: beta-banner.rst

The `Open Ephys Miniscope V4 GUI <https://github.com/open-ephys/bonsai-miniscopev4-gui>`__ is a
free, open-source application developed by Open Ephys for acquiring data from the UCLA Miniscope v4
and the Miniscope DAQ. It puts everything an imaging session needs in one place: live image and
orientation display, hardware control, automatic commutator control, and recording to file.

The GUI is itself a Bonsai workflow. Launch it headless from a shortcut and it behaves like a
standalone application; drop that same workflow into a Bonsai workflow of your own and it behaves
like any other node, so it can stand in for the ``UclaMiniscopeV4`` hardware node without
disturbing anything downstream.

..  TODO(media): screenshot — replace with the GUI mid-acquisition, showing live image data,
..      running Euler angle traces, and a few console messages. 

..  image:: /_static/images/miniscopev4_gui/miniscope-gui-layout.png
    :alt:   the Open Ephys Miniscope V4 GUI window
    :align: center
    :width: 100%

|

..  grid:: 4
    :gutter: 3

    ..  grid-item-card:: Installing & Using the GUI
        :link:      /Software-Guide/installing-and-using-the-gui
        :link-type: doc
        :class-card: intro-card

        Download the GUI, install it, and run a first acquisition.

    ..  grid-item-card:: GUI Reference
        :link:      /Software-Guide/gui-reference
        :link-type: doc
        :class-card: intro-card

        Overview of how to use the Miniscope V4 GUI controls.

    ..  grid-item-card:: Recording Data
        :link:      /Software-Guide/recording
        :link-type: doc
        :class-card: intro-card

        Overview of how to record data using the Miniscope V4 GUI.

    ..  grid-item-card:: Acquisition Within Bonsai
        :link:      /Software-Guide/custom-workflows
        :link-type: doc
        :class-card: intro-card

        Work with the underlying Bonsai operators directly, from raw hardware access up to
        embedding the GUI itself as a single node.
