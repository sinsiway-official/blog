---
title: "decrypt() → stString"
linkTitle: "decrypt "
weight: 20
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  decrypt 는 암호화 된 데이터를 복호화 하는 함수입니다. 
---

### SYNOPSIS
```java
public String decrypt(String ecn, String src) throws PcaException
```


### DESCRIPTION
decrypt 함수는 암호화된 데이터인 src와 해당 암호화 컬럼의 이름인 ecn을 파라미터로 사용합니다. 

ecn 파라미터는 암호화 컬럼 이름을 전달해야 합니다. src 파라미터는 암호화된 데이터를 전달해야 합니다. 만약 null 값을 전달하면 null이 반환됩니다. decrypt 함수의 반환값은 복호화된 평문 데이터입니다.

PcaException이 발생할 수 있으므로, 반드시 예외처리를 해주어야 합니다.


### RETURN
String 복호화 데이터

### EXCEPTION
[-30101](../../../error-codes/#-30101), [-30103](../../../error-codes/#-30103), [-30105](../../../error-codes/#-30105), [-30106](../../../error-codes/#-30106), [-30107](../../../error-codes/#-30107), [-30108](../../../error-codes/#-30108), [-30111](../../../error-codes/#-30111), [-30116](../../../error-codes/#-30116), [-30117](../../../error-codes/#-30117), [-30118](../../../error-codes/#-30118), [-30302](../../../error-codes/#-30302), [-30351](../../../error-codes/#-30351), [-30388](../../../error-codes/#-30388), [-30401](../../../error-codes/#-30401)
