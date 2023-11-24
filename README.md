# learninglinux
This is a Markdown file that contains notes during my journey of learning Linux.

## Introduction to Linux Families
### RedHat Family Systems - ReHat Enterprise Linux (Fedora, CentOs) 

- Fedora serves as an upstream testing platform.
- CentOS is a close clone of REL
- Intelx86, ARM, Itanium, PowerPC
- yum package manager
- Widely used by enterprises

### SUSE Family Systems 

- SLES is upstream for openSUSE
- RPM-based zypper package manager
- YaST for sytem adminn opurposes
- Widely used in retail

### Debian Family Systems 

- Debian family is upstream fo Ubuntu
- DPKG-based APT package manager
- Widely used for cloud deployments
- GNOME-based but differ visually

There are 3 major Linux families as mentioned above.
RedHat, SUSE, & Debian


## Linux Philosophy and Concepts

Kernel - Glue between hardware and applications (considered the brain of the Linux operating system).
*eg. Linux kernel* ![Screenshot 2023-11-18 at 1.33.32 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/958e4ce8-56fd-45f6-a68c-2f268d291350)


Distribution - Collection of software making up a Linux-based system. *eg. RHEL, Fedora, Ubuntu, and Gentoo.*
![Screenshot 2023-11-18 at 1.34.12 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/4bf7059a-d46f-405c-bd7a-b98d0e0aca2f)


Boot Loader - Program that boots the operating system. *eg. GRUB & ISOLINUX.*
![Screenshot 2023-11-18 at 1.39.07 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/f78b1a77-cc88-4634-a803-c8974c368858)


Service - Program that runs as a background process. *eg. httpd, bfsd, ftpd, and named.*
![Screenshot 2023-11-18 at 1.39.30 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/87b428fe-2b64-499f-8cbd-095c9907a01a)


Filesytems - Method for storing and organizing files. *eg. xt3, ext4, FAT, XFS, and Btrfs*
![Screenshot 2023-11-18 at 1.40.00 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/f2005376-1ef9-4435-8993-388e8df15460)


X Window system - Graphical subsystem on nearly all Linux systems.
![Screenshot 2023-11-18 at 1.47.39 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/ae215cf7-7e74-4ddf-945b-d13c0dd23fdc)


Desktop Environment - Graphical user interface on top of the operating system. *eg. GNOME, KDE, Xfce, and Fluxbox.*

Command line - Interface for typing commands on top of the operating system.

Shell - Command line interprator that interprets the command line input and instructs the operating system to perform any necessary tasks and commands. *eg. bash, tcsh, and zsh.*

### Linux Distrubtions

A distribution consists of a kernel and other software tools for file related operations, user management, and software package managment. Each of these tools provide a part of the complete system.

![Screenshot 2023-11-18 at 1.28.48 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/412216f0-3e3c-4763-9ddc-3829fe56a2b1)

![Screenshot 2023-11-18 at 2.04.06 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/7d2b331f-1e33-422c-a14b-9d69e82e54e0)

### Sevices Associated with Linux Distributions

Ubuntu and Fedora are widely used by developers and used for educational content/purposes.
- Linus borrows from UNIX
- Linux accesses features through files
- Linux is a multitasking OS
- Terms: kernel, istribution, boot loader,  etc.
- Linux distro includes kernel and tools


## Linux Basics and System Startup

### BIOS: The First Step

BIOS = Basic Input/ Output System

Power On > BIOS > Initializes the screen and keyboard and tests the main memory.

Also called POST. Power On, Self Test

### Master Boot Record (MBR) and Boot Loader

Power On > BIOS > MBR (also known as first sector of Hard Disk) > Boot Loader(*eg. GRUB*) > Kernel (Linux OS) > Initial RAM disk - initramfs image

Master Boot Record = Partition 1 (bootable), Partition 2, Partition 3

![Screenshot 2023-11-18 at 2.17.25 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/45943ddb-9516-4c99-b994-9f8ba9341e4a)

The Bootloader is responsible for loading the Kernel image and the initial RAM disk or file system into memory.

### Boot Loader In Action

The Boot Loader has two distinct stages.

