####################################################################
Automate tether commutation using 3D orientation data
####################################################################

..  note::

    This tutorial builds on the :ref:`quickstartguide` and is part of the
    :doc:`custom Bonsai workflows </Software-Guide/custom-workflows>` series.

    **You do not need this workflow to use a commutator.** The :doc:`Open Ephys Miniscope
    V4 GUI </Software-Guide/openephys-gui>` connects to and drives an Open Ephys commutator from its
    Control Panel, with no workflow to build: see the
    :doc:`GUI reference </Software-Guide/gui-reference>`. Follow this tutorial when you
    want to understand how commutation works, or when you need to modify it.

After following this tutorial, the user will be able to automatically rotate the coaxial
tether when the UCLA Miniscope v4 rotates, as well as control the commutator turns manually
using keyboard keypresses.

.. raw:: html

  <center><video width="560" height="340" controls>
  <source src="../_static/videos/Miniscope_Coax commutator.mp4" type="video/mp4">
  </video></center>

..  raw:: html

    {% with static_path = '../_static', name = 'uclaminiscopev4-miniscopedaq-commutate' %}
        {% include 'workflow.html' %}
    {% endwith %}

.. hint::

    The ``MiniscopeGui`` workflow is a drop-in replacement for the ``UclaMiniscopeV4`` node in
    this workflow: swap it in to gain the GUI's visualizations, with no changes to anything
    downstream. See :ref:`acquisition_swap`.

***********************
Workflow Description
***********************

The ``Quaternion`` node connects to the ``Commutator`` node, which represents a ``GroupWorkflow``
named *Commutator*. A ``GroupWorkflow`` operator has a workflow nested inside, and its configurable
properties can be exposed. To inspect the grouped workflow, double-click the ``Commutator`` node.
You will see nodes from the OpenEphys.Commutator Bonsai package that transform quaternion
measurements into twists, as well as nodes to capture keyboard keypresses to drive the commutator
automatically or manually, respectively.

The quaternion stream feeding the commutator here is the same one the
:doc:`Miniscope GUI </Software-Guide/openephys-gui>` plots in its *Quaternion* signal tab, and the
same one it uses to drive the commutator.

***********************
Configure the Hardware
***********************

*Additional required components: Open Ephys torque-free coaxial commutator, coaxial cable (SMA ↔ SMA), commutator USB connection cable*

Instead of connecting the Miniscope to Miniscope DAQ as in the :ref:`quickstartguide`, follow the
`Coax Commutator Connections section
<https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html?commutator=coax#connecting>`__
of the commutator hardware docs to:

-   connect the commutator's stator (top SMA connector/s) to the Miniscope DAQ using the SMA-SMA cable.

-   connect the commutator's rotor (bottom SMA connector) to the Miniscope using the coaxial tether.

-   connect the commutator to the PC using the USB cable.

Make sure you follow the sections in the commutator docs on how to `mount the commutator
<https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html>`__ and `manage the
tether
<https://open-ephys.github.io/commutator-docs/user-guide/tether-management_counterweight.html>`__.

**********************
Get Started in Bonsai
**********************

In addition to the setup steps outlined in the :ref:`quickstartguide`, install the following package:

* *OpenEphys.Commutator*: controls Open Ephys commutators.

***********************
Operate the Workflow
***********************

#.  Set the ``UclaMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``Commutator`` node and set the ``PortName`` property under the `Properties`
        pane to match the port that corresponds to your commutator. Set the ``LeftTurnKey`` and
        ``RightTurnKey`` properties to the keyboard keys that you would like to use to manually
        control the commutator.

    ..  note::

        If you are uncertain about which COM port corresponds to your commutator, follow these instructions:

        #.  Click on ``Commutator`` node and look at the options available in the ``PortName`` property drop-down menu.

        #.  Unplug the commutator, observe any changes in the list, and plug it back in. The COM
            port that disappears and appears in drop-down list when doing so is the COM port
            associated with your commutator.

    ..  tip::

        The :doc:`Miniscope GUI </Software-Guide/openephys-gui>` identifies commutator ports for you: its
        **Refresh** button probes every serial port and lists only those that answer as a
        commutator. If you are unsure which port to use here, open the GUI once and read
        the port out of its Commutator section. If there are multiple commutators connected,
        disconnect one at a time to determine which one is which.

#.  Run the workflow and verify that the commutator turns when the miniscope rotates, and when the
    defined keys are pressed (left and right arrow keys in the example).

.. _commutate_viewing_data:

***********************
Viewing the Data
***********************

Double-clicking the ``Quaternion`` node opens Bonsai's built-in quaternion visualizer,
which is enough to confirm the IMU is reporting. For anything more, use the
:doc:`Miniscope GUI </Software-Guide/openephys-gui>`, which shows the orientation as Euler angles
alongside the quaternion, plots the digital inputs on the same time axis, and lets you
freeze the display to inspect a rotation after the fact.

Since only one program can hold the Miniscope DAQ at a time, close the GUI before running
this workflow. Alternatively, place the GUI's embedded workflow directly into this one to
get its display without giving anything up; see :ref:`gui_visualizer_in_workflows`.

***********************
Next Steps
***********************

*   :doc:`/Software-Guide/save-data` adds writing the image and orientation data to file.

*   :doc:`Recording with the GUI </Software-Guide/recording>` describes what the GUI writes
    for you, in case that is all you need.
