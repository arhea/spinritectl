# SpinRite VirtualBox Setup and Configuration
This guide walks you through creating a VirtualBox Virtual Machine to run SpinRite. It also discusses mounting physical drives into the VM.

_SpinRite is a registered trademark of [Gibson Research Corporation](https://www.grc.com) operated by [Steve Gibson](https://twitter.com/SGgrc)._

## Guide
This guide will walk you through getting started with SpinRite and running the virtual machine using VirtualBox.

### Install VirtualBox
Follow the instructions on [VirtualBox's website](https://www.virtualbox.org/wiki/Downloads) to install VirtualBox and the VirtualBox Extensions.

```bash
# macOS
brew cask install virtualbox

# Debian/Ubuntu
apt install virtualbox virtualbox-ext-pack
```

### Purchase and Download a Copy of SpinRite
Visit GRC's website to [purchase and download](https://www.grc.com/cs/prepurch.htm) your copy of SpinRite.

### Create A Bootable ISO of SpinRite
SpinRite is downloaded as a `.exe` file. In order to create a bootable ISO for our VM we need to run SpinRite.

#### Windows
On Windows simply run the `SpinRite.exe` and click "Create ISO or IMG File" then "Save a Boot Image File". Place the `SpinRite.iso` in `~/SpinRite/SpinRite.iso`. `spinritectl` expects the file to be located here.

#### macOS or Linux

On Mac OS or Linux you will need to install [Wine](https://www.winehq.org/) in order to run `SpinRite.exe`. Once you have Wine installed, run the following command:

```bash
# macOS
brew install wine

# Debian/Ubuntu
apt install wine
```

```bash
wine ~/Downloads/SpinRite.exe
```

Then click "Create ISO or IMG File" then "Save a Boot Image File". Place the `SpinRite.iso` in `~/SpinRite/SpinRite.iso`. `spinritectl` expects the file to be located here.

### Running the Virtual Machine
I have created a simple command line utility to get SpinRite up and running quickly.

```bash
# create and configure the virtual machine
sudo ./spinritectl init

# attach drive
sudo ./spinritectl attach <disk name>

# start the virtual machine
sudo ./spinritectl start

# save the world and your hard drive too

# stop the virtual machine
sudo ./spinritectl stop
```

## FAQs

### Does `spinritectl` have any dependencies?
Not directly. You can use tools like Homebrew to make it easier to install Virtualbox and Wine.

### Can I Install `spinritectl`?
If you want to add `spinritectl` as a top level command on your terminal. Simply symlink the file in this directory to a folder in your path.

```bash
ln -sf ./spinritectl /usr/local/bin/spinritectl
```

### Permissions Issues
If you run into permissions issues run through the guide as `root`. This will create an entirely new instance of your VM with the root user who has access to disks directly.
