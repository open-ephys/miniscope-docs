.. _custom_workflows:

####################################################################
Acquisition Within Bonsai
####################################################################

.. toctree::
    :hidden:

    commutate
    save-data
    trigger

.. _bonsai_installation:

**************
Installation
**************

Everything on this page needs Bonsai and the ``OpenEphys.Miniscope`` packages installed. This
is the same setup described in the :ref:`quickstartguide`.

..  note::

    Bonsai, the ``OpenEphys.Miniscope`` packages, and the Miniscope V4 GUI all run on 64-bit Windows
    only.

#.  The Miniscope DAQ works over USB, so configure the operating system's USB settings to
    avoid suspending the device due to power management.

#.  `Download and install Bonsai <https://bonsai-rx.org/docs/articles/installation.html>`__,
    either as a portable environment or as a system-wide application.

#.  Install the following packages from the `Bonsai Package Manager
    <https://bonsai-rx.org/docs/articles/packages.html>`__:

    *   ``OpenEphys.Miniscope.Design``: an extension of the ``OpenEphys.Miniscope`` library that
        includes graphical user interfaces (GUIs). Installing ``OpenEphys.Miniscope.Design``
        automatically installs ``OpenEphys.Miniscope`` as a dependency.

    *   ``Bonsai.StarterPack``: the "standard library" for Bonsai, containing tools used in
        almost every workflow.

.. _installing_the_gui_package:

Installing the GUI Package
===============================

The GUI ships in its own package, ``OpenEphys.MiniscopeV4.Gui``, which is only needed for
:ref:`acquisition_gui` below. During the beta this package is not published to NuGet, so it
does not appear in the Bonsai package manager and has to be installed from a local file
instead. Click `here <https://gofile.me/7cMIw/0BZJIhCfh>`__ to download the package.

Follow the `Installing a Local NuGet Package in Bonsai
<https://github.com/open-ephys/wiki/wiki/Installing-a-Local-Nuget-Package-in-Bonsai>`__ article in
the Open Ephys Wiki to see how to install the package you just downloaded in Bonsai.

..  tip::

    If you only want to run the GUI as a standalone application, you can install the standalone
    installer. See :doc:`/Software-Guide/openephys-gui`.

.. _acquisition_base:

***********************************************
Connecting to the Hardware
***********************************************

The ``OpenEphys.Miniscope`` package's acquisition operators (e.g., ``UclaMiniscopeV4``) are the
foundation everything else on this page is built on. Double-clicking one of Bonsai's default
visualizers on the operator's output is enough to confirm data is flowing, but each member of the
data stream opens in its own window, with no shared time axis. See :ref:`acquisition_swap` below for
what the same acquisition looks like with the GUI's display dropped in instead, with the rest of the
workflow unchanged.

.. _acquisition_gui:

***********************************************
Using the GUI in Bonsai
***********************************************

.. _gui_visualizer_in_workflows:

Embed the GUI as a Single Node
===================================

The GUI is itself a Bonsai workflow (``MiniscopeGui.bonsai``), and it ships inside the
``OpenEphys.MiniscopeV4.Gui`` package as an embedded workflow. Drop it straight into a
workflow of your own and you get the entire GUI as a single node, with exactly the same
functionality as launching it headless; see :ref:`headless_vs_custom_workflow` for why.

#.  Start Bonsai and open the workflow you want to add the GUI to.

#.  Install the ``OpenEphys.MiniscopeV4.Gui`` package, if it is not already installed; see
    :ref:`installing_the_gui_package`.

#.  Find ``MiniscopeGui`` under the package's embedded workflows in the toolbox, and place
    it on the canvas.

    ..  image:: /_static/images/miniscopev4_gui/bonsai-toolbox-embedded-workflow.png
        :alt:   the Bonsai toolbox with the embedded MiniscopeGui workflow located under the OpenEphys.MiniscopeV4.Gui package
        :align: center
        :width: 60%

#.  Run the workflow. With nothing but this node, you get exactly the functionality
    described in :doc:`/Software-Guide/installing-and-using-the-gui`.

