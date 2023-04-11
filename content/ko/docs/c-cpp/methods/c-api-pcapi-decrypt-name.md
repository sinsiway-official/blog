---
title: "PcAPI_decrypt_name → int"
linkTitle: "PcAPI_decrypt_name"
weight: 5
categories: ["guide"]
tags: ["api", "c++", "development", "programming"]
date: 2023-04-11
description: >
  PcAPI_decrypt_name 암호화 된 데이터를 복호화 하는 함수입니다. 
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
    unsigned int *dst_len
);
```


### DESCRIPTION
**PcAPI_decrypt_name** 함수는 Petra Cipher Key Server에서 생성한 암호화 컬럼의 이름인 **enc_col_name**과 암호화된 데이터인 **src**를 입력받아, 해당 암호화 컬럼을 사용하여 원본 데이터를 복호화하는 기능을 제공합니다. 주의할 점은, enc_col_name 매개변수는 암호화 함수(**PcAPI_encrypt_name**)에서 사용했던 **암호화 컬럼의 이름과 동일**해야 한다는 것입니다. 이를 지키지 않으면 복호화가 실패합니다.

**api_sid**에는 **PcAPI_getSession** 함수를 호출하여 반환된 **세션 ID**가 전달되어야 합니다. 세션 ID는 Petra Cipher Key Server와의 통신에 사용되며 사용하려는 키에 대한 접근 권한이나 감사데이터에서 사용자 구분 등에 사용됩니다.

함수의 실행 결과로는 복호화된 데이터가 **dst** 버퍼에 저장되며, 복호화된 데이터의 길이가 **dst_len** 매개변수에 저장됩니다. dst_len은 dst 버퍼의 크기만큼 전달되어야 하며, 최소한 src_len보다는 크도록 해야합니다. 일반적으로 dst 버퍼의 크기는 src 버퍼의 크기와 동일하게 설정됩니다.
복호화가 성공하면 dst에는 원본 데이터가 들어가고 dst_len에는 원본 데이터의 길이가 들어가게 됩니다.

하지만 PcAPI_decrypt_name 실행 후에 dst 버퍼에서 원본 데이터 끝에 마지막 값이 없기 때문에 dst에서 dst_len 길이 만큼 잘라서 사용하거나 dst 버퍼를 바로 사용하려면 `dst[dst_len] ='\0'` 형태로 데이터의 마지막을 표현해주어야 합니다.


### RETURN VALUE
성공 시 0을 반환합니다. 

오류가 발생하면 0 보다 작은 [에러 코드](../../../error-codes)를 반환합니다. 

### ERRORS
[-30101](../../../error-codes/#-30101), [-30103](../../../error-codes/#-30103), [-30105](../../../error-codes/#-30105), [-30106](../../../error-codes/#-30106), [-30107](../../../error-codes/#-30107), [-30108](../../../error-codes/#-30108), [-30111](../../../error-codes/#-30111), [-30116](../../../error-codes/#-30116), [-30117](../../../error-codes/#-30117), [-30118](../../../error-codes/#-30118), [-30302](../../../error-codes/#-30302), [-30351](../../../error-codes/#-30351), [-30388](../../../error-codes/#-30388), [-30401](../../../error-codes/#-30401)
