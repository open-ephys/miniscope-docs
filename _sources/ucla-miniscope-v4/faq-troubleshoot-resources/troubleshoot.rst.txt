:orphan:

###############
Troubleshooting
###############


..
    how to clean https://groups.google.com/g/miniscope/c/kp-wRDo378s



    L13 (search it in forum and get it from support procedure)



    cant see cells during baseplating https://groups.google.com/g/miniscope/c/15I7gyrITR0



    ewl in support procedure

    *********************
    My Image Looks Weird:
    *********************

    Horizontal Bands/Stripes
    ======================================

    ..  image:: horizontal-stripes.webp
        :alt:   image of horizontal stripes

    The stripes appear when there is a bad connection between the Miniscope and the data acquisition hardware that generates a mismatch between frames. Confirm there are no signs of wear or damage on the coaxial cable.

    Lens Flare/Bright in Center
    ===========================

    ..  image:: lens-flare.webp
        :alt:   image of lens flate

    This artifact in your image usually indicates excessive excitation light. For more information, refer to :ref:`ucla-miniscope-v4/faq-troubleshoot-resources/faq:What Led Intensity Should I Use?`. 

    Much of this leaked excitation light makes its way to the image sensor by reflecting off the side surfaces of the dichroic filter. If you take this filter out and paint all its sides with black enamel paint or black optical paint it should drastically reduce the light leakage you see.
    https://groups.google.com/g/miniscope/c/giLyul7dAl0/m/7Ek3pdViAQAJ

    https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Initial-Testing-of-Assembled-Miniscope#imaging-your-surroundings

    Vertical lines
    ==============

    ads

    Marks/Hairs
    ===========

    Dust and other debris can make their way into the scope at various positions. If the mark on your image is in focus, it is most likely a mark on the CMOS sensor of the PCB or the 525 filter. Clean both with soft optics-safe cloth and test the image again.
    If the mark is large, see-through and out-of-focus, it could be dust on the lenses or the 495 dichroic. Disassemble the scope to find the culprit. Use compressed air to clean out places that are difficult to access.
    You want the center of your image to be very clean, however some dust/dirt can be inevitable, and users often reach a point where cleaning the scope more just introduces new marks. As long as marks are small and not in the center of the image, they should not greatly affect your imaging, but this depends on the application and is up to you to decide.

    These are often Delrin burrs that have come loose in the 525 pocket. The only solution is to unscrew the PCB flaps and remove the epoxy so that you can clean the sensor again. The easiest way to remove the epoxy is to very gently twist the Miniscope relative to the PCB to loosen the epoxy, the PCB should come loose. You can then remove the remaining epoxy with forceps so that you are free to reattach the PCB after cleaning.

    ******************************
    Insufficient Voltage Symptoms
    ******************************

    Banding due to low/inconsistent power - How to plug to jack

    This banding appears due to insufficient power. Depending on your settings and cable length, the USB supply might not be enough to power the scope.

    To avoid this, you can use the DC barrel jack to supply a voltage between 5 and 9V. A good starting point would be a 6V voltage. You can also use a wall adapter such as this one.
    You will need to move the jumper on the DAQ to change from USB power to an external power supply, as explained here.

    From forum: You should go with as low of a voltage as needed to get stable functionality. In almost all cases, 6V is enough and will result in less heating of the PCBs.

    You can check that the miniscope is receiving at minimum 4.5V at the coax cable connector, ideally 5V, maximum 6V. Do not power your scope in excess of 6V. (The voltage regulator in the Miniscope that can't handle more than 6 V).

    Internal: what happens if the voltage drop across the coaxial cable is larger than 1V is that the voltage regulators in the Miniscope start failing.

    You can also check no other equipment is drawing power from the USB ports.

    get the instructions from the support procedure doc here



    This banding appears due to insufficient power. Depending on your settings and cable length, the USB supply might not be enough to power the scope.


    To avoid this, you can use the DC barrel jack to supply a voltage between 5 and 9V. A good starting point would be a 6V voltage. You can also use a wall adapter such as this one.
    You will need to move the jumper on the DAQ to change from USB power to an external power supply, as explained here.


    From forum: You should go with as low of a voltage as needed to get stable functionality. In almost all cases, 6V is enough and will result in less heating of the PCBs.


    You can check that the miniscope is receiving at minimum 4.5V at the coax cable connector, ideally 5V, maximum 6V. Do not power your scope in excess of 6V. (The voltage regulator in the Miniscope that can't handle more than 6 V).

    This artifact in your image often indicates

    ***************************************************************
    Imaging Depth Does Not Change After Adjusting *EWL* in Software 
    ***************************************************************

    The most common cause of this symptom is incorrect placement of circular flexible PCB flaps around the electrowetting lens that results in an open or high-impedence connection between the lens and the rest of the circuitry. To remedy this, follow the below instructions until you find the source of the problem and eliminate it:

    #.  Visually inspect the area around the EWL:

        #.  Try following the assembly guide again.

        #.  Confirm both circular flexible PCB flaps are not protruding out from between the objective module and the emission module. If any are protruding, adjust flexible PCB flaps until you confirm they are not protruding.

        #.  Confirm the screws are properly tightened such that both circular flexible PCB flaps are firmly pressed against the EWL. If they not properly tightened, turn the screws until you confirm that they are properly tightened.

        #.  Confirm the bends in the flexible PCB have not been or do not appear over-flexed. If the bends have been or appear over-flexed, the connection between the EWL and the EWL driver might be broken. To help confirm the source of the problem is in the connection between the EWL driver and the EWL (and not the driver itself), proceed to the next step.

    #.  Inspect the temperature of the LED/EWL part of the PCB. If it burns to touch (don't hurt yourself), the EWL is likely dysfunctional. Repair requires procuring another EWL and replacing the broken one.

    #.  Validate the EWL driver's functionality:

        #.  Collect the following equipment:

            *   A UCLA Miniscope v4

            *   A coaxial cable

            *   Data acquisition hardware

            *   A computer with the proper port for connecting data acquisition hardware

                *   For Miniscope-DAQ or MiniDAQ, the proper port is a USB3.0
                
                *   For ONIX, __

            *   The proper cable for 

            *   An oscilloscope capable of measuring amplitudes up to 80 Volts

            *   An oscilloscope probe

        #.  Locate the EWL test points and the exposed copper EWL rings on the flex-rigid PCB:

            .. image::  ewl-pads.webp
                :alt:   image of ewl pads

            ..  image:: ewl-rings-exposed-copper.webp
                :alt:   image of exposed copper EWL rings

        #.  Follow the *Connect Hardware* section of the :doc:`/ucla-miniscope-v4/quick-start/index` corresponding to the data acquisition hardware you're using: 

    ..        *   :ref:`Connect ONIX 2.0 to acquire UCLA Miniscope v4 data <ucla-miniscope-v4/quick-start/onix-2-quick:Connect Hardware>`

            *   :ref:`Connect Miniscope-DAQ or MiniDAQ to acquire UCLA Miniscope v4 data <ucla-miniscope-v4/quick-start/onix-1-quick:Connect Hardware>`

            *   :ref:`Connect ONIX 1.0 to acquire UCLA Miniscope v4 data <ucla-miniscope-v4/quick-start/miniscope-daq-quick:Connect Hardware>`

        #.  Open a :doc:`data acquisition software </overview/data-acq-hardware>` that is compatible with your data acquisition hardware. If there are multiple, choose the one that is most familiar and easy-to-use for you.

        #.  Remove the "witch's hat" from the oscilloscope probe.

        #.  Connect the GND clip to the PCB's GND.

            #.  If the cable is not glued onto the UCLA Miniscope v4, swivel the .fl connector such that the GND pad next to it is exposed. Use that pad as GND.

            ..  image:: ucla-miniscope-v4-gndref-1.webp
                :alt:   image where to put oscope gnd clip 1

            #.  If the cable is glued onto the UCLA Miniscope v4, use the outer shielding of the coaxial cable.

            ..  image:: ucla-miniscope-v4-gndref-2.webp
                :alt:   image where to put oscope gnd clip 2

            #.  If the outer-shielding of the cable is glued, use the solderpads that mechanically and electrically connect the .fl jack to the PCB using an intermediate wire.

            ..  image:: ucla-miniscope-v4-gndref-3.webp
                :alt:   image where to put oscope gnd clip 3

        #.  Probe both flexible exposed copper EWL rings. If the copper connecting the EWL to the EWL driver, the EWL driver and your oscilloscope setup are functioning, the output of the oscilloscope is a 7kHz 70V/ :sub:`pk-pk` PWM signal as demonstrated in the image below. 

        ..  image:: 7khz-70v-pwm.webp
            :alt:   image of 7kHz 70V/ :sub:`pk-pk` from oscilloscope output

            *   If this step yields the 7kHz 70V/ :sub:`pk-pk` PWM signal, do not proceed further through this guide. The problem is proper placement or clamping of the flexible PCB EWL rings. Return to :ref:`ucla-miniscope-v4/faq-troubleshoot-resources/troubleshooot:Imaging Depth Does Not Change After Adjusting *EWL* in Software`.

        ..  important:: Try resetting the software and adjusting the probes if this oscilloscope output does not show the 7kHz 70V/ :sub:`pk-pk` PWM signal after the first time.

        ..  note::  If the source of the error is found in the following steps, DIY solutions for troubleshooting this particular issue requires a soldering equipment

        #.  Probe both EWL test points. If the EWL driver and your oscilloscope setup are functioning, the output of the oscilloscope is a 7kHz 70V/ :sub:`pk-pk` PWM signal as demonstrated in the image from the previous step.

        ..  important:: Try resetting the software and adjusting the probes if this oscilloscope output does not show the 7kHz 70V/ :sub:`pk-pk` PWM signal after the first time.

            *   If this step does yield the 7kHz 70V/ :sub:`pk-pk` PWM signal, and the previous step does not yield the 7kHz 70V/ :sub:`pk-pk` PWM signal: the EWL driver is functional, but the connection between the EWL driver and the EWL is likely dysfunctional. To repair this, solder a wire from the test pads to their corresponding flex PCB rings. 

            ..  image:: ewl-test-pad-corresponding-ring.webp
                :alt:   image of which test pad corresponds to which ring 

            *   If this step does not yield the 7kHz 70V/ :sub:`pk-pk` PWM signal: the EWL driver is likely dysfunctional. The EWL driver *can* be replaced, but we recommend acquiring a new PCB due to the difficulty of replacing the EWL driver. Open Ephys does not service this kind of repair.

    *********************************************
    Miniscope Software Displays Webcam Video Feed
    *********************************************

    Change the DeviceID value until it corresponds to , since this depends on other imaging devices you might have besides the miniscope (webcam, integrated laptop cam, virtual camera, etc). You can change this on the software window once the User Config is loaded, not only on the json file:


    Dust in the scope / cleaning


    We assemble scopes by hand and test them individually to assure they are working and have a clear field of view before shipping. Since any remaining dust or burrs can move around inside the upper pocket during shipping and become a problem, we cover remote dust troubleshooting on assembled scopes if the field of view is obscured, which should not happen. Shipping back is less efficient and might not resolve the issue. Small specks on the FOV are expected and do not usually affect the imaging quality.


    As for scopes we assemble, we cover remote dust troubleshooting. This is because we test our assembled scopes for a clear field of view before shipping, but it can happen that dust or burrs move around inside the upper pocket and become a problem. Shipping back is less efficient and might not resolve the issue.


    You can clean the scopes if there is something obscuring the field of view. This is advisable only if it's definitely interfering with your recording, as often you will just end up introducing more dust into the scope. If you need help judging that you can always send us some pictures.


    In focus dust or particles
    If you can clearly see dust or dirt while imaging, say, a resolution slide, it is most likely on the image sensor itself.


    Out of focus particles

    The spot you see can occasionally appear due to dust particles between the image sensor and the emission filter (or some residue on the filter itself). This kind of spot is normal and does not affect the imaging quality of the Miniscope and since it is static it will not be affected by background subtraction and motion correction.


    Cleaning
    You can remove the pcb from the top of the scope (no need to unscrew anything, but you will have to snap the glue bridges between the scope and the pcb). You can use a lens cloth to clean the 525 filter and CMOS sensor. I wouldn't use any fluid to clean it as they tend to leave streaks, but compressed air can be useful to blast out any dust. You can scrape off any glue residues and re-glue the pcb to the scope using epoxy.


    We use Araldite 2012 from Huntsman for assembly

    **************
    Burnt inductor
    **************

    The miniscope suddenly stopped functioning in the middle of a recording session. The mouse was still connected but the miniscope software displayed only a white screen and could no longer connect to the miniscope.

    Is there any chance that the coax cable you are using had a short across it at some point in the past? This can cause a power surge across the L13 inductor on the DAQ. While all 3 LEDs would still look to be on by eye, if the Data Link LED flickers very rapidly, the data over the coax cable could be corrupted and cause the connection to always fail.


    It's very likely that something shorted and an inductor on the DAQ fried up. If this is the case then the fix is simple. Would you mind removing the lid of the DAQ and sending me a picture of it? In particular close to the connector where you connect the coaxial cable of the Miniscope.


    It's very likely that a short burned one inductor. Because your device is out of warranty I would suggest doing the fix yourself, it's very easy to do. First, you will need to buy one of these inductors. Then, you will need to desolder the inductor marked in red in the picture below, and solder the new inductor in place. Please do all of this with the DAQ disconnected. 

