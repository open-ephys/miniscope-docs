#################
Workflow Tutorial
#################

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../../../_static', name = 'uclaminiscopev4-miniscopedaq-gui' %}
            {% include 'workflow.html' %}
        {% endwith %}

#.  Double-click the ``DataSource`` node and set the ``UCLAMiniscopeV4`` operator's ``Index``
    property to the value that corresponds to the index of your miniscope.

    ..  grid::

        ..  grid-item::
            
            ..  include::  /includes/set-index.rst

        ..  grid-item::
            :columns:   3

            ..  image:: /_static/images/uclaminiscopev4-properties.webp
                :align: center
                :alt:   screenshot of ucla miniscope v4 node properties for index

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``AutoCommutator`` node and set the ``PortName`` property under the
        `Properties` pane to match the port that corresponds to your commutator. 

    ..  note::  
        
        If you are uncertain about which COM port corresponds to your commutator, follow these instructions:

        #.  Open Window's *Device Manager*.

        #.  Unplug the commutator, and plug it back in. Observe which COM port disappears and
            appears in device manager when doing so - that is the COM port associated with your
            commutator. If the commutator does not appear in device manager, follow `these
            instructions <https://www.pjrc.com/teensy/troubleshoot.html>`_

#.  If you do not have a commutator connected, select the following chain of nodes and disable them
    by either pressing ``Ctrl+D`` or right-clicking the selected nodes and clicking the "Disable"
    option in the context menu that pops up.

    ..  figure:: /_static/images/uclaminiscopev4-miniscopedaq-gui_commutate-disable.svg
        :align: center
        :alt:   screenshot of nodes to be disabled if no commutator is connected

        Disable this row that performs commutation if no commutator is connected.

#.  Run the workflow. Double-click the ``Miniscope GUI`` node and expand the visualizer that pops
    up.

#.  From here, you can:

    -   toggle between one of three data-processing pipelines for viewing
    -   control various properties related to the miniscope hardware, saving data,
        and the ΔF/F signal-processing pipeline
    -   toggle recording manually or with a trigger
    -   view real-time histogram data
    -   view real-time IO data
    -   commutate the UCLA Miniscope V4 tether automatically

..  [1]
    .. include::    /includes/start-workflow.rst