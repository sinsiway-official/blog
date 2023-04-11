---
title: "Linux"
linkTitle: "Linux"
weight: 1
---

## System Requirements
### Operating System
This program runs on Linux 64Bit operating systems.
### Kernel Version
To run this program, a Linux-based operating system with kernel version 2.6.32 or higher is required.
### Compiler
To compile this program, GCC compiler version 4.4.7 or higher is required.

## Library and Header File Download
To use this program, download the "libpcapi.so" library file and the "PcAPIL.h" header file.

## Library Installation
The library can be installed in two paths: the system library path and the custom library path. Typically, the custom library path is used for installation.

## Installing in the System Library Path
To make the "libpcapi.so" file available globally on the system, it can be installed in the /usr/lib64 directory as follows:

Open a terminal as root and download the "libpcapi.so" file.
Copy the downloaded file to the /lib or /lib64 directory:
shell
Copy code
```bash
$ sudo cp libpcapi.so /usr/lib64 
```
Change the file permission:
```bash
$ sudo chmod 755 /usr/lib64/libpcapi.so
```
Installing in the Custom Library Path
Alternatively, the "libpcapi.so" file can be installed in the custom library path depending on the application's execution environment:

Copy the "libpcapi.so" file to the directory where the application executable is located:
```bash
$ cp libpcapi.so /usr/local/lib64
```
Add the path where the library file is located to the LD_LIBRARY_PATH environment variable:
```bash
$ export LD_LIBRARY_PATH=/usr/local/lib64
```
Header File Installation
Depending on the application's execution environment that uses the "libpcapi.so" file for compilation, the "PcAPIL.h" header file can be installed and used. The path can be customized to the user's environment:
```bash
$ cp PcAPIL.h /usr/local/include
```