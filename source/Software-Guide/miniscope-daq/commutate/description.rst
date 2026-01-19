####################
Workflow Description
####################

..  note::  This description assumes the reader has a foundation in Bonsai that is built on the :doc:`Trigger Workflow Description <../save-data/description>`. Start there if you have not already.

**************************
Commutator IncludeWorkflow
**************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_quat-commutator.svg
    :alt:   exported svg of main workflow with bounding box over nodes responsible for automatic commutation
    :align: center

*   The ``Quaternion`` node connects to the ``AutoCommutator`` node. The ``AutoCommutator`` node represents a ``IncludeWorkflow`` operator named *AutoCommutator*. An ``IncludeWorkflow`` operator includes a workflow from another file into a parent workflow. To inspect the included workflow, press F12 while the ``AutoCommutator`` node is selected. This workflow comes from the OpenEphys.Commutator Bonsai package. 
