
#############
Miniscope-DAQ
#############

.. image::  /_static/images/miniscope-daq_ucla-miniscope-v4.webp
    :alt:   photograph of ucla miniscope v4 & miniscope-daq

This guide serves as quick hardware-validation of and familiarization with the UCLA Miniscope v4 using the Miniscope-DAQ hardware. 

..  include::   includes.rst
    :start-line:    2
    :end-line:      4

****************
Connect Hardware
****************

..  todo:: better pictures here

#.  Disconnect any previously connected hardware from Miniscope-DAQ and UCLA Miniscope v4. 

#.  Connect only the following hardware for this guide:

    #.  Connect Miniscope-DAQ to the UCLA Miniscope v4 using the provided coaxial SMA plug ↔ U.FL plug tether:

        #.  Insert the cable’s SMA plug into Miniscope-DAQ’s SMA jack labeled `Miniscope`. Gently hand-tighten the SMA connector until the connector no longer turns:

            ..  image:: /_static/images/cable-sma-plug_miniscope-daq-sma-jack.webp
                :align: center
                :alt:   photograph of SMA plug going into Miniscope-DAQ SMA jack
                :height:    500px

        #.  Insert the cable’s U.FL plug into UCLA Miniscope’s U.FL jack. Confirm that a click is felt and heard before proceeding from this step:

            ..  image:: /_static/images/cable-mmcx-plug_ucla-miniscope-v4-ufl-jack.jpg
                :align: center
                :alt:   photograph of U.FL plug going into UCLA Miniscope v4 U.FL jack
                :height:    500px

    #.  Connect Miniscope-DAQ to your computer using the provided USB3.0 Micro Type B plug ↔ USB3.0 Type A plug cable:

        #.  Insert the cable’s USB3.0 Micro Type B plug into the Miniscope-DAQ’s USB3.0 Micro Type B jack located on the Miniscope-DAQ’s back face:

            .. image:: /_static/images/cable-usb3,0-microb-plug_miniscope-daq-usb3,0-microb-jack.webp
                :align: center 
                :alt:   photograph of usb plug going into miniscope-daq jack
                :height:    500px

        #.  Insert the cable’s USB3.0 Type A plug into your computer's USB3.0 Type A jack:

            .. image:: /_static/images/cable-usb3,0-a-plug_computer-usb3,0-a-jack.webp
                :align: center
                :alt:   photograph of usb plug going into computer usb jack
                :height:    500px

#.  Confirm that all three indicators on the miniscope-DAQ are illuminated before proceeding from this step as indicated in the below potos. If not all three indicators are illuminated, refer to :doc:`/ucla-miniscope-v4/faq-troubleshoot-resources/index` section.
        
..       .. image:: /_static/images/sma-plug_ufl-plug.webp
            :align: center
            :alt:   photograph of provided coaxial SMA plug ↔ U.FL plug cable
            :height:    500px

            
..        .. image:: /_static/images/usb3,0-microb-plug_usb3,0-a-plug_cable.webp
                :align: center
                :alt:   photograph of provided USB3.0 Micro Type B plug ↔ USB3.0 Type A plug cable
                :height:    500px

***************************************
Download, Install, and Configure Bonsai
***************************************

#.  If you have not already done so, 

    #.  `Download and Install Bonsai <https://bonsai-rx.org/docs/articles/installation.html>`_

    #.  `Install the necessary Bonsai packages: <https://bonsai-rx.org/docs/articles/packages.html>`_

        #.  Open Bonsai

        #.  Open the Bonsai package manager
        
            *   From Bonsai's landing window, select *Manage Packages*:

                ..  image:: /_static/images/bonsai-landing-page-package-manager-button.webp
                    :alt:   screenshot of Bonsai landing window with *Manage Packages* text highlighted
                    :align: center
                    :height: 300px

            or

            *   From Bonsai's workflow editor, hover over the *Tools* tab in the top ribbon to reveal a drop-down menu, and single left-click *Manage Packages...*.

                ..  image:: /_static/images/bonsai-workflow-editor-package-manager-button.webp
                    :alt:   screenshot of Bonsai workflow editor with *Manage Packages...* text highlighted
                    :align: center
                    :height: 300px

        #.  Select the *Browse* tab in the top ribbon:

            ..  image:: /_static/images/bonsai-package-manager-browse-button.webp
                :alt:   screenshot of Bonsai package manager with *Browse* tab highlighted
                :align: center
                :height: 400px

        #.  Configure the *Package Source* field to *All* using the drop-down menu:

            ..  image:: /_static/images/bonsai-package-manager-package-source-dropdown.webp
                :alt:   screenshot of Bonsai package manager with the Package Source drop-down higlighted
                :align: center
                :height: 400px

        #.  Download and install the required Bonsai packages:

            *   Bonsai.StarterPack

            *   OpenEphys.Bonsai.Miniscope

            For each one, search its name in the search bar, single left-click its corresponding entry, and single left-click the *Install* button:

            ..  image:: /_static/images/bonsai-starterpack.webp
                :alt:   screenshot of Bonsai package manager with search bar higlighted
                :align: center
                :height: 400px

            Click the *I Accept* button when prompted.

