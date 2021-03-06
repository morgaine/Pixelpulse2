## Pixelpulse2

![Windows Status](https://ci.appveyor.com/api/projects/status/32r7s2skrgm9ubva?svg=true)
![OSX Status](https://img.shields.io/travis/analogdevicesinc/Pixelpulse2.svg?label=OSX)
[![License](https://img.shields.io/badge/license-MPL-blue.svg)](https://github.com/analogdevicesinc/Pixelpulse2/blob/master/LICENSE)

Pixelpulse is a powerful user interface for visualizing and manipulating signals while exploring systems attached to affordable analog interface devices, such as Analog Devices' ADALM1000 or the Nonolith Labs' CEE.

Fully cross-platform using the Qt5 graphics toolkit and OpenGL accelerated density-gradiated rendering, it provides a powerful and accessible tool for initial interactive explorations.

Intuitive click-and-drag interfaces make exploring system behaviors across a wide range of signal amplitudes, frequencies, or phases a trivial exercise. Just click once to source a constant voltage or current and see what happens. Choose a function (sawtooth, triangle, sinusoidal, square) - adjust parameters, and make waves.

Zoom in and out  with your scroll wheel or multitouch gestures (on supported platforms). Hold "Shift" to for Y-axis zooming.

Click and drag the X axis to pan in time.

### Screenshot

![Screenshot of PP2 on Windows 7](http://itdaniher.com/static/pp2_win7.png "Pixelpulse on Windows 7")

### Getting Pixelpulse2

#### Easy

* OSX - Navigate to the [releases](https://github.com/analogdevicesinc/pixelpulse2/releases) and collect the latest `pixelpulse2-bundled.dmg.zip` package. The latest testing build is available from [Travis-CI](http://pixelpulse2nightly.s3-website-us-east-1.amazonaws.com/pixelpulse2.dmg).
* Windows - For a testing build, download the dependency package and the latest binary build from [appveyor](https://ci.appveyor.com/project/analogdevicesinc/pixelpulse2/build/artifacts). For an official release build, navigate to releases and collect the latest pixelpulse2-setup.exe.
* Linux - Either build from source (below) or navigate to the releases and collect the latest .deb or .tgz file for your architecture. Install or extract as appropriate.

#### Advanced

To build from source on any platform, you need to install a C++ compiler toolchain, collect the build dependencies, setup your build environment, and compile the project.

If you have not built packages from source before, this is ill-advised.

* Install [LibUSB](http://libusb.info/).
 * Install using your package manager - "libusb" on OSX Homebrew, "libusb-1.0-0-dev" on modern Debian/Ubuntu distributions, "libusb-devel" on Fedora/CentOS.
 * Build from source using the [appropriate branch](https://github.com/kevinmehall/libusb/tree/hp) if a version of LibUSB with HotPlug support for your platform is not available. (Windows, Debian Wheezy)
* Install Qt5.4.
 * On most Linux Distributions, Qt5 is available in repositories. The complete list of packages required varies, but includes qt's support for declarative (qml) UI programming, qtquick, qtquick-window, qtquick-controls, and qtquick-layouts.
 * Binary installers are available from [the Qt project](http://qtmirror.ics.com/pub/qtproject/development_releases/qt/5.4/5.4.0-rc/) for most platforms.

To build / run on a generic POSIX platform

    git clone --recursive https://github.com/signalspec/pixelpulse2
    cd pixelpulse2
    mkdir build
    cd build
    qmake -qt=qt5 ..
    make

To build / install for Debian, from the `pixelpulse2` directory:

    dh_make -p pixelpulse2_0.8 -s -c blank --createorig
    dpkg-buildpackage
    sudo dpkg -i ../pixelpulse2_0.1-1_i386.deb

