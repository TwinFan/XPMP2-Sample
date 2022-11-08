XPMP2 Sample Plugin
=========

[![Build all Platforms](https://github.com/TwinFan/XPMP2-Sample/actions/workflows/build.yml/badge.svg)](https://github.com/TwinFan/XPMP2-Sample/actions/workflows/build.yml)

This is a fully functional sample implementation and _Public Template_
that you can use to play with features of the [XPMP2 library](https://github.com/TwinFan/XPMP2)
and as a starting point for your own implementations.
[Read how to create a repo based on a public template.](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)

I am also using XPMP2-Sample as a testbed for new features, so the implementation
is regularly built, tested, and sometimes even enhanced to make use of
latest features.

Find [developer's documentation on XPMP2 on GitHub pages](https://twinfan.github.io/XPMP2/).

Please note that `XPMP2-Sample` includes `XPMP2` as a submodule,
so you need to checkout those, too, e.g. on the command line by doing
```
git clone --recurse-submodules https://github.com/TwinFan/XPMP2-Sample
```

## Build ##

XPMP2-Sample can be build
- in Visual Studio or XCode IDEs,
- from the command line with `CMake`/`ninja`,
- cross-platform in a Docker environment,
- via GitHub Actions.

Please refer to
[XPMP2's Build documentation on GitHub](https://twinfan.github.io/XPMP2/Building.html)
for details.

The project is prepared to be built with FMOD sound support.
[See here](https://twinfan.github.io/XPMP2/Sound.html#building-xpmp2-with-fmod-sound-support)
how to build with sound support.

## Features ##

This plugin creates 3 planes, one with each of the available ways of using the XPMP2 library.
All planes move in a circle around a position 200m in front of the user's plane
(even if the user plane moves).
1. Subclassing `XPMP2::Aircraft` in `class SampleAircraft`,
   which is the recommended way for any new plugin. This plane flies
   highest, 100m above the user plane.
2. Subclassing the legacy `class XPCAircraft`. This plane flies in the middle,
   50m above the user plane.
3. Using direct C functions. This plane always rolls on the ground, no matter how
   high the user plane flies.

Three menu items are provided:

 1. "Toggle Planes" creates/removes the planes.
 2. "Toggle Visibility" shows/temporary hides the planes without destroying them.
 3. "Cycle Models" changes the CSL model used per plane.
     Also, it flips the visibility of labels in the map view...just for a change.

## Installation ##

The directory structure needs to look as follows:

```
XPMP2-Sample/
  lin_x64/
    XPMP2-Sample.xpl
  mac_x64/
    XPMP2-Sample.xpl
  win_x64/
    XPMP2-Sample.xpl
  Resources/
    CSL/         <-- install CSL models here
    Doc8643.txt
    MapIcons.png
    Obj8DataRefs.txt
    related.txt
```

The individual files under `Resources` listed above, like `Doc8643.txt`, are available
from `lib/XPMP2/Resources`.

For the plugin to work properly some CSL models are necessary in some folders
under `Resources`. All folders under `Resources` are scanned for
`xsb_aircraft.txt` files, so the actual structure underneath `Resources` does not matter.

For CSL models to be put under the `Resources/CSL` folder you may want to refer to
[LiveTraffic's detailed CSL model installation instructions](https://twinfan.gitbook.io/livetraffic/setup/installation/step-by-step#bluebell-csl-package-by-oktalist).