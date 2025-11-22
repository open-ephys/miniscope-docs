####################
Workflow Description
####################

..  note::  This description assumes the reader has a foundation in Bonsai that is built on the :doc:`Trigger Workflow Description <../save-data/description>`. Start there if you have not already.

***************
GUI Description
***************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-gui.svg
    :alt:   exported svg of main workflow with bounding box over nodes responsible for automatic commutation
    :align: center

This example workflow is meant to be extensible. For that purpose, we have provided an overview of
how it works broad overview of how it works.

..  tip::
    
    If you edit this workflow for your own experiment, one important feature of Bonsai to know about
    is that all items passed from node to node are visible to the user using type visualizers. Either: 

    #.  Double-click a node while the workflow is running to open the default visualizer.
    #.  Right-click a node, click "Show Visualizer", and click a visualizer to show up when the 
        workflow is running.
    
    Not all types have descriptive visualizers, but they can still be helpful to know when data is
    sent. Moreover, if a type doesn't have a descriptive visualizer, you might be able to select a
    member from that type and visualize that member instead, i.e. what we do to visualize image or
    quaternion data from a `UCLAMiniscopeV4Frame`. 

There are several ``GroupWorkflow`` operators that have been named after the GUI elements that they
contain or the function that they serve. Double-click one while the workflow is off to inspect it, or
press ``F12`` while one is selected.

-   The "SaveData" ``GroupWorkflow`` contains a pattern that allows the ``VideoWriter`` operator to
    subscribe (a `Reactive <https://reactivex.io/documentation/observable.html>`__ way to say
    "listening") to upstream operators which allows the user to change the filename while the
    workflow is running. 

-   The "DataSource" ``GroupWorkflow`` contains the ``UCLAMiniscopeV4`` source node.

-   The rest of the ``GroupWorkflows`` are for controlling the state of GUI elements. Each one has a
    ``VisualizerMapping`` to map each GUI element to a panel. 

    -   If you want to add your own custom data-processing pipeline for visualization, inspect the
        "Video" ``GroupWorkflow``. It contains three more ``GroupWorkflows`` that each represent a
        way to look at the data. Create another radio button and branch (or override one that
        already exists) to add your custom data-processing pipeline to the visualizer.

This workflow also demonstrates the usage of ``PublishSubject``, ``MulticastSubject``, and
``BehaviorSubject`` which can be combined with ``SubscribeSubject`` to connect nodes without drawing
lines between them. Using `subjects <https://bonsai-rx.org/docs/articles/subjects.html>`_ is `good
practice <https://bonsai-rx.org/docs/articles/workflow-guidelines.html>`_ when creating more
extensive workflows. 