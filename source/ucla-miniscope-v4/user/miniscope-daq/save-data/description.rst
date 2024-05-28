####################
Workflow Description
####################

Please refer to the `Bonsai Language Guide <https://bonsai-rx.org/docs/articles/observables.html>`__ to develop a foundation in Bonsai before proceeding. 

******************************
Produce UCLA Miniscope v4 Data
******************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-savedata_miniscope-node.svg
    :alt:   screenshot of uclaminiscopev4 node boxed
    :align: center

*   The ``UCLAMiniscopeV4`` node represents a ``UCLAMiniscopeV4`` operator. The ``UCLAMiniscopeV4`` operator is a *source* operator as indicated by its node's green color and the orientation of its grey arc. Source operators produce data. 

*   The ``UCLAMiniscopeV4`` operator's output (``Bonsai.Miniscope.V4Frame``) has four members. They can be accessed by right-clicking the ``UCLAMiniscopeV4`` node and hovering the cursor over the *Output* option in the pop-up menu. Left-clicking on one of these members automatically places a new ``MemberSelector`` nodes. These nodes can also be placed by searching modules in the search bar in the *Toolbox* pane or the using the ``Ctrl+E`` hotkey. 

*   The ``MemberSelector`` operators are *transform* operators as indicated by the nodes' blue color and lack of grey bar. Transform operators transform data. The ``MemberSelector`` operator transforms data by selecting one or multiple members of its input to output.  

*   In this workflow, ``Quarternion``, ``FrameNumber``, and ``Image`` members are selected from ``Bonsai.Miniscope.V4Frame`` to be passed to two divergent branches.

***************
Save Image Data
***************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-savedata_image-data.svg
    :alt:   screenshot of uclaminiscopev4 node boxed
    :align: center

*   The ``Image`` node connects to a ``VideoWriter`` node. The ``VideoWriter`` operator writes data to a video file according to settings in the *Properties* pane that appears after left-clicking the ``VideoWriter`` node. 

*   The ``VideoWriter`` operator is a *sink* operator as indicated by the node's purple color and the orientation of its grey arc. A sink operator saves data or triggers external events. 

*********************************
Save Timestamped Quarternion Data
*********************************

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-savedata_quart-data.svg
    :alt:   screenshot of uclaminiscopev4 node boxed
    :align: center

*   The ``FrameNumber, Quarternion`` node connects to the ``Timestamp`` node. The ``Timestamp`` operator appends timestamps to items that are emitted by the upstream operator.

*   The ``Timestamp`` node connects to the  ``CsvWriter`` node. The ``CsvWriter`` operator writes data to a csv file according to settings in the *Properties* pane that appears after left-clicking the ``CsvWriter`` node. 

To continue learning using the UCLA Miniscope v4 and Miniscope-DAQ in Bonsai, refer to the :doc:`Trigger Workflow Description </ucla-miniscope-v4/user/miniscope-daq/trigger/description>`
