---
title: "Installation"
linkTitle: "Installation"
weight: 10
---

**"libpcapi.so"** is a C/C++ encryption library developed by Sinsiway. This library operates in the GCC compiler environment and can perform encryption and decryption functions on data. To do so, it obtains a session from the Petra Cipher Key Server and uses the encryption key received from the key server to perform operations.

**"libpcapi.so"** can be used as a dynamic library in applications that require encryption functionality. To use the library, the application needs to link to the "libpcapi.so" library file.

The library's initialization function uses a configuration file to set the key server information and provides a function to specify the location of the configuration file. This allows users to initialize the library by specifying the location of the configuration file at the time of application execution.

"libpcapi.so" is an encryption library that can be used in various applications.