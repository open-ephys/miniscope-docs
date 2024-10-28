#################
Workflow Tutorial
#################

..  note:: An Open Ephys Coaxial Commutator is necessary for this workflow 

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../../../_static', name = 'uclaminiscopev4-miniscopedaq-commutate' %}
            {% include 'workflow.html' %}
        {% endwith %}

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

    ..  grid::
        
        ..  grid-item::
            :columns:   3

            ..  image:: /_static/images/uclaminiscopev4-properties.webp
                :align: center
                :alt:   screenshot of ucla miniscope v4 node properties for index

        ..  grid-item::
            
            ..  include::  /includes/set-index.rst

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``AutoCommutator`` node and set the ``PortName`` property under the `Properties` pane to match the port that corresponds to your commutator. 

    *   Confirm the RotationAxis is search

#.  Set the commutator to rotate around the correct axis

    *   Left-click the ``AutoCommutator`` node and set the ``RotationAxis`` property under the `Properties` pane to "0, 0, 1". 

    ..  note::  
        
        If you are uncertain about which COM port corresponds to your commutator, follow these instructions:

        #.  Open Window's *Device Manager*.

        #.  Unplug the commutator, and plug it back in. Observe which COM port disappears and appears in device manager when doing so - that is the COM port associated with your commutator. If the commutator does not appear in device manager, follow `these instructions <https://www.pjrc.com/teensy/troubleshoot.html>`__

..  [1]
    .. include::    /includes/start-workflow.rst