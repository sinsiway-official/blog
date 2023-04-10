---
title: "PcAPI_decrypt_name → int"
linkTitle: "PcAPI_decrypt_name → int"
weight: 5
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_decrypt_name(
    int api_sid,
    const char *enc_col_name,
    unsigned char *src,
    int src_len,
    unsigned char *dst,
    unsigned int *dst_len)
```


### DESCRIPTION
The **PcAPI_decrypt_name** function takes the name of the encryption column created by the Petra Cipher Key Server **enc_col_name** and the encrypted data **src** as input, and provides the functionality to decrypt the original data using the corresponding encryption column. It is important to note that the **enc_col_name** parameter must be identical to the name of the encryption column used in the encryption function PcAPI_encrypt_name, otherwise the decryption will fail.

The **api_sid** parameter must be populated with the session ID returned by calling the **PcAPI_getSession** function. The session ID is used for communication with the Petra Cipher Key Server and is also used for access control and user identification in audit data.

The function's output is the decrypted data stored in the dst buffer, and the length of the decrypted data stored in the **dst_len** parameter. **dst_len** must be at least as large as the size of the **src buffer**, and should be the same size as the dst buffer in most cases.

If the decryption is successful, the original data will be stored in the dst buffer and the length of the original data will be stored in the dst_len parameter. However, since the decrypted data does not have a null terminator at the end, if you want to use the dst buffer directly, you need to add a null terminator to the end of the data by setting `dst[dst_len] = '\0'` or by truncating the dst buffer to dst_len bytes.

### RETURN VALUE
The function returns 0 upon success. 

If an error occurs, it returns an error code less than 0.

### ERRORS
[-30101](../../../error-codes/#-30101), [-30103](../../../error-codes/#-30103), [-30105](../../../error-codes/#-30105), [-30106](../../../error-codes/#-30106), [-30107](../../../error-codes/#-30107), [-30108](../../../error-codes/#-30108), [-30111](../../../error-codes/#-30111), [-30116](../../../error-codes/#-30116), [-30117](../../../error-codes/#-30117), [-30118](../../../error-codes/#-30118), [-30302](../../../error-codes/#-30302), [-30351](../../../error-codes/#-30351), [-30388](../../../error-codes/#-30388), [-30401](../../../error-codes/#-30401)
