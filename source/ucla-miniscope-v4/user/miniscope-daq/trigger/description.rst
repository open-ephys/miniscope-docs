###################
Workflow Descrption
###################

..  note::  This description assumes a foundation in Bonsai that is built on the :doc:`Save Data Workflow Description <../save-data/description>`. Start there if you have not already. 

******************
Trigger Image Data
******************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger_trigger-image.svg
    :alt:   exported svg of workflow with bounding box over trigger and image nodes
    :align: center

*   The ``UclaMiniscopeV4`` node connects to the ``Trigger`` node. The ``Trigger`` node represents a ``Condition`` operator named *Trigger*. A ``Condition`` operator emits the item it receives under specific conditions. To inspect the its conditional statement, double left-click the ``Trigger`` node. The ``Trigger`` node connects to the ``Image`` node. ``Trigger`` only emits items if its conditional statement (described in the next section) is ``TRUE``. 

*************
Trigger Logic
*************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-trigger_trigger-condition.svg
    :alt:   exported svg of subworkflow with bounding box over entire thing
    :align: center

*   ``Trigger`` emits ``UCLAMiniscopeV4Frame`` if the ``Trigger`` member of ``UCLAMiniscopeV4Frame`` is ``True``. 

To continue learning using the UCLA Miniscope v4 and Miniscope-DAQ in Bonsai, refer to the :doc:`Commutate Workflow Explainer </ucla-miniscope-v4/user/miniscope-daq/commutate/description>`
