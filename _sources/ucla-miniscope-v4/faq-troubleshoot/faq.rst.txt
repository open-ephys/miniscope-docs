
###
FAQ
###

..  todo:: do we need more readable list of FAQ?

..
    ***********
    List of FAQ
    ***********


    *   :ref:`ucla-miniscope-v4/faq-troubleshoot/faq:What Led Intensity Should I Use?`

    *   :ref:`ucla-miniscope-v4/faq-troubleshoot/faq:I Have More Experimental Subjects than UCLA Miniscope v4s. How Can I Habituate Them All to the UCLA Miniscope v4 Simultaneously?`

    *   :ref:`ucla-miniscope-v4/faq-troubleshoot/faq:How Do I Perform the Surgery for Using the UCLA Miniscope v4?`

********************************
What LED Intensity Should I Use?
********************************

The optimal LED intensity maximizes SNR while avoiding photo-bleaching your indicators or saturating your sensor. The exact power setting this corresponds to in software depends on the UCLA Miniscope version and other parameters of the experimental setup (e.g. type of Calcium indicator, how much Calcium indicator is expressed, imaging depth, etc.). Measuring the light output of your miniscope so that you know how much the luminosity of light you are sending to the brain can be helpful data when switching between Miniscope versions. Suitable  excitation light levels for Calcium Imaging with the UCLA Miniscope v4 is designed to work at 

Excitation light contamination can sometimes become an issue if setting power settings high in software. On the UCLA Miniscope v4, power settings of about 

At very high values, the thin coated filters inside the scope will leak light, resulting in this bright patch or 'flare' on the image. At these intensities the LED will be emitting several mW, which will lead to rapid photobleaching while imaging and is more appropriate for optogenetics. This was less likely to happen on older scopes as their LEDs were less bright.

At very high values, the thin coated filters inside the scope will leak light, resulting in this bright patch or 'flare' on the image. At these intensities the LED will be emitting several mW, which will lead to rapid photobleaching while imaging and is more appropriate for optogenetics. This was less likely to happen on older scopes as their LEDs were less bright.

We recommend always using a lightmeter to confirm the light output of the Miniscope in mW before starting experiments, and using values of well under 1mW output (starting at around 200 uW) to reduce photobleaching. 

Note that if you follow the 

********************************************************************************************************************************
I Have More Experimental Subjects than UCLA Miniscope v4s. How Can I Habituate Them All to the UCLA Miniscope v4 Simultaneously? 
********************************************************************************************************************************

Dummy UCLA Miniscope v4s emulate the shape and weight distribution of a real UCLA Miniscope v4 without the tether. Dummy UCLA Miniscope v4 designs are `open-source for self-producing <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Miniscope_v4_Dummy.step>`__; Dummy UCLA Miniscope v4 products are `available for purchasing <https://open-ephys.org/miniscope-v4/miniscope-v4-dummy-scope>`__. They are for use on animals that have been implanted with the standard Base Plate Variant 2. Similarily: Base Plate Variant 2 designs are `open-source for self-producing <https://github.com/Aharoni-Lab/Miniscope-v4/tree/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Mounting_Variation_2>`__; Base Plate Variant 2 products are `available for purchasing <https://open-ephys.org/miniscope-v4/miniscope-v4-base-plate-variant-2>`__. Dummy UCLA Miniscope v4s cannot produce images.

*************************************************************
How Do I Perform the Surgery for Using the UCLA Miniscope v4?
*************************************************************

Open Ephys does not provide support for surgeries. Refer to `this video <https://www.youtube.com/watch?v=SZPAQps_uVo>`_ from the 2021 Virtual Miniscope Workshop about the protocol for implanting GRIN lenses and baseplating for imaging CA1 with UCLA Miniscope v4 by Susie Feng from the Shuman lab.

*****************************************************
What Video CODEC Should I Use to Save Miniscope Data?
*****************************************************

GREY and FFV1 are recommended for neural recordings. 

*   GREY does not perform data compression. 

*   FFV1 performs lossless compresses data. It is capable of cutting files sizes by ~1/3. However, some softwares don't natively support decoding FFV1. Viewing or processing FFV1 data might require additional effort. 

For behavioral recordings, MJPG or similar is fine.

*************************************************************************
What Are the Differences Between UCLA Miniscope v3 and UCLA Miniscope v4?
*************************************************************************

We advise against using the UCLA Miniscope v3 for numerous technical reasons: the field of view on the v3 Miniscope is smaller, it does not have an electrowetting lens so it cannot be remotely adjusted by software and has worse excitation efficiency than v4. We don't carry v3 at OEPS because it has been superseded by v4, which does have a tunable lens, a longer working distance (and can even image through cranial windows) as well as using GRIN lenses for deeper structures, better power management for enhanced excitation efficiency and prolonged recording capabilities and the onboard head-orientation sensor for commutator use. (though our commutators can be used with orientation information from another source, like real-time pose estimation with SLEAP or DLC, but it is more straightforward, reliable and less computationally expensive to use a headborne sensor).

