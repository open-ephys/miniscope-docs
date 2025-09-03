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
            
            ..  include::  /includes/set-index.rst
        
        ..  grid-item::
            :columns:   3

            ..  image:: /_static/images/uclaminiscopev4-properties.webp
                :align: center
                :alt:   screenshot of ucla miniscope v4 node properties for index

#.  Save data according to your specifications:

    **Image video data:**

    ..  grid::

        ..  grid-item::

            *   Left-click the ``VideoWriter`` node and edit fields under the properties pane. Confirm frame rate matches that of the UCLA Miniscope v4. Make sure the file name has a valid extension (".avi").

            *   For ``FourCC``, "DIB " and "FMP4" are recommended for neural recordings. 

                *   "DIB " is compatible with 8-bit and 10-bit data. 

                *   "FMP4" performs data compression for smaller file sizes and is compatible only with 8-bit data.

        ..  grid-item::

            ..  image:: /_static/images/videowriter-properties.webp
                :alt:   screenshot of videowriter properties
                :align: center

    **Orientation quarternion data:** 

    ..  grid::

        ..  grid-item::

            *   Left-click the ``CsvWriter`` node and edit fields under the properties pane. Make sure the file name has a valid extension (".csv").

        ..  grid-item::

            ..  image:: /_static/images/csvwriter-properties.webp
                :alt:   screenshot of csvwriter properties
                :align: center

    ..  note::  
        
        *   It is best practice to set the ``Suffix`` property to Timestamp or FileCount or set the Overwrite property to False to avoid accidentally overwriting important data. 

        *   Left-click a property field's corresponding label to display the property's detail at the bottom of the properties pane (e.g. how it is for the ``FileName`` property in the two above screenshots)

        *   To temporarily disable saving image or orientation data, disable the respective Writer operator left-clicking the *Disable* option in the menu that appears after right-clicking an enabled node (or left-clicking the node and using the ``Ctrl+D`` hotkey). Re-enable the Writer node by left-clicking the *Enable* option in the menu that appears after right-clicking a disabled node (or left-clicking the node and using the ``Ctrl+Shift+D`` hotkey). 

#.  Start the workflow. [1]_

#.  Stop the workflow. [2]_

#.  Navigate to the directory where data was saved which was specified in step 3. Confirm the data exists and comports with expectations. The image can be easily viewed in any media playback software that supports the ``FourCC`` value specified in step 3. The orientation data can be easily viewed in any spreadsheet software that can supports .csv files.

..  [1]
    .. include::    /includes/start-workflow.rst

..  [2] Stop a workflow by left-clicking the *Stop* button (indicated by dark red square) at the top of the Bonsai workflow editor or pressing ``Shift+F5`` while the Bonsai workflow editor is the active window.
