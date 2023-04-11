---
title: "PcAPI_getSession → int"
linkTitle: "PcAPI_getSession"
weight: 3
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_getSession(const char* client_ip);
```


### DESCRIPTION
The **PcAPI_getSession** function converts the **client_ip** passed as an argument into a hash string and uses it to find a session in the key server session pool. If an existing session exists, it returns the existing session, and if there is no session in the session pool, it creates a new session and returns a **signed 32-bit integer representing the session ID**. The returned session ID is used for encryption/decryption.

In addition, the returned session ID can be used for logging and auditing purposes on the server-side. This enables audit tracking of encryption/decryption activities.

### RETURN VALUE
The function returns a signed 32-bit integer representing the session ID upon success. 

If an error occurs, it returns an error code less than 0.

### ERRORS
[-30309](../../../error-codes/#-30309), [-30310](../../../error-codes/#-30310), [-30312](../../../error-codes/#-30312), [-30315](../../../error-codes/#-30315), [-30316](../../../error-codes/#-30316), [-30340](../../../error-codes/#-30340), [-30341](../../../error-codes/#-30341), [-30342](../../../error-codes/#-30342), [-30343](../../../error-codes/#-30343), [-30344](../../../error-codes/#-30344)
