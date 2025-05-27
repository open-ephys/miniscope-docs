###
GUI
###

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate.svg
    :alt:   image of workflow
    :width: 50%
    :align: center

After following this tutorial, the user will be able to open an example GUI constructed in Bonsai for
interfacing with the UCLA Miniscope v4, Miniscope DAQ and Open Ephys torque-free commutator with the following features:

-   toggle between one of three online data-processing pipelines for viewing (raw, saturation, ΔF/F)
-   control various properties related to the Miniscope hardware, saving data, and the ΔF/F signal-processing pipeline
-   toggle recording manually or with a hardware input trigger
-   view real-time pixel brightness histogram
-   view real-time digital input data
-   commutate the UCLA Miniscope V4 tether automatically with the Open Ephys torque-free commutator

This example GUI is intended to provide easy-to-use access to the key features of the libraries that are available in Bonsai to work with this Miniscope system. We believe it will be useful as-is for most users. However, since the GUI is itself programmed in Bonsai, users can extend the layout or remove features to fit their experimental needs.

..  note::
    This is the first release of this Bonsai GUI for Miniscopes. If you have feedback, (i.e. feature requests, usability issues, bug fixes, etc.), please submit them as a `GitHub issue <https://github.com/open-ephys/miniscope-docs/issues/new>`__!

..  toctree::
    :hidden:

    hardware
    software
    tutorial
    description