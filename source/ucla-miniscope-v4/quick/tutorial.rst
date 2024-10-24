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
            
            #.  Set the ``Index`` value to 0 by editing the ``Index`` field that appears in the *Properties* pane after left-clicking the ``UCLAMiniscopeV4`` node. 

            #.  Test the selected ``Index`` value by starting the workflow [1]_ and double left-clicking the ``Image`` node. If the displayed video stream corresponds to that of your miniscope, proceed to the next step. Otherwise, increment the ``Index`` value by 1 and repeat this step.

            ..  note::  A device index specifies a camera device. If there are additional cameras connected to your PC (including laptop webcams), finding the correct index value might involve an iterative trial-and-error process.

#.  Start the Bonsai workflow [1]_ and test various features:

    **Real-time Data Visualization**

    :Image Data:    Double left-click the ``Image`` node. This displays a real-time visualization of image data from the sensor. Attenuate the sensor's exposure to ambient light or try imaging a target. Confirm that the ``Image`` node visualizer comports with expectations:

                    ..  image:: /_static/images/image-demo.webp
                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                        :align: center
                        :height: 400px

    :Orientation Data:   Double left-click the ``Quaternion`` node. This displays a real-time visualization of quarternion data which represents the miniscope's orientation. Right-click the visualization, and left-click the drop-down menu. Set the value in the ``History Length`` field to 100. Reorient the UCLA Miniscope v4. Confirm the quarternion visualization responds accordingly:

                        ..  image:: /_static/images/quarternion-demo.webp
                            :alt:   screenshot of Bonsai package manager with search bar higlighted
                            :align: center
                            :height: 400px

    **UCLA Miniscope v4 Settings**

    ..  note:: 

        *   When adjusting the *Frame Rate* and *Sensor Gain* settings, avoid under- or over- exposing the sensor.

        *   To adjust the *Dynamic Imaging Depth* setting, the UCLA Miniscope v4 must be fully assembled.

    Left-click the ``UCLAMiniscopeV4`` node.

    :Frame Rate:    Change the ``FramesPerSecond`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Frame rate and exposure-duration-per-frame are inversely related, so higher frame rates produce darker images. Use this information and look at the ``Image`` node visualizer to confirm that the frame rate adjusts according to the ``FramesPerSecond`` value. 

                    ..  image:: /_static/images/fps-demo.webp
                        :alt:   screenshot of Bonsai package manager with search bar higlighted
                        :align: center
                        :height: 400px

                    A discerning eye can also notice changes in frame rate, but that requires a moving image.

    :Sensor Gain:   Change the ``SensorGain`` value by left-clicking the corresponding field’s drop-down menu located in the *Properties* pane and selecting a different option. Look at the ``Image`` node visualizer to confirm that the sensor's gain is adjusted according to the value of ``SensorGain`` value.

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

..  include::  /includes/start-workflow.rst
