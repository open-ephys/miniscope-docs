#################
Workflow Tutorial
#################

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../../../_static', name = 'uclaminiscopev4-miniscopedaq-savedata' %}
            {% include 'workflow.html' %}
        {% endwith %}

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that
    corresponds to the index of your miniscope.

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

            Left-click the enabled ``VideoWriter`` node and edit fields under
            the properties pane. Confirm the frame rate matches that of the ``UCLAMiniscopeV4`` operator. Make sure the file name has a valid extension
            (".avi"). "Y800", an uncompressed greyscale codec, is specified as
            the ``FourCC``.
                
        ..  grid-item::

            ..  image:: /_static/images/bonsai.vision.videowriter-properties.png
                :alt:   screenshot of bonsai.vision.videowriter properties
                :align: center

    Alternatively, you can also use ``VideoWriter`` from the Bonsai.FFmpeg
    library to save video. This provides more flexibility to save video files
    using `FFmpeg <https://ffmpeg.org/>`_ as the backend.

    ..  grid::

        ..  grid-item::

            Disable the first ``VideoWriter`` node and enable the second one. The description of the node in the properties pane can help you distinguish between them. Left-click the enabled
            ``VideoWriter`` node and edit fields under the properties pane.
            Confirm frame rate matches that of the UCLA Miniscope v4. Make sure
            the file name has a valid extension (".avi"). The parameters in
            ``OutputArguments`` specify an 8-bit video with "FFV1", a lossless
            compression codec, as the FourCC. Here are FFmpeg settings that output a compressed grayscale 8-bit video: "-c: ffv1 -pix_fmt gray -bits_per_raw_sample 8".
                
        ..  grid-item::

            ..  image:: /_static/images/bonsai.ffmpeg.videowriter-properties.webp
                :alt:   screenshot of bonsai.ffmpeg.videowriter properties
                :align: center

    ..  tip::
        The FFV1 codec produces smaller files (~30% reduction can be expected), 
        but it requires software that supports loading/playing back this kind 
        of video.

    **Orientation quaternion data:** 

    ..  grid::

        ..  grid-item::

            Left-click the ``CsvWriter`` node and edit fields under the
            properties pane. Make sure the file name has a valid extension
            (".csv").

        ..  grid-item::

            ..  image:: /_static/images/csvwriter-properties.webp
                :alt:   screenshot of csvwriter properties
                :align: center

    ..  note::  
        
        *   It is best practice to set the ``Suffix`` property to Timestamp or 
            FileCount or set the Overwrite property to False to avoid 
            accidentally overwriting important data. 

        *   Left-click a property field's corresponding label to display the 
            property's detail at the bottom of the properties pane (e.g. how it
            is for the ``FileName`` property in the two above screenshots)

        *   To temporarily disable saving image or orientation data, disable the
            respective Writer operator left-clicking the *Disable* option in the
            menu that appears after right-clicking an enabled node (or
            left-clicking the node and using the ``Ctrl+D`` hotkey). Re-enable
            the Writer node by left-clicking the *Enable* option in the menu
            that appears after right-clicking a disabled node (or left-clicking
            the node and using the ``Ctrl+Shift+D`` hotkey). 

#.  Start the workflow by left-clicking the *Start* button (indicated by green
    triangle) at the top of the Bonsai workflow editor or pressing ``F5`` while
    the Bonsai workflow editor is the active window.

#.  Stop the workflow by left-clicking the *Stop* button (indicated by dark red
    square) at the top of the Bonsai workflow editor or pressing ``Shift+F5``
    while the Bonsai workflow editor is the active window.

#.  Navigate to the directory where data was saved which was specified in step
    3. Confirm the data exists and comports with expectations. The image can be
    easily viewed in any media playback software that supports the ``FourCC``
    value specified in step 3. The orientation data can be easily viewed in any
    spreadsheet software that can supports .csv files.
