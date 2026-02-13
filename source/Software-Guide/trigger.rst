##########################################################
Trigger data recording with a hardware digital signal 
##########################################################

..  note::  This tutorial builds on the :ref:`quickstartguide` and previous tutorials.

The Miniscope DAQ Input Trigger port receives 3.3 or 5V level digital inputs. That signal can be used to gate recording to file.
After following this tutorial, the user will be able to record both image and orientation data to file following a hardware trigger signal. In this workflow, recording to file is initiated at the each rising edge and terminated at each falling edge, as depicted below. The LED on/off state can optionally follow the trigger.

..  image:: /_static/images/Trigger_tutorial_diagram.png
    :alt:   diagram explaining how the trigger gates acquired frames
    :align: center
    :width: 500px

..  raw:: html

    {% with static_path = '../_static', name = 'uclaminiscopev4-miniscopedaq-trigger' %}
        {% include 'workflow.html' %}
    {% endwith %}

***********************
Workflow Description
***********************

**Trigger Image Data**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger_trigger-image.svg
    :alt:   exported svg of workflow with bounding box over trigger and image nodes
    :align: center

*   The ``UclaMiniscopeV4`` node connects to the ``Trigger`` node. The ``Trigger`` node represents a ``Condition`` operator named *Trigger*. A ``Condition`` operator emits the item it receives under specific conditions. To inspect the its conditional statement, double left-click the ``Trigger`` node. The ``Trigger`` node connects to the ``Image`` node. ``Trigger`` only emits items if its conditional statement (described in the next section) is ``TRUE``.


**Trigger Logic**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger_trigger-condition.svg
    :alt:   exported svg of subworkflow with bounding box over entire thing
    :align: center

*   ``Trigger`` emits ``UCLAMiniscopeV4Frame`` if the ``Trigger`` member of ``UCLAMiniscopeV4Frame`` is ``True``.


***********************
Configure the Hardware
***********************

*Additional required components: external hardware with 0-5V digital output, SMA-ended cable*

Configure the hardware as in the :ref:`quickstartguide` or as in the :doc:`commutate` tutorial if you are using an Open Ephys Commutator.

Additionally, connect a 0-5V trigger source to the Trigger In port using the SMA cable or a suitable adapter such as a BNC-SMA adapter.

**********************
Get Started in Bonsai
**********************

No additional packages besides the ones listed in the :ref:`quickstartguide` and previous tutorials are required. 

***********************
Operate the Workflow
***********************

#. Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#. If using a commutator, set the COM port associated with your commutator in the workflow. If not using a commutator, delete the nodes corresponding to the commutation.

#. Set the ``UCLAMiniscopeV4`` operator's ``LEDRespectsTrigger`` property to True if you intend to use the LED only during recording.

#. Run the workflow and verify that images are emitted only when the Trigger is set to HIGH, and that the LED behaves accordingly. 