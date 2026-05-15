.. _user_guide:

#################
User Guide
#################

In this User Guide you can find information about using the Miniscope system for performing experiments, beyond the information in the :doc:`/Hardware-Guide/index` and :doc:`/Software-Guide/index`.

This is the typical timeline for a standard Miniscope v4 protocol for deep brain imaging in a transfected mouse:

..  image:: /_static/images/ucla-miniscope-v4_standard-surgery_timeline.webp
    :alt:   image of visualization of surgery timeline

Imaging neural activity with the UCLA Miniscope v4 requires that cells in the regions of interest are loaded with fluorescent CA\ :sup:`2+` indicators. This is primarily accomplished through viral injection. GRIN lenses are necessary for experiments studying deeper regions of the brain. If viral injection and GRIN lens implantation are both to be performed, it is easier to inject before implanting. Three weeks of mouse recovery are recommended after GRIN lens implantation. After recovery, the mouse can be baseplated. The baseplate provides a structural mount for the UCLA Miniscope v4 so that the user can reliably register the miniscope into the same position relative to the brain. Two weeks of habituation after baseplating is recommended. The UCLA Miniscope v4 enables several weeks to months of in-vivo imaging and freely-moving behavior after this step. 

For habituation, a UCLA Miniscope v4 Dummy Scope (`store <https://open-ephys.org/miniscope-v4/miniscope-v4-dummy-scope>`__, `GitHub <https://github.com/Aharoni-Lab/Miniscope-v4/blob/master/Miniscope-v4-Body-Parts/Parts%20v4_2/Miniscope_v4_Dummy.step>`__) is recommended.

Open Ephys does not currently provide support for surgeries. As a starting point for developing a surgical protocol for your own experiment, refer to the 2021 Miniscope Workshop video `Grin Lens & Baseplate Surgery <https://www.youtube.com/watch?v=SZPAQps_uVo>`_ about implanting and baseplating a mouse for imaging its CA1 with the UCLA Miniscope v4 by Susie Feng from the Shuman lab.

Last, confirm that you have compatible data acquisition hardware. If you don't, acquire the compatible data acquisition hardware.

Consult the :doc:`faq` for more information related to Miniscope usage.

.. toctree::
    :hidden:
    :maxdepth: 1
    :titlesonly:

    faq

.. troubleshoot
.. data-analysis
