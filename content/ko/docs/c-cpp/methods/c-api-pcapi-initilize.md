---
title: "PcAPI_initialize → void"
linkTitle: "PcAPI_initialize"
weight: 2
categories: ["guide"]
tags: ["api", "c++", "development", "programming"]
date: 2023-04-11
description: >
  PcAPI_initialize 함수는 구성 파일을 지정하여 초기화 하는 함수입니다. 
---

### SYNOPSIS
```cpp
#include "PcAPIL.h"

int PcAPI_initialize(char *info_file_path, char *credentials_pw);
```


### DESCRIPTION
PcAPI_initialize 함수는 libpcapi.so 라이브러리를 사용하기 위한 구성 파일을 설정합니다. 구성 파일은 키 관리 서버 설정과 인증에 필요한 자격 증명 정보 등을 포함하고 있습니다.
함수의 info_file_path 매개변수에는 구성 파일의 전체 경로와 파일명을 입력해야 하며, credentials_pw 매개변수에는 자격 증명 비밀번호를 입력해야 합니다. 이 비밀번호는 info_file_path 파일의 내용 중 credentials 값을 발급할 때 사용한 비밀번호와 동일해야 합니다. 만약 비밀번호를 사용하지 않았다면 빈 값("")을 입력하면 됩니다.

함수가 호출되지 않았을 때 기본적으로 읽어오는 경로는 "/var/tmp/.petra/petra_cipher_api.conf" 이며, 비밀번호는 사용되지 않습니다.

자세한 정보는 "[설치 가이드 - 구성 파일](../../get-started/installation/linux/#구성-파일-설정)" 부분을 참고하시기 바랍니다.


### RETURN VALUE
성공 시 **0**을 반환합니다. 

오류가 발생하면 0 보다 작은 [에러 코드](../../../error-codes)를 반환합니다. 

### ERRORS
[-30315](../../../error-codes/#-30315), [-30316](../../../error-codes/#-30316), [-30502](../../../error-codes/#-30502), [-30511](../../../error-codes/#-30511)

### NOTE
{{< alert >}}일반적으로 **PcAPI_initialize()** 함수는 기본 경로인 **/var/tmp/.petra/petra_cipher_api.conf 를 사용할 수 있을 경우 호출하지 않고 기본 경로를 사용합니다.** 
예외적으로 시스템 보안 솔루션 혹은 정책에 따라 /var/tmp 에 대한 사용 권한을 얻지 못하거나 주기적으로 /var/tmp 이하 파일을 자동으로 제거하는 솔루션이 동작하는 등 /var/tmp 경로를 사용하기 어려운 환경에서만 사용됩니다. {{< /alert >}}
