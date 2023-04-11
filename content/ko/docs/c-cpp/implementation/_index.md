---
title: "Implementation"
linkTitle: "Implementation"
weight: 20
categories: ["guide"]
tags: ["api", "c++", "development", "programming"]
date: 2023-04-11
description: >
  Petra Cipher 라이브러리를 사용해 함수를 작성하는 방법을 가이드합니다. 
---
```cpp
#include "PcAPIL.h"

int main(int argc, char const *argv[])
{
    unsigned char encryptText[1024];
    unsigned char decryptText[1024];

    int sid = PcAPI_getSession("");
    const char *keyName = "ARIA-256-B64";

    int rtn = 0;
    unsigned char *plainText = (unsigned char *)"sinsiway petra cipher";

    unsigned int encryptTextLen = 1024;
    unsigned int decryptTextLen = 1024;
    memset(encryptText, 0, encryptTextLen);
    memset(decryptText, 0, decryptTextLen);

    rtn = PcAPI_encrypt_name(sid, keyName, plainText, strlen((const char *)plainText), encryptText, &encryptTextLen);
    rtn = PcAPI_decrypt_name(sid, keyName, encryptText, encryptTextLen, decryptText, &decryptTextLen);

    return 0;
}
```

주어진 예제 소스 코드는 PetraCipher 라이브러리인 **libpcapi.so**를 사용하여 세션을 얻고 암호화/복호화 함수를 사용하는 방법을 보여주는 예시입니다.

소스 코드에서는 PcAPIL.h 헤더 파일을 사용하여 PetraCipher 라이브러리를 호출합니다. **PcAPI_getSession()** 함수를 사용하여 **세션 ID**를 얻고, **PcAPI_encrypt_name()** 및 **PcAPI_decrypt_name()** 함수를 사용하여 데이터를 암호화하고 복호화합니다.

PetraCipher 라이브러리를 사용하려면 먼저 세션을 얻어야하며, 각 함수에서 세션 ID, 암호화 키 이름, 평문 데이터 등을 매개변수로 전달해야합니다.

PetraCipher 라이브러리는 데이터 보호 및 안전한 통신을 위해 설계되었으며 다양한 애플리케이션에서 사용할 수 있습니다. 제공된 소스 코드는 라이브러리의 기본 사용법을 보여주며, 더 자세한 정보는 라이브러리의 문서에서 확인할 수 있습니다.