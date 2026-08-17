.. _installing_and_using_the_gui:

####################################################################
Installing and Using the GUI
####################################################################

*********************************************
Installation
*********************************************

*Requirements: 64-bit Windows 10 or 11, and an internet connection during installation.*

#.  Download the latest ``MiniscopeGui-Setup-<version>.exe`` installer from the
    `bonsai-miniscopev4-gui releases page
    <https://github.com/open-ephys/bonsai-miniscopev4-gui/releases>`__.

#.  Run the installer. It installs per-user into
    ``%LOCALAPPDATA%\MiniscopeV4Gui``, so no administrator rights are required.

    ..  note::

        This application is currently not code signed. As a result, Windows may display
        a "Windows protected your PC" or "Unknown publisher" warning the first time you
        run it. This is expected, even if you downloaded it from the project's official
        GitHub Releases page. To continue, click *More info*, verify that the correct
        program is trying to run, and click *Run anyway*.

        ..  image:: /_static/images/miniscopev4_gui/windows-smart-screen.png
            :alt:   Windows Defender SmartScreen when installing the GUI
            :align: center
            :width: 40%

#.  At the end of installation, the setup downloads Bonsai and the acquisition packages the GUI
    depends on. This step needs an internet connection and can take a few minutes.

#.  The installer creates an **Open Ephys Miniscope V4 GUI** shortcut on your Desktop and in the
    Start Menu.

..  note::

    The Miniscope DAQ works over USB, so make sure the operating system's USB settings are
    configured to avoid suspending the device due to power management. See the
    :ref:`quickstartguide` for details on connecting the hardware and verifying that
    Windows recognizes the board.

..  note::

    Avoid USB hubs, including the ones built into some laptops, docks, and monitors; they introduce
    the possibility of dropped frames, especially if anything else sharing the hub is also streaming
    high bandwidth information. Connect the Miniscope DAQ directly to a USB 3.0 port on the computer
    instead.

..  tip::

    To uninstall, use *Add or remove programs* and uninstall the Miniscope V4 GUI.

*********************************************
Launching the GUI
*********************************************

Launch the GUI from the Desktop or Start Menu shortcut.

On startup the GUI restores the settings from the last session, which are kept in
``default_miniscopev4_config.yml`` in the install folder. Closing the GUI window stops
acquisition and saves the current configuration to the same configuration file.

.. _headless_vs_custom_workflow:

Headless Mode vs. Custom Workflows
=====================================

The shortcut above launches the GUI **headless**: no Bonsai editor is visible, just the GUI window
itself. This isn't a separate version of the software; the GUI is itself a Bonsai workflow. The same
workflow can instead be embedded as a single node inside a custom Bonsai workflow of your own, and
it behaves identically whichever way it's launched: nothing about the GUI's own functionality
changes between the two.

What differs is extensibility. Headless mode gives you the whole GUI and nothing else.
Embedding it in a workflow lets you build around it. For example, running a behavior
camera in the same workflow so its feed displays in its own window alongside the GUI's. See
:doc:`/Software-Guide/custom-workflows` for how.

*********************************************
Starting Acquisition
*********************************************

#.  **Choose the Miniscope.** Set ``Index`` in the status bar to the index of your Miniscope, in the
    order the Miniscopes are detected by the computer. ``0`` is the first Miniscope; if you only
    have one Miniscope connected, ``0`` will be correct.

    ..  note::

        There is no way to tell which index corresponds to which physical Miniscope ahead of
        time; the GUI does not show a serial number or name for each one. If you have more
        than one connected, try each index in turn and check the incoming data once acquisition
        starts to see which Miniscope you've selected.

#.  **Start acquiring.** Click **Start Acquisition**. The *Image* tab begins showing live
    frames, and the acquisition timer in the status bar starts counting.

    ..  tip::

        If you are using a commutator, check **Auto Connect** in the *Commutator* section before
        starting to ensure the commutator is connected when acquisition starts. When **Auto
        Connect** is enabled, acquisition cannot start until a commutator is found.

#.  **Set up the optics.** In the *Control Panel* on the left, open the **Miniscope**
    section and adjust:

    :LED Brightness:    The excitation LED level, as a percentage of maximum current.
                        Start low and increase until the sample is visible; the
                        relationship between this value and radiance is non-linear.

    :Focus:             The electrowetting lens (EWL) adjustment around its nominal focal
                        plane, from -100% to 100%. Place the Miniscope roughly its working
                        distance from the sample first, then adjust.

    :Frame Rate:        Frames acquired per second.

    :Sensor Gain:       The image sensor's analog gain.

    :LED Trigger:       Turn on the LED when the selected DigitalIn pin is high. To keep the LED on
                        continuously, choose ``None``

    ..  raw:: html

        <center>
          <video width="362" height="258" controls muted>
            <source src="../_static/videos/miniscopev4-gui/control-panel-miniscope-settings.mp4" type="video/mp4">
          </video>
        </center>

#.  **Check for saturation.** Switch to the *Saturation* tab to see which pixels exceed
    the intensity threshold, and to the *Histogram* signal tab to see the overall
    distribution of pixel intensities. Lower the LED brightness or the sensor gain if a
    large fraction of the image is saturated.

    ..  raw:: html

        <center>
          <video width="700" height="674" controls muted>
            <source src="../_static/videos/miniscopev4-gui/miniscopev4-gui-saturation.mp4" type="video/mp4">
          </video>
        </center>

#.  **Check the orientation data.** Check the *Euler Angles* signal
    tab and rotate the Miniscope. The traces should respond immediately. This confirms
    the on-board IMU is streaming data, which is also what drives automatic commutation.

    ..  raw:: html

        <center>
          <video width="690" height="284" controls muted>
            <source src="../_static/videos/miniscopev4-gui/gui-euler-angles-demo.mp4" type="video/mp4">
          </video>
        </center>

#.  **Record.** In the **Recording** section at the bottom of the Control Panel, click
    ``...`` to choose a folder and base file name, then click **Record** (or press
    :kbd:`Ctrl+R`). See :doc:`/Software-Guide/recording` for the recording modes and the
    files produced.

#.  **Stop.** Click **Stop Recording**, then **Stop Acquisition**.