For BIOS method, the boot loader resides at the First Sector of the Hard disk aka MBR.
size MBR = 512 bytes
In this stage the boot loader examines the partition table and finds a bootable partition. Once it finds a bootable partition, it then searched for the second stage boot loader aka GRUB and loads it into RAM.

For systems EFI/UEFI method, reads its boot manager data to determine which uefi application to launch and from where. The firmware then launches the UEFI application aka GRUB as defined in the boot entry
in the firmware's boot manager.

The second stage boot loader resides under /BOOT. AFter seleting the OS, the bootloader loads the kernel of the selected OS into RAM and passes control to it. The kernels are almost always compressed, then have to uncompress as its first job.
Afterwards it will check and analyze system hardware and intialize any hardware device drivers built into the kernel.

### Inital RAM Disk

Inital RAM disk - initramfs

![Screenshot 2023-11-18 at 2.34.54 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/1b562181-d252-4483-af33-5d023075b5c8)

### Text-Mode Login

Near the end of the boot process, init starts a number of text-mode login prompts.
These enable you to type your username followed by your password and to evenutally get a command shell.
Ususally the default command shell is bash.

### The Linux Kernel

The bootloader loads the kernel and the initial Rm based file system into memory so it can be used directly by the kernel. When the kernel is loaded in RAM and it immediately initializes and configures the cpus memory and it also configures all hardware attached to the system. This includes all processes, IO subsystems, storage, and more. Kernel also loads necessary user space applications.

### /sbin/init and Services

Once the kernel has set up all its hardware and mounted to root file system.
The kernel runs the ```/sbin/init``` which is the parent process.
This becomes the inital process which then starts other processes to get the system running.
Most processes trace their origins back to ```init```. Exceptions include the kernel processes.
Kernel processes are started by the kernel directly and their job is to manage internal operating system details.

![Screenshot 2023-11-18 at 9.22.29 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/b8688d13-7fd5-4eba-a3e5-a6bccc67a38a)


Besides starting the system ```init``` is responsible for keeping the system runnning and for shutting it down cleanly. ```Init``` must act as necessary as a manager for all non-kernel processes. It cleans up after them upon completion, and restarts user login sefvices as needed when users login/logout.

### Systemd

### Linux Filesystem Basics

Filesystems supported by Linux:
- Conventional disk filesytstems
  (ext3, ext4, XFS, Btrfs, JFS, NTFS, vfat, etc.)
- Flash storage systems
  (ubifs, jffs2, yaffs, etc.)
- Database filesystems
- Special purpose filesystems
  (procfs, sysfs, tmpfs, squashfs, debugfs, etc.)

### Partitions and Filesystems

A Partition is a fiscally contiguous section of a disk or what appears to be so in many advanced setups.
Filesystem is a method of storing or finding files on a hard disk, usually in a partition.

Think of a partition as a container where a filesystem resides. Sometimes a filesystem can become larger than a partition.

![Screenshot 2023-11-18 at 10.14.37 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/2cdb8eeb-bf8a-4495-98d2-9877b58ff793)

### The Filesystem Hierarchy Standard

Linux systems store their important files according to a standard layout called the filesystem hierarchy standard. 
This is used to ensure that users, admins, and devs can move between distributions without having to relearn how the system is organized.

ALL LINUX FILE SYSTEMS ARE CASE SENSITIVE!
eg. /boot
    /Boot
    /BOOT

The above example represents three different directories/folders.

### Linux Distribution Installation

Questions to ask before deciding on a distribution.

**_What is the main function of the system?_**

**_What types of packages are important to the organization?_** *eg. web server, word processing, etc.*

**_How much hard disk space is required and how much is available?_** *eg. When installing Linux on an embedded device, space is usually constrained.*

**_How often are packages updated?_**

**_How long is the support cycle for each release?_** *eg. FTS releases have long-term support*

**_What hardware are you running on_** *eg. Could be x86 ARM or PPC*

**_Do you need long-term stability?_**

**_Can you accept or need a more volatile cutting edge system running the latest software?_**

![Screenshot 2023-11-19 at 1.36.04 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/e3582a80-1e86-4edc-bcc0-ab3da7616a2c)


### Linux Installation: Planning

