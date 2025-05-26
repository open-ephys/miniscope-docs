####################
Workflow Description
####################

..  note::  This description assumes the reader has a foundation in Bonsai that is built on the :doc:`Trigger Workflow Description <../save-data/description>`. Start there if you have not already.

**************************
GUI Description
**************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-gui.svg
    :alt:   exported svg of main workflow with bounding box over nodes responsible for automatic commutation
    :align: center

This workflow is quite extensive and therefore instead of node-by-node instructive description, it
gets an overview of how it works. There are several ``GroupWorkflow`` operators that have been named
after the GUI elements that they contain or the function they serve. 

-   The "SaveData" ``GroupWorkflow`` contains a pattern that allows the ``VideoWriter`` operator to
    subscribe (a `Reactive <https://reactivex.io/documentation/observable.html>`__ way to say
    "listening") to upstream operators which allows the user to change the filename while the
    workflow is running. 

-   The "DataSource" ``GroupWorkflow`` contains the ``UCLAMiniscopeV4`` source node.

-   The rest of the ``GroupWorkflows`` are for controlling the state of GUI elements. Each one has a
    ``VisualizerMapping`` to map each GUI element to a panel. In particular:

    -   If you want to add your own custom data-processing pipeline for visualization, inspect the
        "Video" ``GroupWorkflow``. It contains three more ``GroupWorkflows`` that each represent a
        way to look at the data. Create another radio button and branch (or override one that
        already exists) to add your custom data-processing pipeline to the visualizer.

-   This workflow also demonstrates the usage of ``PublishSubject``, ``MulticastSubject``, and
    ``SubscribeSubject``. These are all various ways to makes connections between nodes without
    connecting them directly 

..  note:: To learn more about a respective node, refer to the description in the *Properties* pane that appears after left-clicking the respective node. If the node has a name that is different from the name of the operator it represents, the operator name is presented in parenthesis after the node name.
