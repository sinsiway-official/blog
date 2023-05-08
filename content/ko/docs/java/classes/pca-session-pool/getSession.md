---
title: "getSession() → static sinsiway.PcaSession"
linkTitle: "getSession"
weight: 20
categories: ["guide"]
tags: ["api", "java", "development", "programming"]
date: 2023-04-21
description: >
  getSession 함수는 암복호화를 위한 PcaSession 객체를 얻는 함수입니다.  
---

### SYNOPSIS
```java
public static sinsiway.PcaSession getSession() throws PcaException
public static sinsiway.PcaSession getSession(String client_ip, String user_id, String client_program) throws PcaException
```


### DESCRIPTION
PcaSessionPool 클래스의 getSession() 함수는 Petra Cipher Key Server에서 인가된 키 데이터를 사용하여 암호화 및 복호화를 수행하는 PcaSession 객체를 반환하는 함수입니다.

이 함수는 client_ip, user_id, client_program을 매개변수로 받아 해당 정보를 사용하여 PcaSession 객체의 고유한 hash key를 생성합니다. 그리고 이 hash key를 사용하여 SessionPool에서 PcaSession 객체를 가져옵니다. 만약 SessionPool에서 PcaSession 객체를 찾지 못했다면, 새로운 PcaSession 객체를 생성하고 SessionPool에 추가하며, 이미 SessionPool에 PcaSession 객체가 존재한다면 해당 PcaSession 객체를 반환합니다.

getSession() 함수 내부에서 예외 상황이 발생하면, PcaException 객체를 던져서 예외 상황을 처리하며, 이를 통해 클라이언트에서 예외를 처리할 수 있도록 도와줍니다.

만약 특별히 권한 관리가 필요하지 않고 공유 세션을 위해 성능적인 부분에서 가장 많은 이점을 가지고 싶다면 매개변수가 없는 함수를 사용하여 모든 세션이 같은 세션을 공유하도록 사용할 수 있습니다. 

### RETURN
sinsiway.PcaSession 객체

### EXCEPTION
[-30309](../../../../error-codes/#-30309), [-30310](../../../../error-codes/#-30310), [-30312](../../../../error-codes/#-30312), [-30315](../../../../error-codes/#-30315), [-30316](../../../../error-codes/#-30316), [-30340](../../../../error-codes/#-30340), [-30341](../../../../error-codes/#-30341), [-30342](../../../../error-codes/#-30342), [-30343](../../../../error-codes/#-30343), [-30344](../../../../error-codes/#-30344)


