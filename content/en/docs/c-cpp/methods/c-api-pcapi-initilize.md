---
title: "PcAPI_initialize → void"
linkTitle: "PcAPI_initialize"
weight: 2
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_initialize(char *info_file_path, char *credentials_pw);
```


### DESCRIPTION
The **PcAPI_initialize** function sets up the configuration file required to use the **libpcapi.so** library. The configuration file contains information such as the key management server settings and the credentials needed for authentication.

The **info_file_path** parameter of the function should include the full path and file name of the configuration file, while the **credentials_pw** parameter should contain the credentials password. This password should be the same as the one used when issuing the credentials value in the info_file_path file. If no password was used, an empty value ("") can be entered.

If the function is not called, the default read path is **"/var/tmp/.petra/petra_cipher_api.conf"**, and no password is used.

For detailed information, please refer to the "Installation Guide - Configuration File" section.

### RETURN VALUE
The function returns 0 upon success. 

If an error occurs, it returns an error code less than 0.

### ERRORS
[-30315](../../../error-codes/#-30315), [-30316](../../../error-codes/#-30316), [-30502](../../../error-codes/#-30502), [-30511](../../../error-codes/#-30511)

### NOTE
{{< alert >}}Generally, the PcAPI_initialize() function uses the default path "/var/tmp/.petra/petra_cipher_api.conf" without being called if it is available. However, in exceptional cases where the system security solution or policy does not allow access to /var/tmp or a solution automatically deletes files under /var/tmp periodically, the function is used only in environments where it is difficult to use the /var/tmp path.{{< /alert >}}
