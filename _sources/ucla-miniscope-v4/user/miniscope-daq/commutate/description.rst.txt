####################
Workflow Description
####################

..  note::  This description assumes the reader has a foundation in Bonsai that is built on the :doc:`Trigger Workflow Description <../save-data/description>`. Start there if you have not already.

**************************
Commutator IncludeWorkflow
**************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_quart-commutator.svg
    :alt:   exported svg of main workflow with bounding box over nodes responsible for automatic commutation
    :align: center

*   The ``Quaternion`` node connects to the ``AutoCommutator`` node. The ``AutoCommutator`` node represents a ``IncludeWorkflow`` operator named *AutoCommutator*. An ``IncludeWorkflow`` operator includes a workflow from another file into a parent workflow. To inspect the included workflow, press F12 while the ``AutoCommutator`` node is selected. This workflow comes from the OpenEphys.Commutator Bonsai package. 

*   A node's border represents the scope of the corresponding operator. For instance, the dashed grey line around the ``AutoCommutator`` node indicates it shares a scope with the "main" workflow. In contrast, a solid line would indicates it defines its own scope. For more information, refer to the `Bonsai documentation on this subject <https://bonsai-rx.org/docs/articles/subjects.html#scope-of-subjects>`__.

..  note:: To learn more about a respective node, refer to the description in the *Properties* pane that appears after left-clicking the respective node. If the node has a name that is different from the name of the operator it represents, the operator name is presented in parenthesis after the node name.
