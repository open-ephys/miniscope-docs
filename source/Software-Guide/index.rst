
.. _software_guide:

Software Guide
##############################

.. toctree::
    :hidden:

    openephys-gui
    custom-workflows

The `Open Ephys Miniscope V4 GUI
<https://github.com/open-ephys/bonsai-miniscope-gui>`__ is free, open-source
software for controlling and acquiring data from the UCLA Miniscope V4. It
provides automatic integration with :ref:`torque-free commutators
<commutators>`, hardware synchronization of scope data with external equipment,
triggered recordings, and a variety of real-time processing and data plotting
features.

..  button-link:: https://gofile.me/7cMIw/xMQ4LKVI3
    :color: primary
    :class: wide-button
    :shadow:

    Download Open Ephys Miniscope V4 GUI (Windows)


..  image:: /_static/images/miniscopev4_gui/miniscopev4-gui-all-streams.png
    :alt:   the Open Ephys Miniscope V4 GUI window
    :width: 80%
    :align: center

.. important::

   The **Open Ephys Miniscope V4 GUI** requires the :ref:`latest DAQ firmware
   <daq_firmware_update>`. This firmware provides hardware-level synchronization
   signals, hardware-generated frame counts, and greatly improved IMU sampling
   regularity.

   The Open Ephys Miniscope V4 GUI is currently in **alpha**. Its interface and
   behavior may change in future releases, and this documentation will be
   updated to match. Some screenshots and workflow examples are still
   placeholders and will be filled in as they become available.

   **We welcome your feedback.** While the GUI is in alpha, issues and comments
   can be directed to the `GitHub issues page
   <https://github.com/open-ephys/bonsai-miniscope-gui/issues>`__. Please file
   any comment, concern, or feature request as its own new issue, so we can
   prioritize what to add or fix next.

The GUI is built on `Bonsai <https://bonsai-rx.org/>`__, but runs entirely on
its own: no Bonsai knowledge required. It can also be dropped into a Bonsai
workflow as a single node for fully custom acquisition; see
:doc:`/Software-Guide/custom-workflows`.

Miniscope-DAQ-QT-Software (Deprecated)
-------------------------------------------

The original acquisition software for the Miniscope v4 and MiniCAM, from the
UCLA Miniscope Team. It supports commutation and works with webcams as well as
Miniscope hardware. The QT software remains available `here
<https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/releases>`__