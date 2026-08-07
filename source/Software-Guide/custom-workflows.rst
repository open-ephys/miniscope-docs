.. _custom_workflows:

####################################################################
Custom Bonsai Workflows
####################################################################

.. toctree::
    :hidden:

    commutate
    save-data
    trigger

The :doc:`Miniscope GUI </Software-Guide/index>` covers the great majority of Miniscope
experiments, and it is where you should start. These tutorials are for the cases it does
not cover: when acquisition has to be interleaved with other hardware, when you need
online processing or closed-loop control, or when the recording logic has to differ from
the modes the GUI provides.

These tutorials use the ``OpenEphys.Miniscope`` Bonsai package, which is the same package the GUI
itself is built on, so nothing here replaces the GUI. The two are complementary:

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

***********************
Before You Start
***********************

These tutorials build on the :ref:`quickstartguide`, which covers connecting the hardware,
installing Bonsai, and installing the ``OpenEphys.Miniscope.Design`` and
``Bonsai.StarterPack`` packages. Each tutorial adds more functionality to the last, so it
is best to follow them in order.

***********************
The Tutorials
***********************

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

.. _gui_visualizer_in_workflows:

**************************************
Viewing Your Data with the GUI
**************************************

There are two ways to get the GUI's display while working with your own acquisition logic.

Set Up in the GUI, Then Run Your Workflow
==========================================

The simplest approach, and the one worth reaching for first. Almost everything the GUI's
display is *for* — focusing, setting LED brightness and sensor gain against the saturation
view and histogram, finding cells with :math:`\Delta F/F` and the max projection, and
realigning the field of view against a reference image — happens **before** the experiment
runs, not during it.

So: launch the :doc:`Miniscope GUI </Software-Guide/index>`, get the optics and the
acquisition settings right, export the configuration, then stop acquisition and close the
GUI before running your own workflow with the settings you arrived at. Only one program can
hold the Miniscope DAQ at a time, so the GUI must be stopped before your workflow starts.

Start from the GUI's Own Workflow
==========================================

The Miniscope GUI is itself a Bonsai workflow (``MiniscopeGui.bonsai``), and that workflow
ships inside the ``OpenEphys.MiniscopeV4.Gui`` package as an embedded workflow. You can drop
it straight into a workflow of your own, which gives you the entire GUI as a single node
rather than rebuilding its display around your acquisition logic.

#.  Start Bonsai and open the workflow you want to add the GUI to.

#.  Install the ``OpenEphys.MiniscopeV4.Gui`` package from the Bonsai package manager, if it
    is not already installed.

#.  Find ``MiniscopeGui`` under the package's embedded workflows in the toolbox, and place
    it on the canvas.

#.  Run the workflow. With nothing but this node, you get exactly the functionality
    described in the :doc:`/Software-Guide/index`.

#.  The node's output is the Miniscope data frame, so you can connect it to any custom logic
    you like. Because it is just another node, the GUI can run alongside the rest of your
    workflow: a behavior camera acquired in the same workflow displays at the same time.

..  TODO(media): screenshot — the Bonsai toolbox with the embedded ``MiniscopeGui`` workflow
..      located under the ``OpenEphys.MiniscopeV4.Gui`` package. 
..      Suggested file: /_static/images/miniscopev4_gui/bonsai-toolbox-embedded-workflow.png

..  TODO(media): screenshot — a small example workflow with the ``MiniscopeGui`` node placed
..      and its output branching into custom logic, ideally beside a behavior camera source.
..      This makes the "GUI as one node in a bigger workflow" idea concrete.
..      Suggested file: /_static/images/miniscopev4_gui/bonsai-gui-node-in-workflow.png

.. TODO: Multiple GUIs in one workflow, using higher-order operators
