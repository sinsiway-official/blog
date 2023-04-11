---
title: "PcAPI_encrypt_name → int"
linkTitle: "PcAPI_encrypt_name"
weight: 4
categories: ["guide"]
tags: ["api", "c++", "development", "programming"]
date: 2023-04-11
description: >
  PcAPI_encrypt_name 는 데이터를 암호화 하는 함수입니다. 
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_encrypt_name(
    int api_sid,
    const char *enc_col_name,
    unsigned char *src,
    int src_len,
    unsigned char *dst,
    unsigned int *dst_len
);
```


### DESCRIPTION
**PcAPI_encrypt_name** 함수는 Petra Cipher Key Server에서 생성한 암호화 컬럼의 이름인 **enc_col_name**과 소스 데이터인 **src**를 입력받아, 소스 데이터를 해당 암호화 컬럼을 사용하여 암호화하는 기능을 제공합니다.

**api_sid** 에는 **PcAPI_getSession** 함수를 호출하여 반환된 **세션 ID**가 전달되어야 합니다. 세션 ID는 Petra Cipher Key Server와의 통신에 사용되며 사용하려는 키에 대한 접근 권한이나 감사데이터에서 사용자 구분 등에 사용됩니다. 

함수의 실행 결과로는 암호화 된 데이터가 **dst** 버퍼에 저장되며, 암호화 된 데이터의 길이가 **dst_len** 매개변수에 저장됩니다. dst_len은 dst 버퍼의 크기만큼 전달되어야 하며, 최소한 src_len보다는 크도록 해야합니다. **일반적으로 dst 버퍼의 크기는 src 버퍼의 2배 정도 크기로 충분하게 사용됩니다.**

다만, PcAPI_encrypt_name 실행 후에 dst 버퍼에서 암호화 된 데이터 끝에 마지막 값이 없기 때문에 dst에서 dst_len 길이 만큼 잘라서 사용하거나 dst 버퍼를 바로 사용하려면 `dst[dst_len] ='\0'` 형태로 데이터의 마지막을 표현해주어야 합니다.


### RETURN VALUE
성공 시 0을 반환합니다. 

오류가 발생하면 0 보다 작은 [에러 코드](../../../error-codes)를 반환합니다. 

### ERRORS
[-30101](../../../error-codes/#-30101), [-30103](../../../error-codes/#-30103), [-30106](../../../error-codes/#-30106), [-30115](../../../error-codes/#-30115), [-30117](../../../error-codes/#-30117), [-30301](../../../error-codes/#-30301), [-30302](../../../error-codes/#-30302), [-30351](../../../error-codes/#-30351), [-30388](../../../error-codes/#-30388)
