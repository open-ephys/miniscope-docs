#################
Workflow Tutorial
#################

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../../../_static', name = 'uclaminiscopev4-miniscopedaq-savedata' %}
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
            
            #.  Set the ``Index`` value to 0 by editing the ``Index`` field that appears in the *Properties* pane after left-clicking the ``UCLAMiniscopeV4`` node. 

            #.  Test the selected ``Index`` value by starting the workflow [1]_ and double left-clicking the ``Image`` node. If the displayed video stream corresponds to that of your miniscope, proceed to the next step. Otherwise, increment the ``Index`` value by 1 and repeat this step.

            ..  note::  A device index specifies a camera device. If there are additional cameras connected to your PC (including laptop webcams), finding the correct index value might involve an iterative trial-and-error process.

#.  Save data according to your specifications:

    **Image video data:**

    ..  grid::

        ..  grid-item::

            ..  image:: /_static/images/videowriter-properties.webp
                :alt:   screenshot of videowriter properties
                :align: center

        ..  grid-item::

            *   Left-click the ``VideoWriter`` node and edit fields under the properties pane. Confirm frame rate matches that of the UCLA Miniscope v4. 

            *   For ``FourCC`` value recommendations, GREY and FFV1 are recommended for neural recordings. 

                *   GREY does not perform data compression. 

                *   FFV1 performs lossless data compression. 

                MJPG or similar is sufficient for behavioral recordings.

    **Orientation quarternion data:** 

    ..  grid::

        ..  grid-item::

            ..  image:: /_static/images/csvwriter-properties.webp
                :alt:   screenshot of csvwriter properties
                :align: center

        ..  grid-item::

            *   Left-click the ``CsvWriter`` node and edit fields under the properties pane

    ..  note::  
        
        *   It is best practice to set the ``Suffix`` property to Timestamp or FileCount or set the Overwrite property to False to avoid accidentally overwriting important data. 

        *   Left-click a property field's corresponding label to display the property's detail at the bottom of the properties pane (e.g. how it is for the ``FileName`` property in the two above screenshots)

        *   To temporarily disable saving image or orientation data, disable the respective Writer operator left-clicking the *Disable* option in the menu that appears after right-clicking an enabled node (or left-clicking the node and using the ``Ctrl+D`` hotkey). Re-enable the Writer node by left-clicking the *Enable* option in the menu that appears after right-clicking a disabled node (or left-clicking the node and using the ``Ctrl+Shift+D`` hotkey). 

#.  Start the workflow. [1]_

#.  Stop the workflow. [2]_

#.  Navigate to the directory where data was saved which was specified in step 3. Confirm the data exists and comports with expectations. The image can be easily viewed in any media playback software that supports the ``FourCC`` value specified in step 3. The orientation data can be easily viewed in any spreadsheet software that can supports .csv files.

.. include::    /includes/start-workflow.rst

..  [2] Stop a workflow by left-clicking the *Stop* button (indicated by dark red square) at the top of the Bonsai workflow editor or pressing ``Shift+F5`` while the Bonsai workflow editor is the active window.