Refer to this Comparison Chart

***********************************************************
How Do I Procure GRIN Lenses? Which GRIN lens Should I Use?
***********************************************************

We don't sell relay GRIN lenses, so for more information about that you'd be better off asking Inscopix or GRINtech or Go!Foton (CLH series lenses following this post).
Please note relay GRIN lenses for implantation compatible with the Miniscope v4 are listed as having pitch close to a multiple of 0.5 (as opposed to objective GRIN lenses previously used with the v3 miniscope which have pitches close to 0.25).

Relay GRIN lenses for implantation compatible with the Miniscope v4 are listed as having pitch close to a multiple of 0.5 (as opposed to objective GRIN lenses previously used with the v3 miniscope which have pitches close to 0.25, explained here). The v4 is compatible with all relay GRIN lens diameters, from 0.5mm to 2mm (according to this).

You might want to browse the Miniscope forum, the wiki or the virtual miniscope workshop for more information about what other researchers in the miniscope community use and recommend.

—
If you use a 0.25 pitch lens, the image is formed at infinity, so they can be used as objective lenses in some miniscopes such as the v3.
At 0.5 pitch (or multiples), the image is focused just above the lens surface, making it a suitable lens for relaying the image from deep structures.

https://groups.google.com/g/miniscope/c/9LWngOlzN-E/m/-DGFPpg2BQAJ 
GoFoton also produces compatible relay GRIN lenses but in our experience they have slightly lower optical performance than Grintech (the lenses sold by Inscopix) lenses. You can contract Walter Boyles , walter.boyles _at_ gofoton.com, for more info.

****************************************************************************************************
What Is the Difference Between UCLA Miniscopes from Open Ephys and UCLA Miniscopes from Competitors?
****************************************************************************************************

..  warning:: 
    Each of these differences between Open Ephys Miniscopes and Labmaker Miniscopes was true at one point. These differences might still be true. It could be the case that Labmaker has changed their product since publishing this documentation, but since we aren't up-to-date with Labmaker's manufacturing, . 

Labmaker Miniscopes are not compatible with baseplates sold by Open Ephys. Labmaker Miniscope DAQs have 3 SMA connectors whereas Open Ephys Miniscope DAQs have 4 SMA connectors. This additional SMA conncetor exposes an additional I/O. Labmaker Miniscope DAQs are not 5V tolerant. Open Ephys and Labmaker might not sell the same version at all points in time. Open Ephys and Labmaker Miniscopes use different LEDs as excitation light sources. This could affect signal contamination or power settings set in software. Open Ephys equipment comes with Open Ephys quality assurance and customer service.

******************************************************
What Cable Lengths Can Be Used With UCLA Miniscope v4?
******************************************************

Cable lengths longer than three meters are problematic. Significant voltage drop and power losses can occur over such distances with the coaxial cable provided by Open Ephys. 

The distance between the commutator and the acquisition system must be kept short to avoid data loss.

The Miniscope DAQ can be mounted near the commutator so that this distance can be kept very short (10-15 cm) and have a long USB cable going from the DAQ to the PC. 

***************************
Configuration File Problems
***************************

My video is split up into several files instead of one long video matching the recording time I specified
The default way that data gets saved is by saving 1000 frames per video file. You can change this value on the userConfig file. 
If you want to save your whole recording in a single video just put a large value there (>100000). To answer your question about the delay, there is no delay between the time that consecutively files get saved. 

My recorded video plays back too quickly
About the playback, what you are looking at is a speed-up display of your video. The displayed length value that your player shows doesn't match  the actual length of the recording because its played at a higher frame rate. You can easily check this by looking at the timestamp file. Each frame gets timestamped, and if you calculate the time between frames you can check the actual frame rate. 

***************************************************************************************************************************************************************************************************************************************************************************
What Flourophores or What Range of Wavelengths of Excitation/Emission Light are Compatible with the UCLA Miniscope v4 from Open Ephys? How Do I Adapt the UCLA Miniscope v4 to a Fluorophore Not Natively Supported by the Standard UCLA Miniscope v4 Configuration?  
***************************************************************************************************************************************************************************************************************************************************************************

The UCLA Miniscope v4 as sold by Open Ephys is compatible with green indicators (e.g. GCAMP6f) or red indicators (e.g. RCaMP).

Is it also possible to adapt the UCLA Miniscope v4 to a fluorophore other than one that shares spectral characteristics of GCAMP6f or RCaMP. To learn about your options in this respect, refer to :doc:`/ucla-miniscope-v4/developer/common-mods/led-filters-dichroic-combo` page of this documentation.

****************************************************************
How Do I Adjust Magnification/Field-of-View or Working Distance?
****************************************************************

Refer to :doc:`/ucla-miniscope-v4/developer/common-mods/lenses-combo` page of this documentation.

*************************************************************
How Do I Adjust Dynamic Range of LED Excitation Light Source?
*************************************************************

Refer to :doc:`/ucla-miniscope-v4/developer/common-mods/led-resistor` page of this documentation.

