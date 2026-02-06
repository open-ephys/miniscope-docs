.. _quickstartguide:

#################
Quick Start Guide
#################

This Quick Start Guide uses Bonsai to connect to a Miniscope v4 via a Miniscope DAQ and validate its functionality. You can learn more about the software's functionality and other software options to acquire from the Miniscope v4 in the :doc:`/Software-Guide/index`. For additional information on using miniscopes for experiments, please refer to the :doc:`/User-Guide/index`.

.. figure:: /_static/images/Miniscope_and_DAQ.jpg
   :width: 50%
   :align: center

   Starting with the basics: a system made up of the Miniscope DAQ v3.3 and a Miniscope v4.

Connecting the Hardware
-------------------------------------------

*Required components: Miniscope v4, Miniscope DAQ, coaxial tether (SMA ↔ U.FL), USB3.0 cable (Micro Type B ↔ Type A)*

#.  Connect the Miniscope DAQ to the miniscope using the coaxial tether:
    
    * Insert the tether's SMA plug into Miniscope DAQ's SMA jack labeled `Miniscope`. Gently hand-tighten the SMA connector until the connector no longer turns:

    ..  image:: /_static/images/cable-sma-plug_miniscope-daq-sma-jack.webp
            :align: center
            :alt:   photograph of SMA plug going into Miniscope DAQ SMA jack
            :height: 250px

    * Click the tether's U.FL connector into the miniscope's U.FL socket. Make sure you align both parts and feel them click together to ensure the connector is correctly seated:

    ..  image:: /_static/images/cable-ufl-plug_ucla-miniscope-v4-ufl-jack.webp
            :align: center
            :alt:   photograph of U.FL plug going into Miniscope v4 U.FL jack
            :height: 250px

#.  Connect the Miniscope DAQ to a USB 3.0-compatible port on your computer using the high-speed USB cable provided. USB 3.0-compatible port are usually indicated by a blue color and are often at the back of PCs.

    .. important:: Ensure you establish a reliable USB connection by using a high-speed USB cable and connecting directly to the port instead of through a hub or extension. USB cables longer than 2 meters are not recommended.

    * Insert the cable's USB3.0 Type A plug into your computer's USB3.0 Type A jack:

    .. image:: /_static/images/cable-usb3,0-a-plug_computer-usb3,0-a-jack.webp
            :align: center
            :alt:   photograph of usb plug going into computer usb jack
            :height: 250px

    * Insert the cable's USB3.0 Micro Type B plug into the Miniscope-DAQ's USB3.0 Micro Type B jack located on the Miniscope-DAQ's back face:

    .. image:: /_static/images/cable-usb3,0-microb-plug_miniscope-daq-usb3,0-microb-jack.webp
            :align: center 
            :alt:   photograph of usb plug going into miniscope-daq jack
            :height:    500px

Once all connections have been properly established, you should see all three indicators LEDs on the Miniscope DAQ turn on as in the image above. 

Installation
-------------------------------------------

#. The Miniscope DAQ works via USB, so make sure you configure the Operating System's USB settings to avoid suspension due to power management.

#. `Download and Install Bonsai <https://bonsai-rx.org/docs/articles/installation.html>`__ either as a portable environment or a system-wide application.

#. Install the following packages from the `Bonsai Package Manager <https://bonsai-rx.org/docs/articles/packages.html>`__, making sure the Package source set to "All":

* *OpenEphys.Miniscope.Design*: An extension of the *OpenEphys.Miniscope* library that includes graphical user interfaces (GUIs). Installing *OpenEphys.Miniscope.Design* automatically installs *OpenEphys.Miniscope* as a dependency.
* *Bonsai.StarterPack*: the "standard library" for Bonsai that contains tools that are used in almost every workflow.

Testing the Miniscope's Functionality
-------------------------------------------

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../_static', name = 'uclaminiscopev4-miniscopedaq-quick' %}
            {% include 'workflow.html' %}
        {% endwith %}

#.  Set the ``UCLAMiniscopeV4`` operator's ``Index`` property to the value that corresponds to the index of your miniscope.

    ..  grid::
        
        ..  grid-item::
            :columns:   3

            ..  image:: /_static/images/uclaminiscopev4-properties.webp
                :align: center
                :alt:   screenshot of UCLAMiniscopeV4 node properties for index

        ..  grid-item::
            
            ..  include::  /includes/set-index.rst

#.  Start the Bonsai workflow by left-clicking the green *Start* button at the top of the Bonsai workflow editor or by pressing ``F5``. Once the workflow is running, you can test various features:

    **Real-time Data Visualization**

    :Image Data:    Double left-click the ``Image`` node. This displays a real-time visualization of image data from the sensor. Try imaging a sample such as a tissue paper. Confirm that the magnified image of the sample appears in the ``Image`` node visualizer:

                    ..  image:: /_static/images/image-demo.webp
                        :alt:   animation of demonstrating miniscope data
                        :align: center
                        :height: 400px

    :Orientation Data:   Double left-click the ``Quaternion`` node. This displays a real-time visualization of quaternion data which represents the miniscope's orientation. Right-click the visualization, and left-click the drop-down menu. Set the value in the ``History Length`` field to 100. Reorient the UCLA Miniscope v4. Confirm the quaternion visualization responds accordingly:

                        ..  image:: /_static/images/quaternion-demo.webp
                            :alt:   animation of demonstrating quaternion data
                            :align: center
                            :height: 400px

                        To learn more about how to interpret quaternion data, visit the `IMU Data
                        article <https://github.com/open-ephys/wiki/wiki/IMU-Data>`_ in the Open Ephys Wiki.

    **Miniscope Settings Configuration**

    Left-click the ``UCLAMiniscopeV4`` node to access the Properties pane on the right.

    :Frame Rate:    Change the ``FramesPerSecond`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Frame rate and exposure-duration-per-frame are inversely related, so higher frame rates produce darker images. Use this information and look at the ``Image`` node visualizer to confirm that the frame rate adjusts according to the ``FramesPerSecond`` value. 

                    ..  image:: /_static/images/fps-demo.webp
                        :alt:   animation of changing miniscope fps
                        :align: center
                        :height: 400px

                    A discerning eye can also notice changes in frame rate, but that requires a moving image.

    :Sensor Gain:   Change the ``SensorGain`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Look at the ``Image`` node visualizer to confirm that the sensor's gain is adjusted according to the value of ``SensorGain`` value.

                    ..  image:: /_static/images/gain-demo.webp
                        :alt:   animation of changing miniscope gain
                        :align: center
                        :height: 400px

    :Excitation Light Intensity:    Change the ``LEDBrightness`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and sliding the scrollbar. Confirm that the intensity of the excitation light adjusts according to the ``LEDBrightness`` value.

                                    ..  image:: /_static/images/led-demo.webp
                                        :alt:   animation of changing miniscope excitation light intensity
                                        :align: center
                                        :height: 400px

    :Dynamic Focusing:  Place the miniscope approximately its working distance away from the sample. Change the ``EWL`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Look at the ``Image`` node visualizer shifting in and out of focus according to the ``EWL`` value. 

                        ..  image:: /_static/images/focus-demo.webp
                            :alt:   animation of changing miniscope focus
                            :align: center
                            :height: 400px

Find out how to record image and orientation data, how to perform automatic commutation to avoid the tether from twisting, how to gate data acquisition with a hardware trigger and more in the :doc:`/Software-Guide/index`.

Powering off the system
-------------------------------------------

The Miniscope DAQ does not have an on/off button. When you are done with acquisition, close the software and unplug the board from USB and/or power.