**************************************************
Interact with the UCLA Miniscope v4 Through Bonsai
**************************************************

..  todo::  tighter animations

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../_static', name = 'miniscope-daq_quick-start' %}
            {% include 'workflow.html' %}
        {% endwith %}

#.  Set the ``UCLAMiniscopeV4`` node's ``Index`` property to the value that corresponds to the index of your miniscope.

    #.  Single left-click on the ``UCLAMiniscopeV4`` node. 

    #.  Set the ``Index`` value to 0. 
    
    #.  If there are no additional cameras connected to your PC, skip this step. If there are additional cameras connected to your PC (including laptop webcams), finding the correct index value involves an iterative trial-and-error process.
    
        #.  Increment the ``Index`` value by 1.
        
        #.  Test the selected ``Index`` value by starting the workflow [1]_ and double left-clicking the ``Image`` node. If the displayed video stream corresponds to that of your miniscope, proceed to the next steps. Otherwise, return to the previous step.

#.  Start the Bonsai workflow [1]_ and test various features:

    **Real-time Data Visualization**

    :Image Data:    Double left-click the ``Image`` node. This displays a real-time visualization of image data from the sensor. Attenuate the sensor's exposure to ambient light or try imaging a target. Confirm that the ``Image`` node visualizer comports with expectations:

                    ..  image:: /_static/images/image-demo.webp
                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                        :align: center
                        :height: 400px

    :Orientation Data:   Double left-click the ``Quaternion`` node. This displays a real-time visualization of quarternion data which represents the miniscope's orientation. Single right-click the visualization, and single left-click the drop-down menu. Set the value in the ``History Length`` field to 100. Reorient the UCLA Miniscope v4. Confirm the quarternion visualization responds accordingly:

                        ..  image:: /_static/images/quarternion-demo.webp
                            :alt:   screenshot of Bonsai package manager with search bar higlighted
                            :align: center
                            :height: 400px

    **UCLA Miniscope v4 Settings**

    ..  note:: 

        *   When adjusting the *Frame Rate* and *Sensor Gain* settings, avoid under- or over- exposing the sensor.

        *   To adjust the *Dynamic Imaging Depth* setting, the UCLA Miniscope v4 must be fully assembled.

    Single-left click the ``UCLAMiniscopeV4`` node.

    :Frame Rate:    Change the ``FramesPerSecond`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Frame rate and exposure-duration-per-frame are inversely related, so higher frame rates produce darker images (supposing you're operating the miniscope within its sensor's dynamic range). Use this information and look at the ``Image`` node visualizer to confirm that the frame rate adjusts according to the ``FramesPerSecond`` value. 

                    ..  image:: /_static/images/fps-demo.webp
                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                        :align: center
                        :height: 400px

                    A discerning eye can also notice changes in frame rate, but that's typically less noticeable than changes in exposure duration.

    :Sensor Gain:   Change the ``SensorGain`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* paneand selecting a different option. Look at the ``Image`` node visualizer to confirm the that the gain is adjusted according to the value of ``SensorGain`` value.

                    ..  image:: /_static/images/gain-demo.webp
                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                        :align: center
                        :height: 400px

    :Excitation Light Intensity:    Change the ``LEDBrightness`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and sliding the scrollbar. Confirm that the intensity of the excitation light adjusts according to the ``LEDBrightness`` value.

                                    ..  image:: /_static/images/led-demo.webp
                                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                                        :align: center
                                        :height: 400px

    :Dynamic Focusing:  Place the assembled miniscope approximately its working distance away from an imaging target (e.g. a Kimwipe). Change the ``EWL`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Look at the ``Image`` node visualizer moves in-and-out according to the ``EWL`` value. 

                        ..  image:: /_static/images/focus-demo.webp
                            :alt:   screenshot of Bonsai package manager with search bar higlighted
                            :align: center
                            :height: 400px

                        If the imaging target does not enter the depth of focus, try readjusting the distance of the miniscope from the imaging target and performing the test again. If the working distance does not adjust, try reassembling the EWL module according to the *Assembly* instructions and repeating this part. 

..  [1] Start a workflow by single left-clicking the *Start* button at the top of the Bonsai workflow editor or pressing ``F5`` while the Bonsai workflow editor is the active window.


.. 0:10, 3:13, 6:10