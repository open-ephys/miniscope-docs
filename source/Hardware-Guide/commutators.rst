.. _commutators:

#####################
Coaxial Commutators
#####################

..  image:: /_static/images/commutator_ucla-miniscope-v4_ophelia.gif
    :alt:   animated image of the commutator rotating the tether when ophelia is rotated
    :align: center

Commutators compatible with the Miniscope System need support at least a single coaxial channel. Motorized and passive versions exist, as well as versions with an additional optical channel for optical fibres.

The Open Ephys Coaxial Commutator (`documentation <https://open-ephys.github.io/commutator-docs/index.html>`__, `store <https://open-ephys.org/commutators/coaxial-commutator>`__, `github <https://github.com/open-ephys/commutators>`__) enables twist-free connection between a stationary data acquisition device and the UCLA Miniscope v4 mounted onto a freely-moving animal. This promotes natural animal behavior by reducing mechanical stress during neurophysiology experiments. This also improves signal reliability by maintaining electrical continuity between stationary and moving electronics. It accomplishes this by utilizing the IMU on-board the UCLA Miniscope v4 PCB to sense the orientation of the miniscope and rotate the tether accordingly. For a guide on how to use the UCLA Miniscope v4 with the commutator, please refer to these guides: `Automating Commutation with ONIX and UCLA Miniscope v4 <https://open-ephys.github.io/bonsai-onix1-docs/articles/hardware/ucla-miniscope-v4/overview.html>`__ or :doc:`Automating Commutation with Miniscope-DAQ and UCLA Miniscope v4 </Software-Guide/miniscope-daq/commutate/index>`.
