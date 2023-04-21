---
title: "JAVA"
linkTitle: "JAVA"
weight: 2
---

PetraCipherAPI.jar 아카이브 파일에는 PcaException, PcaSessionPool, PcaSession 클래스가 포함되어 있으며, 이들 클래스는 sinsiway 패키지에 위치합니다. 아카이브 파일은 Java Native Interface (JNI)를 사용하여 "libpcjapi.so" 네이티브 라이브러리를 로드하여 사용합니다. 이 네이티브 라이브러리는 C 또는 C++로 작성된 코드를 포함하고 있으며, Java 가상 머신(VM) 외부에서 실행됩니다.
"PetraCipherAPI.jar" 아카이브 파일에서는 네이티브 코드를 호출하기 위해 JNI 인터페이스를 사용합니다.
"libpcjapi.so" 파일은 네이티브 코드를 포함하고 있으며, 네이티브 라이브러리 파일 형식으로 제공됩니다. 이 파일은 아카이브 파일에서 로드되어 자바 애플리케이션에서 사용됩니다. 네이티브 코드는 일반적으로 자바 코드로 구현하기 어려운 시스템 레벨 기능과 같은 것들을 처리하기 위해 사용됩니다.


