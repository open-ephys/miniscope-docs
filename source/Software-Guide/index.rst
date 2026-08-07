.. _software_guide:

#########################
Software Guide
#########################

.. toctree::
    :hidden:

    interface
    recording
    custom-workflows

The **Miniscope GUI** is the recommended way to acquire data from the UCLA Miniscope v4
and the Miniscope DAQ. It is a free, open-source, Windows application developed by Open
Ephys that gives you everything needed to run an imaging session (live image and
orientation display, hardware control, commutation, and recording to file) without
writing or editing a workflow.

..  TODO(media): screenshot — replace with the GUI mid-acquisition, showing live image data,
..      running Euler angle traces, and a few console messages. The current capture is of an
..      idle, disconnected GUI, so the landing page never shows the software actually working.

..  image:: /_static/images/miniscopev4_gui/miniscope-gui-layout.png
    :alt:   the Miniscope GUI window
    :align: center
    :width: 100%

|

..  grid:: 3
    :gutter: 3

    ..  grid-item-card:: Interface Reference
        :link:      /Software-Guide/interface
        :link-type: doc
        :class-card: intro-card

        Every control in the status bar, control panel, data panel, and console.

    ..  grid-item-card:: Recording Data
        :link:      /Software-Guide/recording
        :link-type: doc
        :class-card: intro-card

        Recording modes, the files each recording produces, and configuration files.

    ..  grid-item-card:: Custom Bonsai Workflows
        :link:      /Software-Guide/custom-workflows
        :link-type: doc
        :class-card: intro-card

        Build acquisition workflows from Bonsai operators when you need to go beyond
        the GUI.

..  note::

    The Miniscope GUI is a Bonsai workflow. It is built on the same
    ``OpenEphys.Miniscope`` operators used in the :doc:`custom workflow tutorials
    </Software-Guide/custom-workflows>`, wrapped in a `Dear ImGui
    <https://github.com/ocornut/imgui>`__ interface and shipped with its own launcher, so
    that no Bonsai knowledge is needed to use it.

*********************************************
Installation
*********************************************

*Requirements: 64-bit Windows 10 or 11, and an internet connection for the first launch.*

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

    ..  TODO(media): screenshot — the Windows SmartScreen "Windows protected your PC" dialog,
    ..      with a second capture after clicking *More info* showing the *Run anyway* button
    ..      and the publisher line.
    ..      Suggested file: /_static/images/miniscopev4_gui/install-smartscreen-warning.png

#.  At the end of installation, the setup downloads Bonsai and the acquisition packages
    the GUI depends on into the install folder. This step needs an internet connection
    and can take a few minutes.

#.  The installer creates a **UCLA Miniscope V4 GUI** shortcut on your Desktop and in the
    Start Menu.

..  note::

    The Miniscope DAQ works over USB, so make sure the operating system's USB settings are
    configured to avoid suspending the device due to power management. See the
    :ref:`quickstartguide` for details on connecting the hardware and verifying that
    Windows recognizes the board.

..  tip::

    The install folder is entirely self-contained. To uninstall, use *Add or remove
    programs*; to reset the GUI to a clean state, uninstall it and delete
    ``%LOCALAPPDATA%\MiniscopeV4Gui``.

*********************************************
Launching the GUI
*********************************************

Launch the GUI from the Desktop or Start Menu shortcut. The shortcut runs a small
PowerShell launcher (``Run.ps1``) that starts the bundled Bonsai runtime with the
``MiniscopeGui.bonsai`` workflow and no editor window, so the GUI is the only window you
see.

On startup the GUI restores the settings from the last session, which are kept in
``default_minscopev4_config.yml`` in the install folder. Closing the GUI window stops
acquisition and shuts the workflow down.

*********************************************
Starting Acquisition
*********************************************

..  note::

    Connect the Miniscope to the Miniscope DAQ and the DAQ to your computer before
    launching the GUI, following the :ref:`quickstartguide`.

#.  **Choose the Miniscope.** Set ``Index`` in the status bar to the index of your
    Miniscope, in the order the cameras are detected by the computer. ``0`` is the first
    camera; if you only have one Miniscope DAQ connected and no other cameras, ``0`` is
    usually correct.

