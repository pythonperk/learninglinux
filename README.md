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
[Screenshot 2023-11-18 at 1.39.07 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/f78b1a77-cc88-4634-a803-c8974c368858)


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

Inital RAM dsik - initramfs

![Screenshot 2023-11-18 at 2.34.54 PM.png](https://github.com/pythonperk/learninglinux/assets/86713638/1b562181-d252-4483-af33-5d023075b5c8)



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
