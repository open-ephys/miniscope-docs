#################
Commutate
#################

..  note::  This tutorial builds on the :ref:`quick-start-guide`.

After following this tutorial, the user will be able to automatically rotate the coaxial tether when the UCLA Miniscope v4 rotates.

..  raw:: html

    {% with static_path = '../../_static', name = 'uclaminiscopev4-miniscopedaq-commutate' %}
        {% include 'workflow.html' %}
    {% endwith %}

The ``Quaternion`` node connects to the ``AutoCommutator`` node. The ``AutoCommutator`` node represents a ``IncludeWorkflow`` operator named *AutoCommutator*. An ``IncludeWorkflow`` operator includes a workflow from another file into a parent workflow. To inspect the included workflow, press F12 while the ``AutoCommutator`` node is selected. This workflow comes from the OpenEphys.Commutator Bonsai package. 

***********************
Configure the Hardware
***********************

*Additional required components: Open Ephys torque-free coaxial commutator, coaxial cable (SMA ↔ SMA), commutator USB connection cable*

Instead of connecting the Miniscope to Miniscope DAQ as in the :ref:`quick-start-guide`, follow the `Coax Commutator Connections section <https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html?commutator=coax#connecting>`__ of the commutator hardware docs to:

-   connect the commutator's stator/s (top SMA connector) to the Miniscope DAQ using the SMA-SMA cable.

-   connect the commutator's rotor/s (bottom SMA connector) to the Miniscope using the coaxial tether.
    
-   connect the commutator to the PC using the USB cable.  

Make sure you follow the sections in the commutator docs on how to `mount the commutator <https://open-ephys.github.io/commutator-docs/user-guide/mount-connect.html>`__ and `manage the tether <https://open-ephys.github.io/commutator-docs/user-guide/tether-management_counterweight.html>`__ .

**********************
Get Started in Bonsai
**********************

In addition to the setup steps outlined in the :ref:`quick-start-guide`, install the following package:

* *OpenEphys.Commutator*: controls Open Ephys commutators.

***********************
Operate the Workflow
***********************

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``AutoCommutator`` node and set the ``PortName`` property under the `Properties` pane to match the port that corresponds to your commutator. 

    ..  note::  
        
        If you are uncertain about which COM port corresponds to your commutator, follow these instructions:

        #.  Click on ``AutoCommutator`` node and look at the options available in the drop-down for ``PortName`` property.

        #.  Unplug the commutator, and plug it back in. Observe which COM port disappears and appears in drop-down list when doing so - that is the COM port associated with your commutator.

#.  Run the workflow and verify that the commutator turns when the miniscope rotates.