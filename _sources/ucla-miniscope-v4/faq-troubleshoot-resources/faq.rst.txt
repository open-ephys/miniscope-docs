
###
FAQ
###

********************************
What LED Intensity Should I Use?
********************************

The optimal LED intensity is high enough to:

*   maximize SNR. There is a baseline of noise due to imperfect sensors (which exhibit dark shot noise and read noise for example) and Poisson statistics. Fortunately, the amplitude of the signal from the sample typically has a more linear response to excitation light than the amplitude of noise does. Therefore, excitation light intensity can be tuned in a way that maximizes SNR.

*   maximize the signal's occupation of the sensor's dynamic range. This maximizes the bit-depth and information collected about the signal.

On the other hand, the optimal LED intensity is low enough to:

*   minimize saturating the sensor with emission light. Information is lost when signal exceeds the dynamic range of the sensor.

*   minimize photo-bleaching. Excessively high-intensity illumination can alter the fluorophore's structure such that the fluorophore no longer fluoresces. 

*   minimize contaminating the sensor with excitation light. Some amount of undesirable light always leaks through optical filters. During normal operation, this leakage is low enough that it is not discernable in the image and therefore of no concern. However, excessively high-intensity excitation light can result in a problematic amount of light leaked into the sensor. 

.. This manifests as ___.

.. :ref:`lens flare <ucla-miniscope-v4/faq-troubleshoot-resources/troubleshoot:Lens Flare>`.

The exact value of *LEDBrightness* value that satisifies the above conditions depends on the UCLA Miniscope version and other parameters of the experimental setup (e.g. type of fluorescent CA\ :sup:`2+` indicator, the amount of fluorescent Ca\ :sup:`2+` indicator, imaging depth, etc.). Measuring the power output of your miniscope is a helpful metric for determining if the user is in the correct ballpark. It is recommended to start ~200 µW and work your way up keeping the above factors in mind.

***************************************************
Should I Increase Exposure, LED Intensity, or Gain?
***************************************************

The trade-offs involved with adjusting the LED intensity is described above. The one most important to keep in mind for this question is photo-bleaching. The trade-off for increasing gain is that noise scales along with signal. The user must determine which of these, photo-bleaching or noise, is more detrimental to their experiment. For instance, photo-bleaching might be more detrimental for a user that wants to record over long periods of time and can mitigate noise with offline filtering anyway. On the other hand, noise might be more detrimental for a user that wants a closed-loop experiment that might have more stricter noise requirements.

The third factor in this is the *exposure duration per frame*. This quantity is inversely proportional to the frame rate. Therefore, if a high frame rate is low-priority in the experiment and the user wants to avoid increasing noise or photo-bleaching, they can also decrease the frame rate or average frames. The UCLA Miniscope v4 by default maximizes *total exposure* - this is not an adjustable parameter. 

***************************************************************************
How Can I Habituate All My Animals to the UCLA Miniscope v4 Simultaneously? 
***************************************************************************

Sometimes the experiment requires habituating more animals that you have UCLA Miniscope v4s. The animals can take turns wearing the miniscope during data acquisition, but habituation protocols suggest that each animal wears a miniscope for three weeks to adapt to the mechanical load of the miniscope. Dummy UCLA Miniscope v4s emulate the shape and weight distribution of a real UCLA Miniscope v4 without the tether (though a tether-like wire can be glued onto a dummy UCLA Miniscope v4). Dummy UCLA Miniscope v4 designs are `open-source for self-producing <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Miniscope_v4_Dummy.step>`__; Dummy UCLA Miniscope v4 products are `available for purchasing <https://open-ephys.org/miniscope-v4/miniscope-v4-dummy-scope>`__. These dummy miniscopes are for use on animals that have been implanted with the standard Base Plate Variant 2. Base Plate Variant 2 designs are `open-source for self-producing <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Mounting_Variation_2>`__; Base Plate Variant 2 products are `available for purchasing <https://open-ephys.org/miniscope-v4/miniscope-v4-base-plate-variant-2>`__. 

