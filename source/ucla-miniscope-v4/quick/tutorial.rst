##################################################
Interact with the UCLA Miniscope v4 Through Bonsai
##################################################

..  todo::  tighter animations

#.  Download the following workflow (.bonsai file) and open it with Bonsai:

    ..  raw:: html

        {% with static_path = '../../_static', name = 'uclaminiscopev4-miniscopedaq-quick' %}
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
            
            ..  include::  /includes/set-index.rst

#.  Start the Bonsai workflow [1]_ and test various features:

    **Real-time Data Visualization**

    :Image Data:    Double left-click the ``Image`` node. This displays a real-time visualization of image data from the sensor. Attenuate the sensor's exposure to ambient light or try imaging a target. Confirm that the ``Image`` node visualizer comports with expectations:

                    ..  image:: /_static/images/image-demo.webp
                        :alt:   animation of demonstrating miniscope data
                        :align: center
                        :height: 400px

    :Orientation Data:   Double left-click the ``Quaternion`` node. This displays a real-time visualization of quaternion data which represents the miniscope's orientation. Right-click the visualization, and left-click the drop-down menu. Set the value in the ``History Length`` field to 100. Reorient the UCLA Miniscope v4. Confirm the quaternion visualization responds accordingly:

                        ..  image:: /_static/images/quarternion-demo.webp
                            :alt:   animation of demonstrating quaternion data
                            :align: center
                            :height: 400px

                        To learn more about how to interpret quaternion data, visit the `IMU Data
                        article <https://github.com/open-ephys/wiki/wiki/IMU-Data>`_ in the Open Ephys wiki repo.

    **UCLA Miniscope v4 Settings**

    ..  note:: 

        *   When adjusting the *Frame Rate* and *Sensor Gain* settings, avoid under- or over- exposing the sensor.

        *   To adjust the *Dynamic Imaging Depth* setting, the UCLA Miniscope v4 must be fully assembled.

    Left-click the ``UCLAMiniscopeV4`` node.

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

    :Dynamic Focusing:  Place the assembled miniscope approximately its working distance away from an imaging target (e.g. a Kimwipe). Change the ``EWL`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Look at the ``Image`` node visualizer moves in-and-out according to the ``EWL`` value. 

                        ..  image:: /_static/images/focus-demo.webp
                            :alt:   animation of changing miniscope focus
                            :align: center
                            :height: 400px

                        If the imaging target does not enter the depth of focus, try readjusting the distance of the miniscope from the imaging target and performing the test again. If the working distance does not adjust, try reassembling the EWL module according to the *Assembly* instructions and repeating this part. 

..  [1] 
    ..  include::  /includes/start-workflow.rst
