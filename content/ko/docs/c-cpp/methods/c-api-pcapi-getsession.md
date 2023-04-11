---
title: "PcAPI_getSession → int"
linkTitle: "PcAPI_getSession"
weight: 3
categories: ["guide"]
tags: ["api", "c++", "development", "programming"]
date: 2023-04-11
description: >
  PcAPI_getSession는 Petra Cipher 키 서버 세션 ID를 얻는 함수입니다. 
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_getSession(const char* client_ip);
```


### DESCRIPTION
**PcAPI_getSession** 함수는 인자로 전달받은 **client_ip**를 해시 스트링으로 변환한 후, 이를 이용하여 키 서버 세션 풀에서 세션을 찾습니다.


만약 기존 세션이 존재하면, 기존 세션을 반환하고, 세션 풀에 세션이 존재하지 않을 경우 새로운 세션을 생성하여 **세션 ID**를 나타내는 **signed 32-bit 정수**를 반환합니다. 반환된 세션 ID는 암/복호화에서 사용됩니다.

또한, 반환된 세션 ID는 서버 측에서 로깅 및 감사 목적으로 사용될 수 있습니다. 이를 통해 암호화/복호화에 대한 감사 추적이 가능합니다.


### RETURN VALUE
성공 시 세션 ID를 나타내는 **signed 32-bit 정수**를 반환합니다.

오류가 발생하면 0 보다 작은 [에러 코드](../../../error-codes)를 반환합니다. 

### ERRORS
[-30309](../../../error-codes/#-30309), [-30310](../../../error-codes/#-30310), [-30312](../../../error-codes/#-30312), [-30315](../../../error-codes/#-30315), [-30316](../../../error-codes/#-30316), [-30340](../../../error-codes/#-30340), [-30341](../../../error-codes/#-30341), [-30342](../../../error-codes/#-30342), [-30343](../../../error-codes/#-30343), [-30344](../../../error-codes/#-30344)