..
    **********************************************************
    How Do I Perform the Surgery to Use the UCLA Miniscope v4?
    **********************************************************

    Open Ephys sells a stereotaxic miniscope holder for positioning the UCLA Miniscope v4 during implantation. Stereotaxic holder designs are `open-source for self-producing <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Holder>`__.

    .. ; stereotaxic holder products are `available for purchasing <https://open-ephys.org/miniscope-v4/>`__. 

    Beyond this and the information included in the :ref:`ucla-miniscope-v4/user/preparation/index:Surgery Timeline`, Open Ephys does not provide support for surgeries.

    ..  todo:: add link to sterteotaxic UCLA Miniscope v4 store link or tell them how they can buy it from us if they can

*****************************************************
What Video CODEC Should I Use to Save Miniscope Data?
*****************************************************

GREY and FFV1 are recommended for neural recordings. 

*   GREY does not perform data compression. 

*   FFV1 performs lossless data compression. 

MJPG or similar is fine for behavioral recordings.

******************************************************
What Cable Lengths Can Be Used With UCLA Miniscope v4?
******************************************************

Cable lengths longer than three meters can be problematic. Significant voltage drop and power losses can occur over such distances with the coaxial cable. 

Decreasing the length of cable between the commutator and the data acquisition hardware allows increasing the length of the cable between the animal and the commutator. This reduces the potential of the cable length bottlenecking the maximimum explorable area. The length of the USB cable between the Miniscope-DAQ and the PC is not as critical.

******************************************************
Do I need a GRIN Lens? Which One? How Do I Procure It?
******************************************************

GRIN lenses are required for imaging deeper regions of the brain. It is important to source the GRIN lens with the correct optical properties and mechanical dimensions for the region you desire to image.

*   The UCLA Miniscope V4 Miniscope only functions with *relay* GRIN lenses. Relay GRIN lenses have a pitch *p* that follow this pattern: :math:`p=0.5n, n = 1, 2, 3...`. Objective GRIN lens are **not** compatible with the UCLA Miniscope v4.  

*   The UCLA Miniscope V4 is compatible with GRIN lens diameters from 0.5mm to 2mm.

*   The ideal length of GRIN lens depends on the depth of the region of brain being studied. For instance, mouse CA1 might requires a GRIN lens length of around 4mm to 5mm.

..  todo:: mention coating? https://groups.google.com/g/miniscope/c/4XRDskiVKhQ

Open Ephys does not sell GRIN lenses. For more information on this subject, ask GRIN lens vendors directly, such as Inscopix, GRINtech, or Go!Foton.

****************************************************************************
What Flourophores Are Compatible with the UCLA Miniscope v4 from Open Ephys?
****************************************************************************

The UCLA Miniscope v4 as sold off-the-shelf by Open Ephys is compatible with green fluorophores (e.g. GCAMP6f) in our :ref:`standard configuration <ucla-miniscope-v4/developer/mods:Standard>` or red fluorophores (e.g. jRGECO1a) in our :ref:`lime configuration <ucla-miniscope-v4/developer/mods:Lime>`. Is it also possible to adapt the UCLA Miniscope v4 to :ref:`other <ucla-miniscope-v4/developer/mods:Other>` fluorophores that don't share spectral characteristics with the fluorophores listed above. Refer to the :ref:`ucla-miniscope-v4/developer/mods:Spectral Modification` section for more details.

*********************************************************************************************************
How Do I Adjust Magnification/Field-of-View, Working Distance, Spatial Resolution, or Numerical Aperture?
*********************************************************************************************************

An alternative objective module can be constructed using a set of lenses that are different from the default ones. Swapping these objective modules allows adjustment of these optical characteristics. Refer to the :ref:`ucla-miniscope-v4/developer/mods:Objective Lens Modification` section for more details.

..
    *************************************************************
    How Do I Adjust Dynamic Range of LED Excitation Light Source?
    *************************************************************

    Refer to :doc:`/ucla-miniscope-v4/developer/mods/led-resistor` page of this documentation.

