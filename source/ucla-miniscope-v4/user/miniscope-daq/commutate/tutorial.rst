#################
Workflow Tutorial
#################

..  note:: An Open Ephys Coaxial Commutator is necessary for this workflow 

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../../../_static', name = 'uclaminiscopev4-miniscopedaq-commutate' %}
            {% include 'workflow.html' %}
        {% endwith %}

..  the following step should be derived from another source because it's reused everywhere

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

    #.  Set the ``Index`` value to 0 by editing the ``Index`` field that appears in the *Properties* pane after left-clicking the ``UCLAMiniscopeV4`` node. 

    #.  Test the selected ``Index`` value by starting the workflow [1]_ and double left-clicking the ``Image`` node. If the displayed video stream corresponds to that of your miniscope, proceed to the next step. Otherwise, increment the ``Index`` value by 1 and repeat this step.

        ..  note::  A device index specifies a camera device. If there are additional cameras connected to your PC (including laptop webcams), finding the correct index value might involve an iterative trial-and-error process.

#.  Set the COM port associated with your commutator in the workflow

    *   Left-click the ``Commutator`` node and edit the ``PortName`` property under the `Properties` pane to match the port that corresponds to your commutator. 
    
    ..  note::  
        
        If you are uncertain about which COM port corresponds to your , follow these instructions:

        #.  Open Window's *Device Manager*.

        #.  Unplug the commutator, and plug it back in. Observe which COM port disappears and appears in device manager when doing so - that is the COM port associated with your commutator. If the commutator does not appear in device manager, follow `these instructions <https://www.pjrc.com/teensy/troubleshoot.html>`__

.. include::    ../../../quick/tutorial.rst
    :start-line:    84
    :end-line:      86