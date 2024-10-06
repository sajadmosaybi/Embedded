# Embedded Linux Yocto project
## Yocto Introduction
### What is Yocto?
**The Yocto Project (YP) is an open source collaboration project that helps developers create custom Linux-based systems regardless of the hardware architecture.**
https://www.yoctoproject.org/

### Why to use Yocto?

* To configure the Linux according to our specs. 
* The Image contains what we need.
*  No extra packages. 
* Small Image Size.
### Host PC Requirements

* Minimum 50 GB free space
* Minimum 4 GB 
#### Supported Linux Distros

- Ubuntu 18.04 (LTS)
- Ubuntu 20.04 (LTS)
- Ubuntu 22.04 (LTS)
- Fedora 34
- Fedora 35
- AlmaLinux 8.5
- Debian GNU/Linux 10.x (Buster)
- Debian GNU/Linux 11.x (Bullseye)
- OpenSUSE Leap 15.3

**I am using Ubuntu 24.04 (LTS)**
### Which Target Hardware is being used?

We are using here **raspberry pi and STM32MP157**.
### Setup Host PC

#### Editor

* OS: Ubuntu 24.04 (LTS)

* Using VSCode

  ```bash
  # Installing VS code using CLI
  sudo apt update
  sudo apt install snapd
  sudo snap install --classic code
  ```

#### Install required packages

```bash
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev pylint3 xterm python3-subunit mesa-common-dev zstd liblz4-tool

```
### Building Image

#### What is Poky?

Poky is a *reference distribution* of the Yocto Project®. It contains the OpenEmbedded Build System (BitBake and OpenEmbedded Core) as well as a set of metadata to get you started building your own distro. 
#### Cloning Poky

Create a project folder and clone the poky in it.

```bash
mkdir yocto_tutorial
cd yocto_tutorial
git clone git://git.yoctoproject.org/poky -b kirkstone
```

#### Initialize Build Environment

```bash
cd poky
source oe-init-build-env
```

Now we are in **build** folder, there are some folders and files, right now the important is **conf** folder.

In terminal there are multiple image options

#### Create Source Folder (not necessary, but very much recommended)

From build folder run the following command

```bash
mkdir ../../sources
```

####  Make Changes in local.conf

* Change Machine

* Change source path

* Set following

* * RM_OLD_IMAGE = "1"

  * INHERIT += "rm_work"

* Save

We will discuss the content of **local.conf** file  in another chapter.

#### Build Image

Execute the following command from build folder

```bash
bibake core-image-full-cmdline
```
#### Image File

Go to the **tmp** folder, my **tmp** folder is in my source folder, that we created before

I am opening a new terminal and going to the image folder.

```bash
cd ../../sources/tmp/deploy/images/beaglebone-yocto
```

Here is our Image : **core-image-full-cmdline-Raspberry.wic**

### End

In the next chapter I will show you how to flash the Image in beaglenone black and how to boot it.
