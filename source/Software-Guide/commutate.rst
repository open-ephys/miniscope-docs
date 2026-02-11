####################################################################
Automate tether commutation using 3D orientation data
####################################################################

..  note::  This tutorial builds on the :ref:`quickstartguide`.

After following this tutorial, the user will be able to automatically rotate the coaxial tether when the UCLA Miniscope v4 rotates, as well as control the commutator turns manually using keyboard keypresses.

.. raw:: html

  <center><video width="560" height="340" controls>
  <source src="../_static/videos/Miniscope_Coax commutator.mp4" type="video/mp4">
  </video></center>

..  raw:: html

    {% with static_path = '../_static', name = 'uclaminiscopev4-miniscopedaq-commutate' %}
        {% include 'workflow.html' %}
    {% endwith %}

***********************
Workflow Description
***********************

The ``Quaternion`` node connects to the ``Commutator`` node, which represents a ``GroupWorkflow`` named *Commutator*. A ``GroupWorkflow`` operator has a workflow nested inside, and its configurable properties can be exposed. To inspect the grouped workflow, double-click the ``Commutator`` node. You will see nodes from the OpenEphys.Commutator Bonsai package that transform quaternion measurements into twists, as well as nodes to capture keyboard keypresses to drive the commutator automatically or manually, respectively.

***********************
Configure the Hardware
***********************

*Additional required components: Open Ephys torque-free coaxial commutator, coaxial cable (SMA ↔ SMA), commutator USB connection cable*

Instead of connecting the Miniscope to Miniscope DAQ as in the :ref:`quickstartguide`, follow the `Coax Commutator Connections section <https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html?commutator=coax#connecting>`__ of the commutator hardware docs to:

-   connect the commutator's stator/s (top SMA connector) to the Miniscope DAQ using the SMA-SMA cable.

-   connect the commutator's rotor/s (bottom SMA connector) to the Miniscope using the coaxial tether.
    
-   connect the commutator to the PC using the USB cable.  

Make sure you follow the sections in the commutator docs on how to `mount the commutator <https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html>`__ and `manage the tether <https://open-ephys.github.io/commutator-docs/user-guide/tether-management_counterweight.html>`__ .

**********************
Get Started in Bonsai
**********************

In addition to the setup steps outlined in the :ref:`quickstartguide`, install the following package:

* *OpenEphys.Commutator*: controls Open Ephys commutators.

***********************
Operate the Workflow
***********************

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``AutoCommutator`` node and set the ``PortName`` property under the `Properties` pane to match the port that corresponds to your commutator. Set the ``LeftTurnKey`` and ``RightTurnKey`` properties to the keyboard keys that you would like to use to manually control the commutator.

    ..  note::  
        
        If you are uncertain about which COM port corresponds to your commutator, follow these instructions:

        #.  Click on ``AutoCommutator`` node and look at the options available in the ``PortName`` property drop-down menu.

        #.  Unplug the commutator, and plug it back in. Observe which COM port disappears and appears in drop-down list when doing so - that is the COM port associated with your commutator.

#.  Run the workflow and verify that the commutator turns when the miniscope rotates, and when the defined keys are pressed (left and right arrow keys in the example).