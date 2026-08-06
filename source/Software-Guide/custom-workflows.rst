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

The Miniscope GUI is itself a Bonsai workflow (``MiniscopeGui.bonsai``) and the installer
lays down a complete Bonsai environment, editor included, alongside it. That means you can
open the GUI in the editor and extend it, rather than rebuilding its display around your
own workflow.

#.  Run ``Bonsai.exe`` from your local environment.

#.  Ensure that the ``OpenEphys.Miniscope`` package is installed through the package manager.

#.  Place the ``MiniscopeGui.bonsai`` from the embedded workflows found in the toolbox.

#.  Running the workflow at this point, with just the ``MiniscopeGui.bonsai`` workflow, will give
    the exact same functionality as the MiniscopeV4 GUI described in the
    :doc:`/Software-Guide/index`.
    
#.  The output of the included workflow is the MiniscopeV4 data frame; this can be connected to any
    custom logic, and viewed at the same time as a behavioral camera that is acquired by the workflow.
