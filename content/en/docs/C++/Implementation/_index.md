---
title: "Implementation"
linkTitle: "Implementation"
weight: 1
---

```cpp
#include "PcAPIL.h"

int main(int argc, char const *argv[])
{
    unsigned char encryptText[1024];
    unsigned char decryptText[1024];

    int sid = PcAPI_getSession("");
    const char *keyName = "ARIA-256-B64";

    int rtn = 0;
    unsigned char *plainText = (unsigned char *)"sinsiway petra cipher";

    unsigned int encryptTextLen = 1024;
    unsigned int decryptTextLen = 1024;
    memset(encryptText, 0, encryptTextLen);
    memset(decryptText, 0, decryptTextLen);

    rtn = PcAPI_encrypt_name(sid, keyName, plainText, strlen((const char *)plainText), encryptText, &encryptTextLen);
    rtn = PcAPI_decrypt_name(sid, keyName, encryptText, encryptTextLen, decryptText, &decryptTextLen);

    return 0;
}
```

The given example source code is an illustration of how to obtain a session and use encryption/decryption functions using the PetraCipher library, **libpcapi.so.**

The source code uses the **PcAPIL.h header** file to invoke the PetraCipher library. The **PcAPI_getSession()** function is used to obtain a session ID, and the **PcAPI_encrypt_name()** and **PcAPI_decrypt_name()** functions are used to encrypt and decrypt data.

To use the PetraCipher library, a session must first be obtained, which is then used to encrypt or decrypt data. In each function, the session ID, encryption key name, plain data, etc. are passed as parameters.

The PetraCipher library is designed for data protection and secure communication and can be used in various applications. The provided source code illustrates the basic usage of the library, and detailed instructions can be found in the library's documentation.