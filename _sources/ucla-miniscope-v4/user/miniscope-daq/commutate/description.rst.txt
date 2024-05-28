####################
Workflow Description
####################

..  note::  This description assumes the reader has a foundation in Bonsai that is built on the :doc:`Trigger Workflow Description <../save-data/description>`. Start there if you have not already.

************************
Commutator GroupWorkflow
************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_quart-commutator.svg
    :alt:   exported svg of main workflow with bounding box over nodes responsible for manual commutation
    :align: center

*   The ``Quarternion`` node connects to the ``Commutator`` node. The ``Commutator`` node represents a ``GroupWorkflow`` operator named *Commutator*. A ``GroupWorkflow`` operator encapsulates a workflow fragment inside a single node. To inspect the encapsulated workflow fragment, double left-click the ``Commutator`` node.

*   A node's border represents the scope of the corresponding operator. For instance, the dashed grey line around the ``Commutator`` node indicates it shares a scope with the "main" workflow. In contrast, a solid line would indicates it defines its own scope. For more information, refer to the `Bonsai documentation on this subject <https://bonsai-rx.org/docs/articles/subjects.html#scope-of-subjects>`__.

..  note:: To learn more about a respective node, refer to the desciption in the *Properties* pane that appears after left-clicking the respective node. If the node has a name that is different from the name of the operator it represents, the operator name is presented in parenthesis after the node name.

***********************
Sample Quarternion Data
***********************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_source1-sample-timer.svg
    :alt:   exported svg of sub workflow with bounding box over nodes responsible for sampling quarternion data
    :align: center

*   The ``Source1`` node represents a ``WorkflowInput`` operator. A ``WorkflowInput`` operator is a source operator that emits items passed to the ``GroupWorkflow`` from the parent workflow. In this case, ``Source1`` emits quarternion data that is what is passed to the input of ``Commutator``.

*   The ``Source1`` and ``Timer`` nodes connect to the ``Sample`` node. The ``Sample`` node emits the most recent upstream data at an interval specified by setting the ``Period`` value that appears in the *Properties* pane after left-clicking the ``Timer`` node (in this case, 100ms). 

*************************************
Generate Automated Commutator Command
*************************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_auto.svg
    :alt:   exported svg of sub workflow with bounding box over nodes responsible for automated commutation
    :align: center

*   The ``Sample`` node connects to the ``Heading`` node. The ``Heading`` node represents a ``PythonTransform`` operator named ``Heading``. A ``PythonTransform`` operator contains a Python script for transforming items in an observable sequence. The script contained in ``Heading`` transforms quarternion data to a single quantity that represents direction the UCLA Miniscope v4 is heading. To inspect the script that performs this computation, double left-click the ``Heading`` node.

*   The ``Heading`` node connects to ``Zip`` and ``Skip`` nodes. The ``Skip`` node also connects to the the ``Zip`` node. The ``Skip`` operator skips a number of items in the observable sequence or upstream data as specified by the ``Count`` value that appears in the *Properties* pane after left-clicking the ``Skip`` node (in this case, 1). The ``Zip`` operator emits a combination of two inputs. In this case, the ``Zip`` operator emits the most recently sampled heading data and the sample before that. In other words, if the ``Heading`` emits the :math:`nth` item in an observable sequence, ``Zip`` emits items :math:`(n, n-1)`.

*   The ``Zip`` node connects to the ``AutomatedCommutatorCommand`` node. The ``AutomatedCommutatorCommand`` node represents a ``PythonTransform`` operator named *AutomatedCommutatorCommand*. The script contained in ``AutomatedCommutatorCommand`` transforms current and previous heading data to a commutator command. To inspect the script that performs this computation, double left-click the ``AutomatedCommutatorCommand`` node. 

**********************************
Generate Manual Commutator Command
**********************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_manual.svg
    :alt:   exported svg of sub workflow with bounding box over nodes responsible for manual commutation
    :align: center

*   The ``KeyDown`` node represents a ``KeyDown`` operator. A ``KeyDown`` operator emits an item anytime a key/key combination specified by the ``Filter`` value that appears after left-clicking the ``KeyDown`` node (in this case, ``Alt+Right`` and ``Alt+Left``) is pressed.

*   The ``KeyDown`` nodes each connect to the ``String`` node. 

*   The ``String`` node represents a ``String`` operator. A ``String`` operator emits a string specified by the ``Value`` value that appears after left-clicking the ``String`` node (in this case, ``"{turn : 0.1}"`` and ``"{turn : -0.1}"``) anytime it receives an item from upstream item.

***********************************  
Send Commutator Command Over Serial
***********************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-commutate_command.svg
    :alt:   exported svg of workflow with bounding box over nodes responsible for sending serial command to commutator
    :align: center

*   The two ``String`` nodes and ``AutomatedCommutatorCommand`` each connect to the ``Merge`` node. The ``Merge`` node represents a ``Merge`` operator A ``Merge`` operator merges multiple observable sequences into one.

*   The ``Merge`` node connects to a ``SerialWriteLine`` node. The ``SerialWriteLine`` node represents a ``SerialWriteLine`` operator. A ``SerialWriteLine`` operator writes serial messages appended with specified by the ``NewLine`` value that appears afer left-clicking the ``SerialWriteLine`` node.

..  note::  Because ``SerialWriteLine`` operator is a sink operator, it doesn't transform data. In other words, its output is equivalent its input, and the ``SerialWriteLine`` operator passes that data to the ``WorkflowOutput`` as-is to the downstream operator.

*   The ``SerialWriteLine`` node connects to a ``WorkOutput`` node. The ``WorkOutput`` node represents a ``WorkOutput`` operator. Items passed to the ``WorkOutput`` operator are emitted by the corresponding group workflow's node (in our case, ``Commutator`` in the main workflow). This can be seen by double-clicking the ``Commutator`` node while the workflow is running. 
