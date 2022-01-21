# Updated Instructions

piclone is an app for the Raspberry Pi that makes it easy to backup the SD card.

The instructions below this section are the original instructions from [the original repository](https://github.com/raspberrypi-ui/piclone).

The instructions in _this_ section are for installing piclone on **Ubuntu Desktop 21.10 64-bit arm64 architecture**.

Install dependencies:

- `sudo apt update`
- `sudo apt upgrade -y`
- `sudo apt build-essential libgtk2.0-dev libgtk-3-dev intltool uuid git curl`

Clone this respository:

- `git clone https://github.com/christroutner/piclone`
- `cd piclone`

Create the configure script:

- `./autogen.sh`

Configure the install:

- `./configure`

Make the app:

- `make`

Install the app:

- `sudo make install`

To run piclone, insert an SD card reader into the RPi's USB. You may need to format the SD card on a different computer, in order for the RPi to recognize it.

Run piclone:

- `sudo dbus-launch piclone`

That will launch the GUI.

---

This is an application which allows the SD card inserted into the Pi to be copied to one in a connected USB reader.

# How to build

1. Install dependencies

The dependencies of any Debian project are listed in the "Build-Depends" section
of the file named "control" in the "debian" subdirectory of the project.

If the project has already been released into apt, then the build dependencies
can be automatically installed using the command "sudo apt build-dep <package-name>".

2. Prepare project

To create the "configure" file and prepare the project directory, use the command
"./autogen.sh" in the top directory of the project.

If this file is not present, then instead use the command "autoreconf -i -f"
followed by the command "intltoolize -c --automake --force", both in the top directory
of the project.

3. Configure

To configure the make system, use the command "./configure" in the top directory of
the project. This will by default set the project for installation in the /usr/local tree,
which will not overwrite a version which has been installed from apt.

If you wish to overwrite a preinstalled version in the /usr tree, supply the arguments
"./configure --prefix=/usr --libdir=/usr/lib/<library-location>" to the configure command.
On a 32-bit system, <library-location> should be "arm-linux-gnueabihf".
On a 64-bit system, <library-location> should be "aarch64-linux-gnu".

4. Build

To build the application, use the command "make" in the top directory of the project.

5. Install

To install the application and all required data files, use the command "sudo make install"
in the top directory of the project.
