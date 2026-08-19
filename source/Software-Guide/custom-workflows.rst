.. _custom_workflows:

####################################################################
Acquisition Within Bonsai
####################################################################

.. toctree::
    :hidden:

    commutate
    save-data
    trigger

..  important::

    .. include:: beta-banner.rst

..  note::

    The Open Ephys Miniscope V4 GUI is built on the ``OpenEphys.Miniscope`` Bonsai package, and
    everything it does can be done by working in Bonsai directly.

There are three levels to build at, roughly in order of how much of the GUI's own tooling you
bring along:

:Base:      Talk directly to the hardware with the raw ``OpenEphys.Miniscope`` operators and
            Bonsai's own built-in visualizers. See :ref:`acquisition_base`.

:Design:    Add the visualizer tooling from ``OpenEphys.Miniscope.Design`` for one task at a
            time (commutation, recording, triggering) without pulling in the rest of the
            GUI. See :ref:`acquisition_design`.

:GUI:       Embed the GUI's own workflow for its complete display and hardware control in a
            single node. See :ref:`acquisition_gui`.

.. _acquisition_base:

***********************************************
Base: Talking Directly to the Hardware
***********************************************

The ``OpenEphys.Miniscope`` package's acquisition operators (e.g., ``UclaMiniscopeV4``) are the
foundation everything else on this page is built on. Double-clicking one of Bonsai's default
visualizers on the operator's output is enough to confirm data is flowing, but each member of the
data stream opens in its own window, with no shared time axis. See :ref:`acquisition_swap` below for
what the same acquisition looks like with the GUI's display dropped in instead, with the rest of the
workflow unchanged.

.. _acquisition_design:

***********************************************
Design: Visualizer-Focused Tutorials
***********************************************

These tutorials are for the cases the full GUI doesn't cover: when acquisition has to be
interleaved with other hardware, when you need online processing or closed-loop control, or
when the recording logic has to differ from the modes the GUI provides. They use the
``OpenEphys.Miniscope.Design`` Bonsai package, the same visualizer tooling the GUI itself
is built on, for one task at a time: commutation, recording, or triggering.

*   **Build in Bonsai** when you need behavior the GUI does not offer.

*   **View with the GUI** while you do. Bonsai's built-in visualizers show one member of the
    data stream at a time, in separate windows. The GUI shows all of it at once, with the
    display tools you actually need at the rig (i.e., the saturation view, :math:`\Delta F/F`,
    max projection, reference-image overlay, histogram, and the orientation and
    digital-input plots on a shared time axis). Each tutorial below notes how to use the GUI
    to view the data it acquires.

..  note::

    While not strictly required, it is highly recommended to study the `Bonsai Language
    Guide <https://bonsai-rx.org/docs/articles/observables.html>`__ before working through
    these tutorials.

Before You Start
===================================

These tutorials build on the :ref:`quickstartguide`, which covers connecting the hardware,
installing Bonsai, and installing the ``OpenEphys.Miniscope.Design`` and ``Bonsai.StarterPack``
packages. Each tutorial adds more functionality to the last, so it is best to follow them in order.

The Tutorials
===================================

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

.. _acquisition_gui:

***********************************************
GUI: Embedding the Full Interface
***********************************************

.. _gui_visualizer_in_workflows:

Embed the GUI as a Single Node
===================================

The GUI is itself a Bonsai workflow (``MiniscopeGui.bonsai``), and it ships inside the
``OpenEphys.MiniscopeV4.Gui`` package as an embedded workflow. Drop it straight into a
workflow of your own and you get the entire GUI as a single node, with exactly the same
functionality as launching it headless; see :ref:`headless_vs_custom_workflow` for why.

#.  Start Bonsai and open the workflow you want to add the GUI to.

#.  Install the ``OpenEphys.MiniscopeV4.Gui`` package, if it is not already installed. During
    the beta this package is not on NuGet, so it has to be installed from a local file rather
    than the Bonsai package manager; see :doc:`/Software-Guide/beta-downloads`.

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
