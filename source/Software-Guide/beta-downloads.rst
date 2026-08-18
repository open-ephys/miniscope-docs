.. _beta_downloads:

####################################################################
Downloading the Beta
####################################################################

During the beta, the Open Ephys Miniscope V4 GUI is available as a direct download
instead of being published to NuGet or to the GitHub release page. Choose the corresponding link
below to download the GUI to run in headless mode, or to download the NuGet package locally so it
can be installed in Bonsai.

..  button-link:: https://gofile.me/7cMIw/lQe4F0dBX
    :color: primary
    :expand:

    Download the headless mode installation executable

..  button-link:: https://gofile.me/7cMIw/2yLWwRnWM
    :color: primary
    :expand:

    Download the NuGet package

*********************************************
Which File Do You Need?
*********************************************

..  list-table::
    :header-rows: 1
    :widths: 30 35 35

    *   - If you want to
        - Download
        - Then
    *   - Run the GUI on its own
        - ``MiniscopeV4Gui-Setup-<version>.zip``
        - Unzip the executable, and follow :doc:`/Software-Guide/installing-and-using-the-gui`.
    *   - Use the GUI inside your own Bonsai workflow
        - ``MiniscopeV4Gui-<version>.zip``
        - Unzip the package, then install it locally, as described below.

To run the GUI in headless mode, the executable is the only thing you need: the package is bundled
inside it, so you do not need the ``.nupkg`` as well.

Take the ``.nupkg`` only if you already work in Bonsai and want the GUI available in
your own environment alongside your other packages. See
:doc:`/Software-Guide/custom-workflows` for what you can do with it once installed.

*********************************************
Installing the NuGet Package in Bonsai
*********************************************

A ``.nupkg`` file cannot be installed from the Bonsai package manager the usual way,
because it is not on a package feed. Instead, point Bonsai at the folder you
downloaded it into and install from there. The `Installing a Local NuGet Package in
Bonsai
<https://github.com/open-ephys/wiki/wiki/Installing-a-Local-Nuget-Package-in-Bonsai>`__
article in the Open Ephys Wiki walks through it.

..  note::

    This page describes the beta only. Once the GUI is released, it will be published
    to NuGet and installable from the Bonsai package manager like any other package,
    and this page will go away.