#.  The node's output is the Miniscope data frame, so you can connect it to any custom logic you
    like. Because it is just another node, the GUI can run alongside the rest of your workflow: a
    behavior camera acquired in the same workflow displays at the same time in a different window.

    ..  image:: /_static/downloads/bonsai-gui-node-in-workflow.svg
        :alt:   the MiniscopeGui workflow placed next to a CameraCapture node
        :align: center
        :width: 20%

.. TODO: This is currently just an SVG; we cannot embed this as a regular workflow and make
    use of the `{% include 'workflow.html' %}` HTML snippet until the NuGet package is published.
    Once the Bonsai.config file includes the OpenEphys.MiniscopeV4.Gui package, we can swap this SVG for a workflow

.. _acquisition_swap:

Swapping the Hardware Node for the GUI
=======================================

The GUI's output is the same per-frame Miniscope data stream the raw ``UclaMiniscopeV4`` node
produces, so the GUI workflow is a drop-in replacement for that node: whatever you build
downstream keeps working whether it is fed by the bare hardware node or by the GUI.

If you have already developed a processing pipeline around ``UclaMiniscopeV4``, put the GUI
workflow in the same position to gain its visualizations. Nothing downstream has to change.
Here is the :doc:`/Software-Guide/trigger` workflow with the ``UclaMiniscopeV4`` node replaced
by the ``MiniscopeGui`` workflow:

..  image:: /_static/downloads/miniscope-gui-swapped-in-for-hardware-node-commutator.svg
    :alt:   the MiniscopeGui workflow replacing the UclaMiniscopeV4 node in the trigger workflow
    :align: center
    :width: 50%

.. _gui_workflow_bandwidth:

Alongside Other Processing
===================================

Because the GUI is just another node, it can run in the same workflow as an entirely
separate piece of processing: for example, a behavior-tracking tool like SLEAP watching a
second camera, each with its own display.

Running two independent capture/encode pipelines side by side has the potential for USB bandwidth
and CPU contention to show up. This is the same effect you'd see running a video call over a webcam
while also acquiring from the Miniscope. To minimize any disruption, put any hardware on separate
USB controllers where possible, and avoid running other encode/decode-heavy software (video calls,
screen recording) during acquisition if you can.

..  TODO(workflow): a workflow combining ``MiniscopeGui`` with a second camera source
..      feeding a behavior-tracking pipeline, demonstrating that both can run and display
..      at once.
..      Suggested file: /_static/downloads/miniscopegui-with-behavior-tracking.bonsai

Running Multiple GUIs Simultaneously
=======================================

If you have multiple Miniscopes connected to one computer and want to visualize all of them from
one workflow, wrap the included workflow inside higher-order operators and run them side by side.
In the following workflow, each ``SelectMany`` contains a ``MiniscopeGui.bonsai`` embedded
workflow and nothing else.

..  image:: /_static/downloads/two-miniscope-guis-running-simultaneously.svg
    :alt:   two MiniscopeGui workflows running simultaneously, one inside each SelectMany operator
    :align: center
    :width: 20%


Tutorials
==============

To understand how the ``UclaMiniscopeV4`` can be used directly, check out the following tutorials.
Remember that everywhere the ``UclaMiniscopeV4`` node is placed, the ``MiniscopeGui.bonsai``
included workflow can be swapped in without changing the downstream logic while allowing for full
visualization with the GUI.

..  grid:: 3
    :gutter: 3

    ..  grid-item-card:: 1. Automate Commutation
        :link:      /Software-Guide/commutate
        :link-type: doc
        :class-card: intro-card

        Rotate the coaxial tether automatically from the Miniscope's orientation data, and
        control the commutator manually with keypresses.

    ..  grid-item-card:: 2. Record Data to File
        :link:      /Software-Guide/save-data
        :link-type: doc
        :class-card: intro-card

        Write image data and timestamped orientation data to disk, with a choice of video
        codecs.

    ..  grid-item-card:: 3. Trigger Recordings
        :link:      /Software-Guide/trigger
        :link-type: doc
        :class-card: intro-card

        Gate recording with a hardware digital signal, producing one file set per trigger
        pulse.

