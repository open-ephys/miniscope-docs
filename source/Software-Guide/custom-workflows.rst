.. _custom_workflows:

####################################################################
Acquisition Within Bonsai
####################################################################

.. toctree::
    :hidden:

    commutate
    save-data
    trigger
    gui-in-workflow

.. _bonsai_installation:


Installation
==============

Everything on this page needs Bonsai and the ``OpenEphys.Miniscope`` packages installed. This
is the same setup described in the :ref:`quickstartguide`.

..  note::

    Bonsai and the ``OpenEphys.Miniscope`` packages all run on 64-bit Windows
    only.

#.  The Miniscope DAQ works over USB, so configure the operating system's USB settings to
    avoid suspending the device due to power management.

#.  `Download and install Bonsai <https://bonsai-rx.org/docs/articles/installation.html>`__,
    either as a portable environment or as a system-wide application.

#.  Install the following packages from the `Bonsai Package Manager
    <https://bonsai-rx.org/docs/articles/packages.html>`__, making sure the
    Package source set to "All":

    * ``Bonsai.StarterPack``: the "standard library" for Bonsai, containing tools used in
      almost every workflow.

    * ``OpenEphys.Miniscope.Design``: an extension of the ``OpenEphys.Miniscope`` library that
      includes graphical elements. Installing ``OpenEphys.Miniscope.Design``
      automatically installs ``OpenEphys.Miniscope`` as a dependency.

    *  ``OpenEphys.Miniscope.Gui`` (Optional): The :ref:`MiniscopeV4 GUI
       <gui_interface>` can be used as Bonsai operator and launched from a
       Bonsai workflow.

       .. note::

        The MiniscopeV4 GUI is currently in alpha. During this time the
        package is not published to NuGet, so it does not appear in the Bonsai
        package manager and has to be installed from a local file instead. Click
        `here <https://gofile.me/7cMIw/xWpCInTog>`__ to download the package and
        follow the `Installing a Local NuGet Package in Bonsai
        <https://github.com/open-ephys/wiki/wiki/Installing-a-Local-Nuget-Package-in-Bonsai>`__
        article in the Open Ephys Wiki to see how to install the package you just
        downloaded in Bonsai.

        If you only want to run the GUI as a standalone application, you can
        install the standalone installer. See
        :doc:`/Software-Guide/openephys-gui`.

.. _acquisition_base:

Basic Miniscope Control and Acquisition
==========================================

#.  Copy or download the following workflow using the corresponding icons and
    paste the contents or open the .bonsai file in Bonsai:

    ..  raw:: html

        {% with static_path = '../_static', name =
        'uclaminiscopev4-miniscopedaq-quick' %}
            {% include 'workflow.html' %}
        {% endwith %}

    *   The ``UclaMiniscopeV4`` node represents a ``UclaMiniscopeV4`` *source*
        operator as indicated by its green color and the orientation of
        its gray arc. Source operators produce data.

    *   The ``UclaMiniscopeV4`` operator's output (``Bonsai.Miniscope.V4Frame``)
        has four members. They can be accessed by right-clicking the
        ``UclaMiniscopeV4`` node and hovering the cursor over the *Output*
        option in the pop-up menu. Left-clicking on one of these members
        automatically places a new ``MemberSelector`` node. These nodes can also
        be placed by searching modules in the search bar in the *Toolbox* pane
        or by using the ``Ctrl+E`` hotkey.

    *   The ``MemberSelector`` operators are *transform* operators as indicated
        by the nodes' blue color and lack of gray bar. Transform operators
        transform data. The ``MemberSelector`` operator transforms data by
        selecting one or multiple members of its input to output.

    *   In this workflow, the ``Image`` and ``Quaternion`` members are selected
        from ``Bonsai.Miniscope.V4Frame`` to be visualized.


#.  Using the drop-down list, set the ``UclaMiniscopeV4`` operator's ``Index``
    property to the value that corresponds to the index of your miniscope.

    ..  image:: /_static/images/uclaminiscopev4-properties.webp
        :align: center
        :alt:   screenshot of UclaMiniscopeV4 node properties for index

    ..  note::  If there is no value populated in the drop-down, check the hardware connections. If there are multiple Miniscope DAQs connected to your PC, iterate through the index values while testing the node's functionality to verify what index corresponds to each miniscope.

#.  Start the Bonsai workflow by left-clicking the green *Start* button at the
    top of the Bonsai workflow editor or by pressing ``F5``. Once the workflow
    is running, you can test various features:

    **Real-time Data Visualization**

    :Image Data:    Double left-click the ``Image`` node. This displays a
       real-time visualization of image data from the sensor. Try imaging a
       sample such as a tissue paper. Confirm that the magnified image of the
       sample appears in the ``Image`` node visualizer.

                    ..  image:: /_static/images/image-demo.webp
                        :alt:   animation of demonstrating miniscope data
                        :align: center
                        :height: 400px

