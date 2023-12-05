
#########################
Data Acquisition Software
#########################

******
Bonsai
******

The software that Open Ephys supports for acquiring data with the UCLA Miniscope v4 is `Bonsai <https://bonsai-rx.org/>`__. Bonsai is an open-source, highly extensible, reactive, visual programming language. Open Ephys provides Bonsai packages and example workflows (Bonsai scripts) for interacting with all of the hardware that it sells.

********************
Miniscope-DAQ-QT-GUI
********************

The software that the UCLA Miniscope team developed for acquiring data with the UCLA Miniscope v4 is the Miniscope DAQ QT GUI. To learn how to use the software https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/wiki

..  warning::
    The Miniscope DAQ QT GUI is not recommended. Its future is uncertain as the UCLA Miniscope team does not actively maintain it (as of writing this, the latest commit was two years ago), and there does not seem to be an active community maintainer either. Open Ephys has no intention of picking it up, as Bonsai is more easily extensible to customize for your specific experiment and a better user experience.