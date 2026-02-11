#################
Save Data
#################

..  note::  This tutorial builds on the :ref:`quickstartguide` and previous tutorials.

After following this tutorial, the user will be able to save image data and timestamped orientation data from the UCLA Miniscope v4.

..  raw:: html

    {% with static_path = '../_static', name = 'uclaminiscopev4-miniscopedaq-savedata' %}
        {% include 'workflow.html' %}
    {% endwith %}

***********************
Workflow Description
***********************

**Save Image Data**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-savedata_video-data.svg
    :alt:   screenshot of uclaminiscopev4 node boxed
    :align: center

*   The ``Image`` node connects to a ``VideoWriter`` node. The ``VideoWriter``
    operator writes data to a video file according to settings in the
    *Properties* pane that appears after left-clicking the ``VideoWriter`` node.

*   There are two ``VideoWriter`` operators. The first one is from the
    ``Bonsai.Vision`` package, and the second one is from the ``Bonsai.FFmpeg``
    package. They are both *sink* operators as indicated by the nodes' purple
    color and the orientation of its grey arc. A sink operator saves data or
    triggers external events.

*   The first ``VideoWriter`` operator is enabled. It can be disabled by
    clicking it and pressing :kbd:`Ctrl+D`. It is configured to save video
    using a Y800 (no compression) codec.

*   The second ``VideoWriter`` operator is disabled. It can be enabled by
    clicking it and pressing :kbd:`Ctrl+Shift+D`. It is configured to save
    video using an 8-bit FFV1 (lossless compression) codec.

*   The ``Annotation`` nodes (which contain a "#" symbol) are simply there to
    indicate the difference between the ``Bonsai.Vision.VideoWriter`` operator
    and the ``Bonsai.FFmpeg.VideoWriter`` operator. They don't provide any
    functional difference in the workflow. You can think of them like comments
    in code.

**Save Timestamped Orientation (Quaternion) Data**

..  image:: /_static/images/uclaminiscopev4-miniscopedaq-savedata_quat-data.svg
    :alt:   screenshot of uclaminiscopev4 node boxed
    :align: center

*   The ``FrameNumber, Quaternion`` node connects to the ``Timestamp`` node. The
    ``Timestamp`` operator appends timestamps to items that are emitted by the
    upstream operator.

*   The ``Timestamp`` node connects to the  ``CsvWriter`` node. The
    ``CsvWriter`` operator writes data to a csv file according to settings in
    the *Properties* pane that appears after left-clicking the ``CsvWriter``
    node. 

***********************
Configure the Hardware
***********************

Configure the hardware as in the :ref:`quickstartguide` or as in the :doc:`commutate` tutorial if you are using an Open Ephys Commutator.

**********************
Get Started in Bonsai
**********************

In addition to the setup steps outlined in previous tutorials, install the following package:

* *Bonsai.FFmpeg*: controls video output encoding.

This package requires installing `FFmpeg <https://ffmpeg.org/>`_ separately in order to work. Follow the FFmpeg installation guide available in `documentation for the Bonsai.FFmpeg package <https://bonsai-rx.org/ffmpeg/>`_.

***********************
Operate the Workflow
***********************

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

#.  If using a commutator, set the COM port associated with your commutator in the workflow. If not using a commutator, delete the nodes corresponding to the commutation.

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
    using FFMpeg as the backend.

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

#.  Run the workflow for some time to collect data.

#.  Navigate to the directory where data was saved which was specified in step
    3. Confirm the data exists and comports with expectations. The image can be
    easily viewed in any media playback software that supports the ``FourCC``
    value specified in step 3. The orientation data can be easily viewed in any
    spreadsheet software that can supports .csv files.