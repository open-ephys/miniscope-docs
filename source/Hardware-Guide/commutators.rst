.. _commutators:

#####################
Coaxial Commutator
#####################

.. raw:: html

  <center><video width="560" height="340" controls>
  <source src="../_static/videos/Miniscope_Coax commutator.mp4" type="video/mp4">
  </video></center>

Commutators compatible with the Miniscope System must support at least a single 50Ohm coaxial channel. Motorized and passive versions exist, as well as versions with an additional optical channel for optical fibres.

The Open Ephys Coaxial Commutator (`documentation <https://open-ephys.github.io/commutator-docs/index.html>`__, `store <https://open-ephys.org/commutators/coaxial-commutator>`__, `github <https://github.com/open-ephys/commutators>`__) enables twist-free connection between a stationary data acquisition device and the UCLA Miniscope v4 mounted onto a freely-moving animal. This promotes natural animal behavior by reducing mechanical stress during neurophysiology experiments. This also improves signal reliability by maintaining electrical continuity between stationary and moving electronics. It accomplishes this by utilizing the IMU on-board the UCLA Miniscope v4 PCB to sense the orientation of the miniscope and rotate the tether accordingly. To use the UCLA Miniscope v4 with the commutator via the Miniscope DAQ, the simplest route is the :doc:`Miniscope GUI </Software-Guide/index>`, which connects to and drives the commutator from its Control Panel with no workflow to build; see the :doc:`interface reference </Software-Guide/interface>`. To build the commutation logic yourself, refer to :doc:`Automating Commutation with Miniscope-DAQ and UCLA Miniscope v4 </Software-Guide/commutate>`.
