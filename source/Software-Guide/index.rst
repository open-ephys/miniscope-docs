.. _software_guide:

##############################
Software Guide
##############################

.. toctree::
    :hidden:

    openephys-gui
    custom-workflows

There are currently two methods of acquiring data from a Miniscope V4: the **Open Ephys Miniscope V4
GUI**, which can be run as an application or embedded as a group workflow in Bonsai, or the
**Miniscope-DAQ-QT-Software**, created by the UCLA Miniscope Team.

Open Ephys Miniscope V4 GUI
##############################

..  grid:: 2
    :gutter: 2
    :margin: 0

    ..  grid-item::
        :columns: 8

        ..  image:: /_static/images/miniscopev4_gui/miniscope-gui-window.png
            :alt:   the Open Ephys Miniscope V4 GUI window
            :width: 100%

    ..  grid-item::
        :columns: 4
        :class: sd-d-flex-column sd-align-major-center sd-align-minor-center

        ..  button-link:: https://gofile.me/7cMIw/uoFCjHjIE
            :color: primary
            :shadow:

            Download the Open Ephys Miniscope V4 GUI (Windows)

..  important::

    The Open Ephys Miniscope V4 GUI is currently in **beta**. Its interface and behavior
    may change in future releases, and this documentation will be updated to match. Some
    screenshots and workflow examples are still placeholders and will be filled in as
    they become available.

Open Ephys develops the free, open-source **Open Ephys Miniscope V4 GUI** for acquiring data
from the UCLA Miniscope v4 and the Miniscope DAQ. It puts everything an imaging session needs
in one place: live image and orientation display, hardware control, automatic commutator
control, and recording to file.

Feedback from beta testers
-------------------------------------

While the GUI is in beta, all issues and comments should be directed to the `GitHub issues page
<https://github.com/open-ephys/bonsai-miniscopev4-gui/issues>`__ so we can track any and all issues
found. Please put any comments or concerns as a new issues, as well as any requests for features, so
we can prioritize what to add or fix next.

Miniscope-DAQ-QT-Software (deprecated)
#######################################

The original software developed by the UCLA Miniscope Team that enables data acquisition from the
Miniscope v4 and the MiniCAM via the Miniscope DAQ, as well as webcams. It supports commutation, but
it is deprecated and is not supported by Open Ephys. Click `here
<https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/releases>`__ to download the appropriate
application.
