
###############
Troubleshooting
###############

*******************************
Image Contains Stripes or Bands
*******************************
..
  ..  image:: horizontal-stripes.webp
      :alt:   image of black horizontal stripes on UCLA Miniscope v4 mimage

The stripes appear when there is a bad connection between the Miniscope and the DAQ, so there is a mismatch between frames coming to the DAQ. Would you check if the coaxial cable has any signs of wear or damage?

This banding appears due to insufficient power. Depending on your settings and cable length, the USB supply might not be enough to power the scope.


To avoid this, you can use the DC barrel jack to supply a voltage between 5 and 9V. A good starting point would be a 6V voltage. You can also use a wall adapter such as this one.
You will need to move the jumper on the DAQ to change from USB power to an external power supply, as explained here.


From forum: You should go with as low of a voltage as needed to get stable functionality. In almost all cases, 6V is enough and will result in less heating of the PCBs.


You can check that the miniscope is receiving at minimum 4.5V at the coax cable connector, ideally 5V, maximum 6V. Do not power your scope in excess of 6V. (The voltage regulator in the Miniscope that can't handle more than 6 V).

******************************
Insufficient Voltage Symptoms
******************************



****************************************************************
Image Doesn't Adjust After Adjusting ETL/EWL Voltage in Software 
****************************************************************

This is almost always due to the PCB being incorrectly placed around the electrowetting lens and therefore not making full contact. Take a look at your objective module- do the screws need tightening so that the PCB and the lens are pushed closer together? Can you see any PCB stick out at the side? The circles of the PCB must fit neatly inside the objective module and touch the electrowetting lens.

********************
Image Contains Marks
********************

Dust and other debris can make their way into the scope at various positions. If the mark on your image is in focus, it is most likely a mark on the CMOS sensor of the PCB or the 525 filter. Clean both with soft optics-safe cloth and test the image again.
If the mark is large, see-through and out-of-focus, it could be dust on the lenses or the 495 dichroic. Disassemble the scope to find the culprit. Use compressed air to clean out places that are difficult to access.
You want the center of your image to be very clean, however some dust/dirt can be inevitable, and users often reach a point where cleaning the scope more just introduces new marks. As long as marks are small and not in the center of the image, they should not greatly affect your imaging, but this depends on the application and is up to you to decide.

*********************************************************
Image Was Clean, But Now I See Dark In-Focus Marks/Hairs
*********************************************************

These are often Delrin burrs that have come loose in the 525 pocket. The only solution is to unscrew the PCB flaps and remove the epoxy so that you can clean the sensor again. The easiest way to remove the epoxy is to very gently twist the Miniscope relative to the PCB to loosen the epoxy, the PCB should come loose. You can then remove the remaining epoxy with forceps so that you are free to reattach the PCB after cleaning.

***************
USB2.0 Symptoms
***************

These symptoms are often caused by using USB2.0 instead of USB3.0

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

*************************
Bright Spot in Center
*************************

Much of this leaked excitation light makes its way to the image sensor by reflecting off the side surfaces of the dichroic filter. If you take this filter out and paint all its sides with black enamel paint or black optical paint it should drastically reduce the light leakage you see.
https://groups.google.com/g/miniscope/c/giLyul7dAl0/m/7Ek3pdViAQAJ

**********************************************
When to turn up Gain Instead of LED Intensity?
**********************************************

For the V4 Miniscope, likely LED values under 30 and recording lengths under 30 minutes will not generate noticeable bleaching. That said, the only real issue with always increasing the gain over increasing LED intensity is the gain will scale up both the signal and CMOS image sensor noise. This will result in slightly noisier recordings where things like salt-and-pepper noise and potentially some row noise might show up. But these are very easy to deal with and filter out offline so they aren't much of an issue. 

https://github.com/Aharoni-Lab/Miniscope-v4/wiki/Initial-Testing-of-Assembled-Miniscope#imaging-your-surroundings