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

.. _gui_visualizer_in_workflows:

***************************************************
Embed the GUI as a Single Node
***************************************************

The GUI is itself a Bonsai workflow (``MiniscopeGui.bonsai``), and it ships inside the
``OpenEphys.MiniscopeV4.Gui`` package as an embedded workflow. Drop it straight into a
workflow of your own and you get the entire GUI as a single node, with exactly the same
functionality as launching it headless; see :ref:`headless_vs_custom_workflow` for why.

#.  Start Bonsai and open the workflow you want to add the GUI to.

#.  Install the ``OpenEphys.MiniscopeV4.Gui`` package from the Bonsai package manager, if it
    is not already installed.

#.  Find ``MiniscopeGui`` under the package's embedded workflows in the toolbox, and place
    it on the canvas.

#.  Run the workflow. With nothing but this node, you get exactly the functionality
    described in :doc:`/Software-Guide/installing-and-using-the-gui`.

#.  The node's output is the Miniscope data frame, so you can connect it to any custom logic you
    like. Because it is just another node, the GUI can run alongside the rest of your workflow: a
    behavior camera acquired in the same workflow displays at the same time in a different window.

..  TODO(media): screenshot — the Bonsai toolbox with the embedded ``MiniscopeGui`` workflow
..      located under the ``OpenEphys.MiniscopeV4.Gui`` package.
..      Suggested file: /_static/images/miniscopev4_gui/bonsai-toolbox-embedded-workflow.png

..  TODO(media): screenshot — a small example workflow with the ``MiniscopeGui`` node placed
..      and its output branching into custom logic, ideally beside a behavior camera source.
..      This makes the "GUI as one node in a bigger workflow" idea concrete.
..      Suggested file: /_static/images/miniscopev4_gui/bonsai-gui-node-in-workflow.png

Working in Bonsai three levels to build at, roughly in order of how much of the
GUI's own tooling you bring along:

:Base:      Talk directly to the hardware with the raw ``OpenEphys.Miniscope`` operators and
            Bonsai's own built-in visualizers. See :ref:`acquisition_base`.

:Design:    Add the visualizer tooling from ``OpenEphys.Miniscope.Design`` for one task at a
            time (commutation, recording, triggering) without pulling in the rest of the
            GUI. See :ref:`acquisition_design`.

:GUI:       Embed the GUI's own workflow, as just shown, for its complete display and
            hardware control in a single node. See :ref:`acquisition_gui` for two more ways
            to build around it.

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

.. _acquisition_gui:

***********************************************
GUI: Building Around the Full Interface
***********************************************

The example above embeds the whole GUI as one node. Two more ways to build around it:

.. _gui_workflow_bandwidth:

Alongside Other Processing
===================================

Because the GUI is just another node, it can run in the same workflow as an entirely
separate piece of processing: for example, a behavior-tracking tool like SLEAP watching a
second camera, each with its own display:

..  mermaid::

    flowchart LR
        subgraph workflow["One Bonsai Workflow"]
            direction LR
            A["MiniscopeGui<br/>(IncludeWorkflow)"] --> AW["GUI window"]
            B["Behavior camera<br/>source"] --> C["SLEAP-style<br/>tracking"]
            C --> CW["Tracking window"]
        end

Running two independent capture/encode pipelines side by side has the potential for
USB bandwidth and CPU contention to show up. This is the same effect you'd see running a video call
over a webcam while also acquiring from the Miniscope. To minimize any disruption, put any hardware on separate USB
controllers where possible, and avoid running other encode/decode-heavy software (video
calls, screen recording) during acquisition if you can.

..  TODO(workflow): a workflow combining ``MiniscopeGui`` with a second camera source
..      feeding a behavior-tracking pipeline, demonstrating that both can run and display
..      at once.
..      Suggested file: /_static/downloads/miniscopegui-with-behavior-tracking.bonsai

.. _acquisition_swap:

Swapping the Hardware Node for the GUI
=======================================

Because the GUI's output is the same per-frame Miniscope data stream the raw
``UclaMiniscopeV4`` node produces, the two are interchangeable in a workflow: whatever you
build downstream keeps working whether it's fed by the bare hardware node or the GUI.

..  mermaid::

    flowchart LR
        subgraph baseVariant["Base tier"]
            direction LR
            H["UclaMiniscopeV4"] --> P1["Your custom<br/>processing"]
        end
        subgraph guiVariant["GUI tier"]
            direction LR
            G["MiniscopeGui<br/>(IncludeWorkflow)"] --> P2["Your custom<br/>processing"]
        end

Start with the raw node while you're building and debugging your processing logic, then
drop the GUI in over it once you also want the live display and hardware control —
everything downstream is unaffected.

..  TODO(workflow): two variants of the same downstream processing workflow, one fed by
..      ``UclaMiniscopeV4`` and one fed by ``MiniscopeGui``, to show they're interchangeable.
..      Suggested files: /_static/downloads/uclaminiscopev4-basic-processing.bonsai and
..      /_static/downloads/miniscopegui-basic-processing.bonsai

.. TODO: Multiple GUIs in one workflow, using higher-order operators

.. _acquisition_design:

Before You Start
===================================

These tutorials build on the :ref:`quickstartguide`, which covers connecting the hardware,
installing Bonsai, and installing the ``OpenEphys.Miniscope.Design`` and
``Bonsai.StarterPack`` packages. Each tutorial adds more functionality to the last, so it
is best to follow them in order.

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
