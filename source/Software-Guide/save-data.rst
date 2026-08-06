###################################################
Record image and orientation data to file
###################################################

..  note::

    This tutorial builds on the :ref:`quickstartguide` and previous tutorials, and is part
    of the :doc:`custom Bonsai workflows </Software-Guide/custom-workflows>` series.

    **You do not need this workflow to record data.** The :doc:`Miniscope GUI
    </Software-Guide/index>` records video, per-frame orientation and digital-input
    metadata, a session log, and a configuration snapshot from a single **Record** button,
    with all file names kept in sync; see :doc:`/Software-Guide/recording`. Follow this
    tutorial when you want to understand how the writers work, or when you need file
    outputs the GUI does not produce: a different codec, additional data streams, or a
    different file layout.

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
    color and the orientation of their grey arcs. A sink operator saves data or
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

..  note::

    The Miniscope GUI uses the same ``Bonsai.Vision.VideoWriter`` operator, with the
    ``Y800`` codec by default and ``MJPG`` when *Compress Video* is enabled. The FFV1
    option shown here is one the GUI does not expose, as it requires a separate Bonsai package
    (``Bonsai.Ffmpeg``) to handle encoding. It does require playback
    software that supports the codec.

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

..  tip::

    The GUI writes a wider CSV from this same operator, adding the hardware clock and both
    digital input states to each row. If you want that layout, see
    :ref:`gui_output_files` for the columns and extend the ``MemberSelector`` feeding the
    ``Timestamp`` node accordingly.

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

    ..  warning::

        Each writer resolves its own suffix independently here, so the video and CSV file
        names can drift apart: a ``Timestamp`` suffix is evaluated separately by each
        writer, and a ``FileCount`` suffix is counted per extension. If matching names
        matter to you, set the suffixes explicitly rather than relying on them lining up.
        The GUI avoids this by resolving one suffix for the whole set of files it writes.

#.  Run the workflow for some time to collect data.

#.  Navigate to the directory where data was saved which was specified in step
    3. Confirm the data exists and comports with expectations. The image can be
    easily viewed in any media playback software that supports the ``FourCC``
    value specified in step 3. The orientation data can be easily viewed in any
    spreadsheet software that supports .csv files.

.. _save_data_viewing_data:

***********************
Viewing the Data
***********************

Double-clicking the ``Image`` and ``Quaternion`` nodes opens Bonsai's built-in visualizers,
which is enough to confirm data is flowing. Judging image quality is another matter: it is
hard to tell by eye whether an image is clipping, or where the cells are in a noisy field
of view.

The :doc:`Miniscope GUI </Software-Guide/index>` can show saturation
view and histogram for exposure, :math:`\Delta F/F` and the max projection for finding
cells, and the reference-image overlay for returning to a field of view across sessions.
Because only one program can hold the Miniscope DAQ at a time, use the GUI to focus and
dial in LED brightness, sensor gain, and frame rate, export the configuration, then close
it and run this workflow with those settings. See :ref:`gui_visualizer_in_workflows`.

***********************
Next Steps
***********************

*   :doc:`/Software-Guide/trigger` gates this recording on a hardware digital signal.

*   :doc:`Recording with the GUI </Software-Guide/recording>` describes the files the GUI
    writes and how its recording modes work.