The partiton layout needs to be decided at the time of installation. It can be difficult to change later.
Nearly all installers provide a reasonable default layout with either all space dedicated to normal files on one big partition, and a smaller swap partition, or with a separate partitions for some space sensitive areas like ```/home``` and ```var```.

### Linux Installation: Software Choices

All installations include the minimum software for running a Linux distribution. Most installers provide options for adding categories of software common applications. *eg. Firefox web browser adn Libre Office Suite* 

Like other operating systems Linux distributions are provied on removable media such as USB drives, CDs, DVDs.
Most Linux distributions also support booting a small image and downloading the rest of the system over the network.
These small images are usable on media or as Network boot images in which case it is possible to perform and install without using any local media.

### Linux Installation: The Process

The installation process is similar for all distributions.
After booting from the installation media, the installer starts and asks questions about how the system should be setup. 

These questions are skipped if an automatic installation file is provided, then the installation is performed.
Finally the cpu reboots into the newly designed system.

### Linux Installation: The Warning



## Graphical Interface

## System Configuration from the Graphical Interface

## Common Applications

## Command Line Operations

## Finding Linux Documentation

## Processes

## File Operations

## Text Editors

## User Environment

## Manipulating Text

## Network Operations


## Basic Commands

# Linux Commands - Day 1

  print working directory = pwd

  ```tree``` displays the order of the directories.
  ```sudo apt``` or ```sudo snap``` is used for installations or updates/upgrades.

  login using ssh 

  To delete (or remove) a directory, use ```rmdir``` if the directory is empty or ```rm -r``` if there still any files or other directories inside of it.

  ```cd ~``` redirects you back to home directory. or ``` cd /home```

  ```cd ..``` redirects you to the parent folder in the directory hierarchy.

  ``` cd $HOME``` take you to your home directory.

  ``` cd $OLDPWD``` takes you to your previous pwd

  ```ls``` lists files in the directory.

  ```mkdir``` is to create a directory. name the file after creating it. ```mkdir test``` will result in TEST as a new directory.

  ```rmdir``` to remove directory.

  ```touch``` is to create a new empty file.

  ```rm``` is to remove a file in directory. ```rm -r``` deletes a directory and the files it contains.

  ```mv``` to move the file in directory. Also used to rename a file.

  ``` cp ``` is to coopy file then name the second file.
  
  ```cp my first-file my-second-file``` for example


  ```tldr ls``` basically reads the manual to you in simple terms.
  
## Navigating the Command Line

``` nmap``` is a port scanner. It allows us to scan a target system to see what ports are open , what services are running on it, which is a great way to get an image of what the target looks like.(You can't hack the system if you don't know what it is.) AKA Network Exploration tool and security/port scanner.

```locate``` can be used to find a specific file in many folders/directories. 
```find``` simliar to locate. find will find anything you're looking for. not just binaries. can find files by name, size, etc. can aso filter using ```grep```.

```whereis``` checks all binary folders aka ```bin/sbin``` for the specific file. Shows you where the binary is that holds that file.
*eg.*  ```ubuntu@ouroboros:/$ whereis snap
snap: /usr/bin/snap /usr/share/man/man8/snap.8.gz```


```which``` shows where the specific files binary is AMONG the directories in the $PATH variable aka ```echo $PATH```.

```timedatectl``` shows current timezone and date.

``` hostnamectl``` show the hostname with all relevant information.

``` sudo hostnamectl set-hostname {new hostname}``` script to set new hostname for environment.

``` timedatectl set-timezone {timezone}``` script to set new timezone.

- Check the current system clock time:
  
```timedatectl```

- Set the local time of the system clock directly:
  
```timedatectl set-time "{{yyyy-MM-dd hh:mm:ss}}"```

- List available timezones:
  
```timedatectl list-timezones```

- Set the system timezone:
  
```timedatectl set-timezone {timezone}```

- Enable Network Time Protocol (NTP) synchronization:
  
```timedatectl set-ntp on```

## Linux Directories

![IMG_4507.jpg](https://github.com/pythonperk/learninglinux/assets/86713638/1d9aa330-8563-4f71-a09e-80737c001e5a)


