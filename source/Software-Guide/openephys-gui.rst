.. _openephys_gui:

####################################################################
Open Ephys Miniscope V4 GUI
####################################################################

.. toctree::
    :hidden:

    installing-and-using-the-gui
    gui-reference
    recording

The `Open Ephys Miniscope V4 GUI <https://github.com/open-ephys/bonsai-miniscopev4-gui>`__ is a
free, open-source application developed by Open Ephys for acquiring data from the UCLA Miniscope V4
and the Miniscope DAQ. It puts everything an imaging session needs in one place: live image and
orientation display, hardware control, automatic commutator control, and recording to file.

Launch the GUI as a standalone application from a shortcut or drop the workflow node into a Bonsai
workflow of your own and it behaves like any other node, so it can stand in for the
``UclaMiniscopeV4`` hardware node without disturbing anything downstream.

..  TODO(media): screenshot — replace with the GUI mid-acquisition, showing live image data,
..      running Euler angle traces, and a few console messages. 

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

        ..  button-link:: https://gofile.me/7cMIw/lQe4F0dBX
            :color: primary
            :shadow:

            Download the Open Ephys Miniscope V4 GUI (Windows)

To install, download and run ``MiniscopeV4Gui-Setup-<version>.exe``. This is everything you need to
run the GUI. Follow :doc:`/Software-Guide/installing-and-using-the-gui`, which walks through the
installation and a first acquisition.

To build your own acquisition around the GUI instead of running it on its own, see
:doc:`/Software-Guide/custom-workflows`, which also covers installing the GUI as a Bonsai
package.
