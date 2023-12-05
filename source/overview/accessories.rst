
###########
Accessories
###########

There are accessories that are frequently used with miniscopes. Those include:

*   :ref:`overview/accessories:Open Ephys Coaxial Commutator` 

*   :ref:`overview/accessories:UCLA MiniCam`

*****************************
Open Ephys Coaxial Commutator
*****************************

..  image:: commutator-ucla-miniscope-v4-ophelia.webp
    :alt:   animated image of the commutator rotating the tether when ophelia is rotated

The Open Ephys Coaxial Commutator (`documentation <https://open-ephys.github.io/commutator-docs/coax-commutator/index.html>`_, `store <https://open-ephys.org/commutators/coaxial-commutator>`_, `github <https://github.com/open-ephys/onix-commutator>`_) enables twist-free connection between a stationary data acquisition device and the UCLA Miniscope v4 mounted onto a freely-moving animal. This promotes natural animal behavior by nearly eliminating mechanical stress during neurophysiology experiments. This also improves signal reliability by maintaining electrical continuity between stationary and moving electronics. It accomplishes this by utilizing the IMU on-board the UCLA Miniscope v4 PCB to sense the orientation of the miniscope and rotate the tether accordingly. For a guide to using the UCLA Miniscope v4 using the commutator, please refer to these guides: `Automating Commutation with ONIX and UCLA Miniscope v4 <https://open-ephys.github.io/commutator-docs/coax-commutator/user-guide/automatic-control/onix-miniscopev4.html>`_ or `Automating Commutation with Miniscope DAQ and UCLA Miniscope v4 <https://open-ephys.github.io/commutator-docs/coax-commutator/user-guide/automatic-control/miniscopedaq-miniscopev4.html>`_.

************
UCLA MiniCam
************

..  image:: ucla-miniscope-v4_minicam-data.webp
    :alt:   image of minicam & minicam data

..  todo::
    fix refs. gitref?

The MiniCAM (`documentation <https://open-ephys.github.io/commutator-docs/coax-commutator/index.html>`_, `store <https://open-ephys.org/commutators/coaxial-commutator>`_, `github <https://github.com/open-ephys/onix-commutator>`_) is a camera that enables data collection about the behavior of a freely-moving animal during an experiment. It is compatible with the Miniscope-DAQ-QT-GUI and Miniscope-DAQ. The MiniCAM ecosystem comprises of the `IR MiniCAM LED Ring <https://open-ephys.org/minicam/minicam-led-ring?rq=minicam>`_ and the `MiniCAM Lenses Kit <https://open-ephys.org/minicam/lens-kit?rq=minicam>`_. The *IR MiniCAM LED Ring* enables easy adjustment of the intensity of the illumination of the behavaioral setup. The *MiniCAM Lenses Kit* enables lens swapability to adjust the field of view for their behavioral setup.
