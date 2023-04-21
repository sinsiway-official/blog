---
title: "initialize() → static void"
linkTitle: "initialize"
weight: 10
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  PcAPI_decrypt_name 암호화 된 데이터를 복호화 하는 함수입니다. 
---

### SYNOPSIS
```java
public static void initialize(String conf_file_path, String credentials_password) throws PcaException
```


### DESCRIPTION
이 메소드는 세션 풀을 초기화하기 위한 구성 파일을 설정합니다. 구성 파일은 키 관리 서버 설정과 인증에 필요한 자격 증명 정보 등을 포함하고 있습니다.

함수의 conf_file_path 매개변수에는 구성 파일의 전체 경로와 파일명을 입력해야 하며, credentials_password 매개변수에는 자격 증명 비밀번호를 입력해야 합니다. 이 비밀번호는 conf_file_path 파일의 내용 중 credentials 값을 발급할 때 사용한 비밀번호와 동일해야 합니다. 만약 비밀번호를 사용하지 않았다면 빈 값("")을 입력하면 됩니다.

함수가 호출되지 않았을 때 기본적으로 읽어오는 경로는 "/var/tmp/.petra/petra_cipher_api.conf" 이며, 비밀번호는 사용되지 않습니다.
자세한 정보는 "설치 가이드 - 구성 파일" 부분을 참고하시기 바랍니다.

만약 세션 풀 초기화에 실패하면 PcaException 예외를 throw 합니다. 이 예외는 "initialize failed. error code[에러코드]" 라는 메시지와 함께 던져집니다.

### RETURN
void

### EXCEPTION
[-30315](../../../error-codes/#-30315), [-30316](../../../error-codes/#-30316), [-30502](../../../error-codes/#-30502), [-30511](../../../error-codes/#-30511)


