.. ***********************************************
.. Connecting to the Hardware
.. ***********************************************

.. The ``OpenEphys.Miniscope`` package's acquisition operators (e.g.,
.. ``UclaMiniscopeV4``) are the foundation everything else on this page is built
.. on. Double-clicking one of Bonsai's default visualizers on the operator's output
.. is enough to confirm data is flowing, but each member of the data stream opens
.. in its own window, with no shared time axis. See :ref:`acquisition_swap` below
.. for what the same acquisition looks like with the GUI's display dropped in
.. instead, with the rest of the workflow unchanged.

.. _acquisition_gui:

***********************************************
Using the GUI in Bonsai
***********************************************

.. _gui_visualizer_in_workflows:

Embed the GUI as a Single Node
===================================

The GUI is itself a Bonsai workflow (``MiniscopeV4Gui.bonsai``), and it ships
inside the ``OpenEphys.Miniscope.Gui`` package as an embedded workflow. Drop it
straight into a workflow of your own and you get the entire GUI as a single
node, with exactly the same functionality as launching it as a standalone
application; see :ref:`headless_vs_custom_workflow` for why.

#.  Start Bonsai and open the workflow you want to add the GUI to.

#.  Install the ``OpenEphys.Miniscope.Gui`` package, if it is not already installed (see
    :ref:`bonsai_installation`)

#.  Find ``MiniscopeV4Gui`` under the package's embedded workflows in the toolbox, and place
    it on the canvas.

    ..  image:: /_static/images/miniscopev4_gui/bonsai-toolbox-embedded-workflow.png
        :alt:   the Bonsai toolbox with the embedded MiniscopeV4Gui workflow located under the OpenEphys.MiniscopeV4.Gui package
        :align: center
        :width: 60%

#.  Run the workflow. With nothing but this node, you get exactly the functionality
    described in :doc:`/Software-Guide/installing-and-using-the-gui`.

#.  The node's output is the Miniscope data frame, so you can connect it to any custom logic you
    like. Because it is just another node, the GUI can run alongside the rest of your workflow: a
    behavior camera acquired in the same workflow displays at the same time in a different window.

    ..  image:: /_static/downloads/bonsai-gui-node-in-workflow.svg
        :alt:   the MiniscopeV4Gui workflow placed next to a CameraCapture node
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
by the ``MiniscopeV4Gui`` workflow:

..  image:: /_static/downloads/miniscope-gui-swapped-in-for-hardware-node-commutator.svg
    :alt:   the MiniscopeV4Gui workflow replacing the UclaMiniscopeV4 node in the trigger workflow
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

..  TODO(workflow): a workflow combining ``MiniscopeV4Gui`` with a second camera source
..      feeding a behavior-tracking pipeline, demonstrating that both can run and display
..      at once.
..      Suggested file: /_static/downloads/miniscopegui-with-behavior-tracking.bonsai

Running Multiple GUIs Simultaneously
=======================================

If you have multiple Miniscopes connected to one computer and want to visualize all of them from
one workflow, wrap the included workflow inside higher-order operators and run them side by side.
In the following workflow, each ``SelectMany`` contains a ``MiniscopeV4Gui.bonsai`` embedded
workflow and nothing else.

..  image:: /_static/downloads/two-miniscope-guis-running-simultaneously.svg
    :alt:   two MiniscopeV4Gui workflows running simultaneously, one inside each SelectMany operator
    :align: center
    :width: 20%
