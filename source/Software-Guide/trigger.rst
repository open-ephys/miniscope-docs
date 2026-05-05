##########################################################
Trigger data recording with a hardware digital signal 
##########################################################

..  note::  This tutorial builds on the :ref:`quickstartguide` and previous tutorials.

The Miniscope DAQ Input Trigger port receives 3.3V or 5V level digital inputs. That signal can be used to gate recording to file.
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

**Miniscope Data Publishing**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger-data-publishing.svg
    :alt:   exported svg of workflow first branch
    :align: center

*   The ``UclaMiniscopeV4`` node output is connected to a ``BehaviorSubject`` named ``MiniscopeDataFrame`` which publishes the stream so it can be reused in multiple parts of the workflow. This branch is used to visualize the ``Image`` and ``Quaternion`` members and to provide orientation data to the ``Commutator`` group workflow.

**Trigger Logic**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger-trigger-logic.svg
    :alt:   exported svg of workflow second branch
    :align: center

*   On a second branch, the same ``MiniscopeDataFrame`` is saved to file based on the state of the ``Trigger`` member, which corresponds to the hardware input. A ``Condition`` node named ``TriggerAsserted`` monitors the ``Trigger`` member to detect a rising edge (LOW → HIGH transition). The condition fires once per trigger onset as per the logic in the subworkflow:

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger-trigger-asserted.svg
    :alt:   exported svg of TriggerAsserted node
    :align: center

*   When a rising edge is detected in the external trigger, a ``SelectMany`` operator named ``ChunkData`` subscribes to the ``MiniscopeDataFrame`` data stream to begin recording. The ``TakeWhile`` operator ensures that frames are passed downstream only while the trigger line remains HIGH. When the trigger goes LOW, the recording chunk ends:

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger-chunk-data.svg
    :alt:   exported svg of ChunkData node
    :align: center

*   This mechanism creates one recording session per hardware trigger pulse. After each pulse, the workflow resets using the ``Repeat`` operator so it is ready for the next trigger event. Within each trigger-defined recording session, the Image, FrameNumber and Quaternion data are written to file as explained in previous tutorials: only one video and one csv file are generated per trigger pulse.

***********************
Configure the Hardware
***********************

*Additional required components: external hardware with 0-5V digital output, SMA-ended cable*

Configure the hardware as in the :ref:`quickstartguide` or as in the :doc:`commutate` tutorial if you are using an Open Ephys Commutator.

Additionally, connect a 0-3.3V or 0-5V trigger source to the Trigger In port using the SMA cable or a suitable adapter such as a BNC-SMA adapter.

**********************
Get Started in Bonsai
**********************

No additional packages besides the ones listed in the :ref:`quickstartguide` and previous tutorials are required. 

***********************
Operate the Workflow
***********************

#. Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#. If using a commutator, set the COM port associated with your commutator in the workflow. If not using a commutator, delete the nodes corresponding to the commutation.

#. Set the ``UCLAMiniscopeV4`` operator's ``LEDRespectsTrigger`` property to True if you intend to use the LED only during the triggered recording. This can help reduce photobleaching during long experimental sessions with multiple triggered recordings, but means the LED will be off during acquisition periods that are not being recorded to file. To be able to monitor the brain activity during acquisition, toggle this property to False.

#. Run the workflow and verify that images are emitted only when the Trigger is set to HIGH, and that the LED behaves accordingly. 