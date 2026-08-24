.. _openephys_gui:

####################################################################
Open Ephys Miniscope V4 GUI
####################################################################

.. toctree::
    :hidden:

    installing-and-using-the-gui
    gui-reference
    recording

The `Open Ephys Miniscope V4 GUI
<https://github.com/open-ephys/bonsai-miniscope-gui>`__ is a free, open-source
application developed by Open Ephys for acquiring data from the UCLA Miniscope
V4 and the Miniscope DAQ. It puts everything an imaging session needs in one
place: live image and orientation display, hardware control, automatic
commutator control, and recording to file. *The GUI can be run in two modes*:

**1. Standalone application.** To use the the GUI as a standalone application,
follow :doc:`/Software-Guide/installing-and-using-the-gui` for installation and
usage instructions.

.. image:: /_static/images/miniscopev4_gui/miniscopev4-gui-all-streams.png
    :alt:   The standalone Open Ephys Miniscope V4 GUI window
    :width: 80%
    :align: center


**2.** ``MiniscopveV4Gui`` **Bonsai operator.** The `MiniscopveV4Gui` operator
allows the GUI to placed into a  `Bonsai <https://bonsai-rx.org/>`__ workflow,
which enables its integration with a huge variety of other tools and real-time
processing capabilities. Follow :doc:`/Software-Guide/custom-workflows` for
installation and usage instructions.

.. image:: /_static/images/miniscopev4_gui/gui-in-workflow.png
    :alt:   The standalone Open Ephys Miniscope V4 GUI along with SLEAP pose estimation
    :width: 80%
    :align: center

