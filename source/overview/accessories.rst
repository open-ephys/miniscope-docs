
#####################
Miniscope Accessories
#####################

Accessories frequently used with miniscopes include:

*   :ref:`overview/accessories:Open Ephys Coaxial Commutator` 

*   :ref:`overview/accessories:MiniCam`

*****************************
Open Ephys Coaxial Commutator
*****************************

..  image:: /_static/images/commutator_ucla-miniscope-v4_ophelia.gif
    :alt:   animated image of the commutator rotating the tether when ophelia is rotated
    :align: center

The Open Ephys Coaxial Commutator (`documentation
<https://open-ephys.github.io/commutator-docs/coax-commutator/index.html>`__, `store
<https://open-ephys.org/commutators/coaxial-commutator>`__, `github
<https://github.com/open-ephys/onix-commutator>`__) enables twist-free connection between a
stationary data acquisition device and the UCLA Miniscope v4 mounted onto a freely-moving animal.
This promotes natural animal behavior by reducing mechanical stress during neurophysiology
experiments. This also improves signal reliability by maintaining electrical continuity between
stationary and moving electronics. It accomplishes this by utilizing the IMU on-board the UCLA
Miniscope v4 PCB to sense the orientation of the miniscope and rotate the tether accordingly. For a
guide on how to use the UCLA Miniscope v4 with the commutator, please refer to this page:
`Automating Commutation
<https://open-ephys.github.io/commutator-docs/coax-commutator/user-guide/automatic-control/index.html>`__.

*******
MiniCAM
*******

..  image:: /_static/images/minicam.png
    :alt:   image of minicam & minicam data
    :align: center

The MiniCAM (`store <https://open-ephys.org/minicam/minicam>`__, `github
<https://github.com/Aharoni-Lab/MiniCAM>`__) is a camera that enables data collection about the
behavior of a freely-moving animal during an experiment. It requires its own MiniDAQ or
Miniscope-DAQ, and it can be used with Miniscope-DAQ-QT-GUI. The MiniCAM ecosystem comprises of the
`IR MiniCAM LED Ring <https://open-ephys.org/minicam/minicam-led-ring?rq=minicam>`__ and the
`MiniCAM Lenses Kit <https://open-ephys.org/minicam/lens-kit?rq=minicam>`__. The *IR MiniCAM LED
Ring* facilitates adjustment of the intensity of the illumination of the behavioral setup. IR
illumination does not contaminate the sensor that would be like light of lower wavelengths i.e.
visible light. The *MiniCAM Lenses Kit* enables lens swapping to adjust the field-of-view
according to the behavioral experiments. The lenses included in the *MiniCAM Lenses Kit* are:

..  image:: /_static/images/minicam-lenses.jpg
    :alt: chart of minicam lenses