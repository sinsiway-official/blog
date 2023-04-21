---
title: "sinsiway.PcaException class"
linkTitle: "PcaException"
weight: 20
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  Petra Cipher 라이브러리의 클래스를 정의합니다.
---

**PcaException** 클래스는 **Exception** 클래스를 상속받아 구현된 사용자 정의 예외 클래스입니다.

이 클래스는 생성자를 통해 예외 메시지와 에러 코드를 받아 객체를 생성하며, **getErrCode()** 메소드를 제공하여 에러 코드를 반환할 수 있습니다.

PcaException 클래스는 Petra Cipher API에서 발생한 예외를 처리하기 위해 사용됩니다. 예를 들어, API 호출 중 에러가 발생한 경우 해당 에러 코드와 함께 예외를 발생시켜, 호출한 쪽에서 적절하게 예외 처리를 할 수 있도록 도와줍니다. 상속받은 **getMessage()**, **getCause()**, **getStackTrace()** 함수 외에 Petra Cipher 의 에러 코드를 확인할 수 있는 **getErrCode()** 함수를 제공합니다. 

## Constructors
```java
PcaException(String msg, int errcode)
PcaException(String msg)
```