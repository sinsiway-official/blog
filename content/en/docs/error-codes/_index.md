---
title: "Error Codes"
linkTitle: "Error Codes"
weight: 3
---

##### -30101
This error occurs when the key length is not 128 bits or 256 bits when using the SEED algorithm. In this case, you need to contact the developer to confirm the correct key settings information.

##### -30103
This error occurs when using an encryption algorithm not supported by the encryption library. In this case, you need to contact the developer to modify the configuration information to use a supported encryption algorithm.

##### -30105
This error occurs when the decrypted result data is larger than the size of the output buffer. In this case, you need to adjust the size of the output buffer appropriately so that the decrypted data can be stored.

##### -30106
This error occurs when a Secure Hash Algorithm (SHA) hash function uses a bit size other than 256, 384, or 512 bits. In this case, you need to contact the developer to confirm the correct configuration information.

##### -30107
This error occurs when the length of the encrypted data is invalid. In this case, you need to check if the length of the data to be decrypted is valid.

##### -30108
This error occurs when the length of the data to be decrypted is less than the minimum length determined by the algorithm, mode, encoding, and other settings used for encryption. It also occurs when trying to decrypt null or unencrypted data. In this case, you need to adjust the length of the data to be decrypted appropriately or try to decrypt the data again using the correct encryption settings or encrypted data. Alternatively, if the data to be decrypted is null, you can ignore this error code and process it normally.

##### -30111
This error occurs when the input parameters used for decryption are invalid. In particular, hash functions such as SHA or HMAC cannot be used in the decryption function. In this case, it is necessary to check whether the algorithm for the key being used supports symmetric key algorithms for decryption.

##### -30115
This error occurs when attempting to encrypt data that has already been encrypted. In this case, it is necessary to ensure that the data is not already encrypted.

##### -30116
This error occurs when the trailer value is invalid. The trailer value's length exceeds the encryption block size or is less than 0, causing the decryption to fail. In this case, the data being decrypted and the key being used must be checked again.

##### -30117
This error occurs when initialization of encryption or decryption metadata fails. In this case, it is necessary to check the algorithms supported by the library, the key size, and the encryption mode again.

##### -30118
This error occurs when the padding is invalid. When performing decryption, padding must be removed, but it may be incorrect or nonexistent. In this case, the data being decrypted and the key being used must be checked again.

##### -30301
This error occurs when the session requesting the encryption key does not have access to the encryption key. In this case, the user must check with the policy administrator to ensure they have access to the encryption key.

##### -30302
This error occurs when an invalid API session ID is used. It occurs when session information cannot be obtained. In this case, the log file specified in the encryption library configuration file should be checked to analyze the specific cause of the inability to obtain an encryption session.

##### -30309
This error occurs when a spin lock cannot be obtained while obtaining an API session. This may be because another thread already holds the lock for that critical section. In this case, try again after a short period of time.

##### -30310
This error occurs when a latch lock cannot be acquired during the process of obtaining a key server session. This may be because another thread already holds a lock on the critical section. In this case, please try again after a moment.

##### -30312
This error occurs when there are no more available sessions in the session pool. In this case, please try again after a certain amount of time or increase the maximum capacity of the session pool in the configuration file.

##### -30315
This error is returned when a parsing error occurs in the configuration file. Each line in the configuration file should exist in the format of "variable=value". For example, this error may occur when there is no "=" sign in the line to be parsed, or when there are spaces in the name or value. In this case, you should check the values in the configuration file.

##### -30316
This error occurs when the configuration file does not exist or the executing account does not have read permission on the file. Check whether the configuration file exists and whether you have read permission on the file or directory and file. Generally, the configuration file is located in the /var/tmp/.petra/petra_cipher_api.conf path. In this case, you need to modify the location and permission of the configuration file.

##### -30340
This error occurs when the key server host information cannot be obtained. In this case, check the values of keysvr.primary.host, keysvr.secondary.host, and keysvr.third.host in the configuration file. If there is no information in the configuration file, add the host information.

##### -30341
This error occurs when a socket communication for a key server session creation fails. The reasons for such failure may include attempting to allocate an already in-use port, insufficient permission on the process trying to create a socket, or insufficient operating system resources. In this case, you can check the open files option by using the ulimit -n command and increase the value.

##### -30342
This error occurs when the key server session connection fails. The reasons for such failure can be diverse. Check the configuration file and examine the log file for detailed information about the cause.

##### -30343
This error occurs when data transmission fails in key server socket communication. There can be various reasons for this failure. For example, this error may occur when the socket is already closed, the socket connection is disconnected, or the socket buffer is full and cannot send data. In this case, you should check the log file in the configuration file's log file path for detailed information.

##### -30344
Failed to retrieve data from key server socket communication. The reason for this failure can be various, such as when the socket is already closed, the socket connection is lost, or unable to receive data. In this case, you should analyze the log file by checking the log file path in the configuration file for more detailed information.

##### -30351
Unable to verify the key name. This error occurs when the key name provided as input does not exist in the key server. You need to verify the key name.

##### -30388
This error occurs when attempting to perform a character set convert on input data that is null or an empty string. In this case, you need to check the character set convert option.

##### -30401
This error occurs when the session requesting the decryption key does not have access to the decryption key. In this case, the policy administrator should verify whether the user has permission to access the decryption key.

##### -30502
This error occurs when the credential information is invalid. You should verify the credential information and check whether the values are correct. Credential information is typically stored in the configuration file and is used to perform authentication and authorization based on the information provided by the user.

##### -30511
This error occurs when the product fails to load the libklib.so library file, which is a government-certified validation filter encryption module used by the product. You need to check whether the file exists in the system or dynamic library path and whether it has execution permission. Typically, the file is located in the /usr/lib directory. If the file is missing, you need to install or rebuild it. If the file exists but does not have execution permission, you need to add execution permission using the chmod command.

##### -30701
This error occurs when the product cannot verify information about the key server. You should check the keysvr.primary, keysvr.secondary, and keysvr.third values in the configuration file. These values typically contain information about the key server's IP address and port. You need to verify that this information is correct.
