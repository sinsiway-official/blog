---
title: "encrypt() → stString"
linkTitle: "encrypt "
weight: 10
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  encrypt 는 평문 데이터를 암호화 하는 함수입니다.
---

### SYNOPSIS
```java
public String encrypt(String ecn, String src) throws PcaException
```


### DESCRIPTION
encrypt 함수는 암호화 컬럼 이름 enc과 평문 데이터 src를 파라미터로 사용합니다. 

ecn 파라미터에는 Petra Cipher Key Server에서 생성한 암호화 컬럼의 이름을 전달해야 합니다. src 파라미터에는 암호화하고자 하는 평문 데이터를 전달해야 합니다. 이 때, null 값을 전달하면 null을 반환합니다. encrypt 함수가 반환하는 값은 암호화된 데이터입니다. 이를 복호화하려면 decrypt 함수를 사용해야 합니다.

PcaException이 발생할 수 있으므로, 예외처리를 반드시 해주어야 합니다.


### RETURN
String 암호화 데이터

### EXCEPTION
[-30101](../../../error-codes/#-30101), [-30103](../../../error-codes/#-30103), [-30106](../../../error-codes/#-30106), [-30115](../../../error-codes/#-30115), [-30117](../../../error-codes/#-30117), [-30301](../../../error-codes/#-30301), [-30302](../../../error-codes/#-30302), [-30351](../../../error-codes/#-30351), [-30388](../../../error-codes/#-30388)