#.  **Start acquiring.** Click **Start Acquisition**. The *Image* tab begins showing live
    frames, and the acquisition timer in the status bar starts counting.

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

    ..  TODO(media): animated gif — one clip per setting, showing the live image responding
    ..      as the slider or dropdown is dragged.
    ..      Suggested files: /_static/images/miniscopev4_gui/gui-{focus,led,gain,fps}-demo.webp

#.  **Check for saturation.** Switch to the *Saturation* tab to see which pixels exceed
    the intensity threshold, and to the *Histogram* signal tab to see the overall
    distribution of pixel intensities. Lower the LED brightness or the sensor gain if a
    large fraction of the image is saturated.

    ..  TODO(media): animated gif — the Saturation tab beside the Histogram tab while LED
    ..      brightness is raised, so the highlighted pixels spread and the histogram piles up
    ..      against the right edge.
    ..      Suggested file: /_static/images/miniscopev4_gui/gui-saturation-demo.webp

#.  **Check the orientation data.** Check the *Euler Angles* signal
    tab and rotate the Miniscope. The traces should respond immediately. This confirms
    the on-board IMU is streaming data, which is also what drives automatic commutation.

    ..  TODO(media): animated gif — a hand rotating the Miniscope beside the Euler Angles
    ..      traces responding. A split view showing both the physical scope and the plot is
    ..      ideal; the existing quaternion-demo.webp is the model.
    ..      Suggested file: /_static/images/miniscopev4_gui/gui-euler-angles-demo.webp

#.  **Record.** In the **Recording** section at the bottom of the Control Panel, click
    ``...`` to choose a folder and base file name, then click **Record** (or press
    :kbd:`Ctrl+R`). See :doc:`/Software-Guide/recording` for the recording modes and the
    files produced.

#.  **Stop.** Click **Stop Recording**, then **Stop Acquisition**.

*********************************************
Keyboard Shortcuts
*********************************************

..  list-table::
    :header-rows: 1
    :widths: 20 80

    *   - Key
        - Action
    *   - :kbd:`Ctrl+R`
        - Start or stop recording (arm or disarm in Trigger mode).
    *   - :kbd:`Space`
        - Freeze or resume the live display, without affecting acquisition or recording.
    *   - :kbd:`C`
        - Capture the current image to the data folder.
    *   - :kbd:`E`
        - Expand the image to fill the window, or collapse it back.
    *   - :kbd:`R`
        - Reset the accumulated max projection.
    *   - :kbd:`O`
        - Toggle the live overlay on the reference image.
    *   - :kbd:`Shift` + mouse wheel
        - Step the time-series timebase up or down.
    *   - :kbd:`Ctrl+C`
        - Copy the selected console messages to the clipboard.

Shortcuts are ignored while the cursor is in a text field.

*********************************************
Other Acquisition Software
*********************************************

..  grid::

    ..  grid-item-card:: Bonsai Package OpenEphys.Miniscope
        :link-type: doc
        :link: /Software-Guide/custom-workflows
        :class-card: intro-card
        :img-top: /_static/images/bonsai-logo.png
        :img-alt: bonsai logo
        :class-img-top: software-card-img
        :columns: 5

        Acquire data from the Miniscope DAQ in Bonsai, a highly extensible visual programming
        language that enables collected data to interface with other hardware in real-time, and
        perform online software processing and experimental control with supported tools. The
        ``OpenEphys.Miniscope`` package is the package the Miniscope GUI is built on, and it is
        developed by Open Ephys.

        *Click to start browsing the workflow tutorials.*

    ..  grid-item-card:: Miniscope-DAQ-QT-Software (deprecated)
        :link-type: url
        :link: https://github.com/Aharoni-Lab/Miniscope-DAQ-QT-Software/wiki
        :class-card: intro-card
        :img-top: /_static/images/miniscope-logo.png
        :img-alt: Miniscope-DAQ-QT-Software logo
        :class-img-top: software-card-img
        :columns: 5

        The original software developed by the UCLA Miniscope Team that enables data
        acquisition from the Miniscope v4 and the MiniCAM via the Miniscope DAQ, as well
        as webcams.

        This software is deprecated and not supported by Open Ephys. It has been updated to
        support commutation.

        *Click to navigate to its documentation site.*
