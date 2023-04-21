---
title: "getErrCode() → int"
linkTitle: "getErrCode"
weight: 5
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  PcAPI_decrypt_name 암호화 된 데이터를 복호화 하는 함수입니다. 
---

### SYNOPSIS
```java
public int getErrCode()
```


### DESCRIPTION
이 함수를 사용하여 **PcaException**에서 발생한 에러 코드를 반환합니다. 함수가 의미하는 코드는 Petra Cipher API에서 발생한 **오류 코드**입니다. 이 코드를 활용하여 암/복호화에서 발생할 수 있는 에러를 더 상세히 확인할 수 있습니다. 


### RETURN VALUE
PcaException 에서 발생한 에러 코드