\
    :Orientation Data:   Double left-click the ``Quaternion`` node. This
      displays a real-time visualization of quaternion data which represents the
      miniscope's orientation. Right-click the visualization, and left-click the
      drop-down menu. Set the value in the ``History Length`` field to 100.
      Reorient the UCLA Miniscope v4. Confirm the quaternion visualization
      responds accordingly. To learn more about how to interpret quaternion
      data, visit the `IMU Data article
      <https://github.com/open-ephys/wiki/wiki/IMU-Data>`_ in the Open Ephys
      Wiki.

                        ..  image:: /_static/images/quaternion-demo.webp
                            :alt:   animation of demonstrating quaternion data
                            :align: center
                            :height: 400px


    **Miniscope Settings Configuration**

    Left-click the ``UclaMiniscopeV4`` node to access the Properties pane on the
    right.

    :Frame Rate:    Change the ``FramesPerSecond`` value by left-clicking the
       corresponding field's drop-down menu located in the *Properties* pane and
       selecting a different option. Frame rate and exposure-duration-per-frame
       are inversely related, so higher frame rates produce darker images. Use
       this information and look at the ``Image`` node visualizer to confirm
       that the frame rate adjusts according to the ``FramesPerSecond`` value. A
       discerning eye can also notice changes in frame rate, but that requires a
       moving image.

                    ..  image:: /_static/images/fps-demo.webp
                        :alt:   animation of changing miniscope fps
                        :align: center
                        :height: 400px


\
    :Sensor Gain:   Change the ``SensorGain`` value by left-clicking the
      corresponding field’s drop-down menu located in the *Properties* pane and
      selecting a different option. Look at the ``Image`` node visualizer to
      confirm that the sensor's gain is adjusted according to the value of
      ``SensorGain`` value.

                    ..  image:: /_static/images/gain-demo.webp
                        :alt:   animation of changing miniscope gain
                        :align: center
                        :height: 400px

\
    :Excitation Light Intensity:    Change the ``LEDBrightness`` value by
       left-clicking the corresponding field’s drop-down menu located in the
       *Properties* pane and sliding the scrollbar. Confirm that the intensity
       of the excitation light adjusts according to the ``LEDBrightness`` value.

                                    ..  image:: /_static/images/led-demo.webp
                                        :alt:   animation of changing miniscope excitation light intensity
                                        :align: center
                                        :height: 400px

\
    :Dynamic Focusing:  Place the miniscope approximately its working distance
     away from the sample. Change the ``EWL`` value by left-clicking the
     corresponding field’s drop-down menu located in the *Properties* pane and
     selecting a different option. Look at the ``Image`` node visualizer
     shifting in and out of focus according to the ``EWL`` value.

                        ..  image:: /_static/images/focus-demo.webp
                            :alt:   animation of changing miniscope focus
                            :align: center
                            :height: 400px

Find out how to record image and orientation data, how to perform automatic
commutation to prevent the tether from twisting, how to gate data acquisition
with a hardware trigger, and more in the :doc:`/Software-Guide/openephys-gui`.

Tutorials
==============

To understand how the ``UclaMiniscopeV4`` can be used directly, check out the following tutorials.
Remember that everywhere the ``UclaMiniscopeV4`` node is placed, the ``MiniscopeV4Gui.bonsai``
included workflow can be swapped in without changing the downstream logic while allowing for full
visualization with the GUI.

..  grid:: 3
    :gutter: 3

    ..  grid-item-card:: 1. Automate Commutation
        :link:      /Software-Guide/commutate
        :link-type: doc
        :class-card: intro-card

        Rotate the coaxial tether automatically from the Miniscope's orientation
        data, and control the commutator manually with keypresses.

    ..  grid-item-card:: 2. Record Data to File
        :link:      /Software-Guide/save-data
        :link-type: doc
        :class-card: intro-card

        Write image data and timestamped orientation data to disk, with a choice
        of video codecs.

    ..  grid-item-card:: 3. Trigger Recordings
        :link:      /Software-Guide/trigger
        :link-type: doc
        :class-card: intro-card

        Gate recording with a hardware digital signal, producing one file set
        per trigger pulse.

    ..  grid-item-card:: 4. Miniscope V4 Gui Operator
        :link:      /Software-Guide/gui-in-workflow
        :link-type: doc
        :class-card: intro-card

        Use the complete :ref:`Miniscope V4 GUI <gui_interface>` as a Bonsai
        Operator that can be combined with custom workflows.
