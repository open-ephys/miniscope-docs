
#########################
Data Acquisition Hardware
#########################

The :ref:`overview/data-acq-hardware:Miniscope-DAQ` is the most common hardware for acquiring data from miniscopes derived from the UCLA Miniscope v4 and the v4 itself.

.. note:: Wireless miniscopes with on-board loggers such as the UCLA Miniscope v3 Wireless do not require data-acqusition hardware.
..
    ****
    ONIX
    ****

    ONIX is the data acquisition hardware designed by Open Ephys. It is compatible with a large array of Open Ephys hardware including electrophysiology headstages and miniscopes for Ca/ :sup:`2+` imaging. It supports several digital/analog GPIO, simultaneous data acquisition from up to two headstages/miniscopes, and many more features. To learn more about ONIX, refer to the `ONIX documentation <https://open-ephys.github.io/onix-docs/Hardware%20Guide/index.html>`__ and `ONIX store webpage <https://open-ephys.org/onix>`__. To learn how to acquire miniscope data with ONIX, refer to the ONIX *Quick Start Guide* for your respective miniscope:

    *   :doc:`UCLA Miniscope v4 </ucla-miniscope-v4/quick-start/onix1-quick>`

*************
Miniscope-DAQ
*************

..  image:: /_static/images/miniscope-daq.webp
    :alt:   image of miniscope-daq
    :align: center

The `Miniscope-DAQ <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__ is the data acquisition hardware developed by the UCLA Miniscope team for acquiring miniscope data. It accepts an external power supply for more power-intensive applications and plugs into a PC through a USB cable. It supports sync output, input trigger, and data acquisition from a UCLA Miniscope v4 or a MiniCAM. The Miniscope-DAQ is compatible with :ref:`overview/data-acq-software:Bonsai` and :ref:`overview/data-acq-software:Miniscope-DAQ-QT-Software`. To acquire miniscope or MiniCAM data with the Miniscope-DAQ, refer to the corresponding :doc:`/ucla-miniscope-v4/quick/index` and *User Guide* (coming soon). To learn more about the Miniscope-DAQ, refer to the `UCLA Miniscope v4 Wiki <https://github.com/Aharoni-Lab/Miniscope-v4/wiki/DAQ-Hardware>`__. 

Miniscope-DAQ Variants
======================

MiniDAQ
-------

..  image:: /_static/images/minidaq.webp
    :alt:   image of minidaq
    :align: center

..  todo:: remove background of and color-correct these photos, or take new photos

The MiniDAQ is a simplified, more compact, and more affordable version of the Miniscope-DAQ. It plugs directly into a PC through its on-board USB cable. It supports data acquisition from a single UCLA Miniscope v4 or a single MiniCAM. Unlike the Miniscope-DAQ, the MiniDAQ does not accept an external supply or support sync output or input trigger functions. The MiniDAQ is compatible with :ref:`overview/data-acq-software:Bonsai` and :ref:`overview/data-acq-software:Miniscope-DAQ-QT-Software`. To acquire miniscope or MinicCAM data with the MiniCAM, refer to the corresponding :doc:`/ucla-miniscope-v4/quick/index` and *User Guide* (coming soon).

.. :doc:`/ucla-miniscope-v4/user/data-acq/index`

NINscope-DAQ
------------

..  image:: /_static/images/ninscope-daq.webp
    :alt:   image of ninscope-daq
    :align: center

..  todo:: color-correct this photo so it matches miniscope-daq photo

The NINscope-DAQ is like the Miniscope-DAQ except the NINscope-DAQ is also compatible with the `NINscope <https://github.com/ninscope>`__. It accepts an external power supply for more power-intensive applications and plugs into a PC through a USB cable. It supports sync output, input trigger, and data acquisition from a single NINscope. The NINscope is compatible with `custom NINscope software <https://github.com/ninscope/Software/wiki/NINscope-software>`__ from the NINscope developers. To learn more about the NINscope, refer to the `NINscope hardware wiki <https://github.com/ninscope/Hardware/>`__ from the NINscope developers.
