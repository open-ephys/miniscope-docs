#####################
Compatible Devices
#####################

MiniCAM
----------------------------------------------

..  image:: /_static/images/minicam.png
    :alt:   image of minicam & minicam data
    :align: center

The MiniCAM (`store <https://open-ephys.org/minicam/minicam>`__, `github
<https://github.com/Aharoni-Lab/MiniCAM>`__) is a camera that enables data collection about the
behavior of a freely-moving animal during an experiment. It requires its own MiniDAQ or
Miniscope-DAQ, and it can be used with both the Miniscope-DAQ-QT-GUI or the OpenEphys.Miniscope Bonsai library. The MiniCAM ecosystem is comprised of the
`IR MiniCAM LED Ring <https://open-ephys.org/minicam/minicam-led-ring?rq=minicam>`__ and the
`MiniCAM Lenses Kit <https://open-ephys.org/minicam/lens-kit?rq=minicam>`__. The *IR MiniCAM LED
Ring* facilitates adjustment of the intensity of the illumination of the behavioral setup. IR
illumination does not contaminate the sensor that would be like light of lower wavelengths i.e.
visible light. The *MiniCAM Lenses Kit* enables lens swapping to adjust the field-of-view
according to the behavioral experiments. The lenses included in the *MiniCAM Lenses Kit* are:

..  image:: /_static/images/minicam-lenses.jpg
    :alt: chart of minicam lenses

MiniDAQ
----------------------------------------------

..  image:: /_static/images/minidaq.webp
    :alt:   image of minidaq
    :align: center

..  todo:: remove background of and color-correct these photos, or take new photos

The MiniDAQ is a simplified, more compact, and more affordable version of the Miniscope-DAQ, designed as a companion data acquisition device for the MiniCAM. It plugs directly into a PC through its on-board USB cable. It supports data acquisition from a single MiniCAM. Unlike the Miniscope-DAQ, the MiniDAQ does not support sync output or input trigger functions, nor accept an external supply. The MiniDAQ is supported by Bonsai and the Miniscope-DAQ-QT-Software. To acquire MiniCAM data with the MiniDAQ, follow the same user guides as the Miniscope-DAQ. While recording data from the Miniscope v4 with the MiniDAQ is possible, it is not recommended. The Miniscope DAQ has more extensive functionality and power management specific to integrate Miniscopes into an experimental setup.