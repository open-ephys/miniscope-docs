.. _software_guide:

#########################
Software Guide
#########################

.. toctree::
    :hidden:

    openephys-gui
    custom-workflows

Open Ephys Miniscope V4 GUI
-----------------------------

..  important::

    The Open Ephys Miniscope V4 GUI is currently in **beta**. Its interface and behavior
    may change in future releases, and this documentation will be updated to match. Some
    screenshots and workflow examples are still placeholders and will be filled in as
    they become available.

    During the beta the GUI is distributed as a direct download rather than through
    NuGet, so it does not appear in the Bonsai package manager.

..  image:: /_static/images/miniscopev4_gui/miniscope-gui-window.png
    :alt:   the Open Ephys Miniscope V4 GUI window
    :align: center
    :width: 100%

Open Ephys develops the free, open-source **Open Ephys Miniscope V4 GUI** for acquiring data
from the UCLA Miniscope v4 and the Miniscope DAQ. It puts everything an imaging session needs
in one place: live image and orientation display, hardware control, automatic commutator
control, and recording to file.

Unzip the download and run ``MiniscopeV4Gui-Setup-<version>.exe``. The installer requires no
administrator rights, and it creates Desktop and Start Menu shortcuts that launch the GUI as a
standalone application; nothing else has to be installed first. See
:doc:`/Software-Guide/openephys-gui` for what the GUI does, and
:doc:`/Software-Guide/installing-and-using-the-gui` for the full walkthrough.

..  button-link:: https://gofile.me/7cMIw/lQe4F0dBX
    :color: primary
    :expand:
    :shadow:

    Download the Open Ephys Miniscope V4 GUI

..  note::

    The Miniscope V4 GUI runs on 64-bit Windows only, as do the
    ``OpenEphys.Miniscope`` Bonsai packages it is built on.

Miniscope-DAQ-QT-Software (deprecated)
---------------------------------------

..  grid:: 1

    ..  grid-item-card:: Miniscope-DAQ-QT-Software
        :link-type: url
        :link: https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/wiki
        :class-card: intro-card
        :columns: 12

        The original software developed by the UCLA Miniscope Team that enables data
        acquisition from the Miniscope v4 and the MiniCAM via the Miniscope DAQ, as well as
        webcams. It supports commutation, but it is deprecated and is not supported by
        Open Ephys.

        *Click to navigate to its documentation site.*
