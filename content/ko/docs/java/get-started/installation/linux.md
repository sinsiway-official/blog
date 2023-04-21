---
title: "Linux"
linkTitle: "Linux"
categories: ["guide"]
tags: ["petra cipher", "java", "library"]
weight: 2
date: 2023-04-21
description: >
  이 가이드는 Linux 계열 운영체제에서 이 라이브러리를 설치하고 운영하는 방법을 안내합니다. Linux 계열 운영체제는 _Ubuntu_, _CentOS_, _Debian_, _Fedora_ 등이 포함됩니다. 
---



## 시스템 요구사항

### 운영체제
본 프로그램은 Linux 64Bit 계열의 운영체제에서 동작합니다.

### 커널 버전
본 프로그램을 실행하기 위해서는 Linux 계열의 운영체제에서 사용되는 커널 버전 2.6.32 이상이 요구됩니다.

### 컴파일러
본 프로그램을 컴파일하기 위해서는 GCC 컴파일러 4.4.7 이상과 java8 (jdk1.8) 이상에서 동작합니다. 

## 다운로드 및 설치
본 프로그램을 사용하기 위해서는 libpjcapi.so 라이브러리 파일과 PcaException.java, PcaSessionPool.java, PcaSession.java 파일을  다운로드합니다.

### 아카이브 파일 설치
PcaException.java, PcaSessionPool.java, PcaSession.java 파일은 sinsiway 패키지로 사용됩니다. 파일을 모두 sinsiway 디렉토리로 이동 후 javac 컴파일하여 PetraCipherAPI.jar 아카이브 파일로 생성해야 합니다. 
```bash
$ tree sinsiway/
sinsiway/
|-- PcaException.java
|-- PcaSession.java
`-- PcaSessionPool.java

$ javac -Xlint:unchecked sinsiway/*.java
$ jar -cvf0 PetraCipherAPI.jar ./sinsiway/*.class
```

### 라이브러리 설치
라이브러리는 시스템 라이브러리 경로와 커스텀 라이브러리 두 가지 경로로 설치 가능합니다. 일반적으로 커스텀 라이브러리 경로를 사용해 설치합니다. 




#### 시스템 라이브러리 경로에 설치하는 방법
libpcapi.so 파일을 /usr/lib64 디렉토리에 설치하여 시스템 전역에서 사용할 수 있도록 할 수 있습니다. 이 방법은 다음과 같이 진행됩니다.

root 권한으로 터미널을 열고, libpcjapi.so 파일을 다운로드합니다.

다운로드한 파일과 생성한 아카이브 파일을 /lib 또는 /lib64 디렉토리에 복사합니다.

```bash
$ sudo cp libpjcapi.so /usr/lib64
$ sudo cp PetraCipherAPI.jar /usr/lib64
```

파일의 권한을 변경합니다.
```bash
$ sudo chmod 755 /usr/lib64/libpjcapi.so
$ sudo chmod 755 /usr/lib64/PetraCipherAPI.jar
```


#### 커스텀 라이브러리 경로에 설치하는 방법
libpcjapi.so 과 PetraCipherAPI.jar파일을 사용하는 애플리케이션의 실행 환경에 따라 커스텀 라이브러리 경로에 설치하여 사용할 수도 있습니다. 이 방법은 다음과 같이 진행됩니다.

애플리케이션 실행 파일이 위치한 디렉토리에 libpcjapi.so, PetraCipherAPI.jar 파일을 복사합니다.
```bash
$ cp libpcjapi.so /usr/local/lib64
$ cp PetraCipherAPI.jar /usr/local/lib64
```

LD_LIBRARY_PATH 환경 변수에 라이브러리 파일이 있는 경로를 등록합니다.
```bash
$ export LD_LIBRARY_PATH=/usr/local/lib64
```

## 컴파일
PetraCipherAPI.jar 아카이브 파일을 사용하는 컴파일하기 위해서는 클래스패스 옵션을 사용하여 아카이브 파일을 지정해줘야 합니다. 

```bash
$ javac -cp ./lib64/PetraCipherAPI.jar program.java
```

위 명령어에서 -cp 옵션은 환경변수 CLASSPATH 역할을 옵션으로 지정하며, program.java는 컴파일할 소스 코드 파일 이름을 의미합니다.

### 프로그램 실행
program 실행 파일을 생성하고 실행합니다.
```bash
java ./program
```

위 명령어를 실행하면 program 프로그램이 실행됩니다. 
단, 프로그램에서 암복호화 함수 호출을 위해 반드시 서버에 구성 파일을 작성해두어야 합니다. 구성 파일의 설정 방법은 아래와 같습니다.

## 구성 파일 설정
본 프로그램을 실행하기 위해선 페트라 싸이퍼 키 서버 정보가 저장 된 구성 파일을 필요로합니다. 
구성 파일은 소스코드 내부에서 초기화 함수로 특별히 지정하지 않으면 “/var/tmp/.petra/petra_cipher_api.conf” 기본 경로를 사용합니다. 

### 자격 증명 값 생성
구성 파일 작성을 위해 우선 키 서버에서 자격 증명 값을 생성해야 합니다. 자격 증명 값은 키 서버에서 pcp_credentials 바이너리를 통해 생성할 수 있습니다. 

```bash
$ pcp_credentials generate -svc demo -user dgadmin -password abc -[key|svc_home]
```

#### 옵션



##### -svc SOHA_SVC
SOHA_SVC는 페트라 싸이퍼 인 메모리 데이터베이스 SOHA DBMS의 서비스  이름입니다. 페트라 싸이퍼 설치 계정에서  env \| grep SOHA_SVC 를 통해 값을 확인할 수 있습니다. 

##### -user soha_user
SOHA DBMS의 접속 계정입니다. 기본값으로 dgadmin을 사용합니다. 

##### -password soha_password
SOHA DBMS 계정의 비밀번호입니다. 기본값으로 petra@one1을 사용합니다. 
##### -key [=credentials_password] (선택)
생성하려는 자격 증명 값에 대한 비밀번호입니다. 만약 자격 증명 값을 생성할 때 비밀번호를 사용하면 라이브러리를 사용하는 프로그램에서 반드시 초기화 함수를 사용해 자격 증명 값 비밀번호를 입력해야 합니다. 선택할 수 있는 값으로 사용하지 않으면 비밀번호를 사용하지 않습니다. 
##### -soha_home [=SOHA_HOME] (선택)
로컬 키 서버를 사용하기 위해  설정할 수 있는 SOHA DBMS의 설치 경로입니다. 페트라 싸이퍼 설치 계정에서 env \| grep SOHA_HOME 으로 확인할 수 있습니다. 응용 프로그램과 같은 서버에 설치 된 키 서버에 프로세스 파이프 통신을 통해 보다 빠른 속도로 키 데이터를 얻어오는 구성을 사용할 때 선택할 수 있는 값입니다. 옵션을 사용하기 위해 구성 파일에서 키 서버 호스트 값을 "LOCAL"로 설정해야 합니다.

다음과 같이 생성할 수 있습니다. 
```bash
$ env | grep SOHA_SVC
SOHA_SVC=keysvr
$ pcp_credentials generate -svc keysvr -user dgadmin -password petra@one1

credentials => Y8UdAzNpEDbO8bvMK5ez2W+buNUO8dShCJYgGO84B6y/waMSyTL/RdXzU1d39Pd0PfhNQZEw4LRHKJm5ySPN0kz+DGu/IGKAWbepbG9EgycA=AYQA
```

### 구성파일 생성
구성 파일을 다음과 같이 작성할 수 있습니다. 먼저 vi를 통해 기본 경로인 “/var/tmp/.petra/petra_cipher_api.conf” 파일을 열어줍니다. 
```bash
vi /var/tmp/.petra/petra_cipher_api.conf
```

다음과 같이 키 서버 정보를 입력합니다. 
```bash
keysvr.primary.host = 192.168.10.94
keysvr.primary.port = 6002
keysvr.primary.credentials = Y8UdAzNpEDbO8bvMK5ez2W+buNUO8dShCJYgGO84B6y/waMSyTL/RdXzU1d39Pd0PfhNQZEw4LRHKJm5ySPN0kz+DGu/IGKAWbepbG9EgycA=AYQA
```
페트라 싸이퍼의 구성 정보 파일은 다양한 옵션이 사용될 수 있습니다. 아래는 구성 파일에 사용할 수 있는 옵션들에 대한 설명입니다. 


#### 필수 설정
##### keysvr.primary.host
이 파라미터는 기본 키 서버의 호스트 IP 주소를 지정합니다.
##### keysvr.primary.port
이 파라미터는 기본 키 서버의 KRED(Key Request Encrypt Decrypt)포트 번호를 지정합니다. SOHA_HOME 경로의 config/listener.list 파일에서 client_type=kred 로 설정 된 포트 값을 입력하면 됩니다. 혹은 페트라 싸이퍼 설치 계정에서 “. ~/_profile” 실행 후 키 서버 선택 한 상태에서 “petractl status” 명령어로 상태 확인 시 3번째 포트번호입니다. 
##### keysvr.primary.credentials
이 파라미터는 기본 키 서버의 자격 증명을 지정합니다.

#### 선택 설정
---
키 서버 설정

---

##### keysvr.primary.con_timeout  [=5]
이 파라미터는 기본 키 서버의 연결 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다. 
##### keysvr.primary.in_timeout  [=5]
이 파라미터는 기본 키 서버의 입력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다. 
##### keysvr.primary.out_timeout  [=5]
이 파라미터는 기본 키 서버의 출력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다. 
##### keysvr.secondary.host
이 파라미터는 보조 키 서버의 호스트 IP 주소를 지정합니다.
##### keysvr.secondary.port
이 파라미터는 보조 키 서버의 KRED(Key Request Encrypt Decrypt) 포트 번호를 지정합니다.
##### keysvr.secondary.credentials
이 파라미터는 보조 키 서버의 자격 증명을 지정합니다.
##### keysvr.secondary.con_timeout  [=5]
이 파라미터는 보조 키 서버의 연결 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.
##### keysvr.secondary.in_timeout  [=5]
이 파라미터는 보조 키 서버의 입력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.
##### keysvr.secondary.out_timeout  [=5]
이 파라미터는 보조 키 서버의 출력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.
##### keysvr.third.host
이 파라미터는 세 번째 키 서버의 호스트 IP 주소를 지정합니다.
##### keysvr.third.port
이 파라미터는 세 번째 키 서버의 KRED(Key Request Encrypt Decrypt) 포트 번호를 지정합니다.
##### keysvr.third.credentials
이 파라미터는 세 번째 키 서버의 자격 증명을 지정합니다.
##### keysvr.third.con_timeout  [=5]
이 파라미터는 세 번째 키 서버의 연결 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.
##### keysvr.third.in_timeout  [=5]
이 파라미터는 세 번째 키 서버의 입력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.
##### keysvr.third.out_timeout  [=5]
이 파라미터는 세 번째 키 서버의 출력 시간 초과 값을 지정합니다. 단위는 초 입니다. 설정하지 않을 시 기본값은 5 입니다.

---
로그 관련 설정

---
##### trace_level  [=0]
이 파라미터는 로그 덤프 레벨을 설정합니다. 0 혹은 10의 값으로 사용합니다. 0 값은 장애 로그만 출력되며, 10의 값은 분석을 위한 상세 로그 데이터를 출력합니다. 
##### log_file_path  [=/tmp/petra_cipher_api.log]
이 파라미터는 로그 파일의 경로를 지정합니다.
##### same_err_no_log_interval  [=0]
이 파라미터는 동일한 오류 번호가 발생한 경우 로그에 기록되는 간격을 지정합니다. 단위는 초 입니다. 로그가 빈번하게 발생한다면 해당 값을 30 정도로 설정합니다.  

---
기타 설정

---
ip_prob_cmd_path  [= /usr/bin/who]
이 파라미터는 IP 주소를 검색하는 데 사용되는 명령어의 경로를 지정합니다. 세션을 얻을 때 IP 값을 사용하지 않으면 이 명령어로 IP를 추출하여 사용합니다. 
keysvr.sessions  [=1]
이 파라미터는 키 서버로 연결되는 최대 세션 수를 지정합니다. 일반적으로 1 이상의 값을 필요로 하지 않습니다. 
num_shared_session  [=1]
이 파라미터는 공유 세션의 수를 지정합니다. 


## 샘플 테스트
### 테스트 디렉토리 구조
```bash
$ tree
.
|-- lib64
|   `-- libpcjapi.so
|-- program.java
`-- sinsiway
    |-- PcaException.java
    |-- PcaSession.java
    `-- PcaSessionPool.java
```

### 구성 파일
```bash
$ cat /var/tmp/.petra/petra_cipher_api.conf
keysvr.primary.host = 192.168.10.94
keysvr.primary.port = 6002
keysvr.primary.credentials = Y8UdAzNpEDbO8bvMK5ez2W+buNUO8dShCJYgGO84B6y/waMSyTL/RdXzU1d39Pd0PfhNQZEw4LRHKJm5ySPN0kz+DGu/IGKAWbepbG9EgycA=AYQA
```

### 소스코드
vi program.java
```java
public class program {

  public static void main(String[] args) {
    try {
            
sinsiway.PcaSessionPool.initialize("/var/tmp/.petra/petra_cipher_api.conf", "");

      sinsiway.PcaSession session = sinsiway.PcaSessionPool.getSession(
        "127.0.0.1",
        "test",
        "program"
      );

      String encryptString = new String();
      String decryptString = new String();

      String keyName = new String("ARIA_256_b64");

      String plainString = new String("sinsiway petra cipher");
      encryptString = session.encrypt(keyName, plainString);
      decryptString = session.decrypt(keyName, encryptString);

      System.out.println("Original text: " + plainString);
      System.out.println("Encrypted text: " + encryptString);
      System.out.println("Decrypted text: " + decryptString);
    } catch (PcaException e) {
      System.out.println(
        "error_code = " + e.getErrCode() + "  error_message = " + e.getMessage()
      );
      return;
    }
  }
}
```

### 아카이브 파일 컴파일
```bash
$ javac -Xlint:unchecked sinsiway/*.java
$ jar -cvf0 lib64/PetraCipherAPI.jar ./sinsiway/*.class
```

### 소스코드 컴파일
```bash
javac -cp lib64/PetraCipherAPI.jar program.java
```

### 바이너리 실행
```bash
$ export LD_LIBRARY_PATH=./lib64
$ java ./program
Original text: sinsiway petra cipher
Encrypted text: vcUVmF09LkxN77fLiNlDVt+nXFhMJNhcivegvUzKKmA=
Decrypted text: sinsiway petra cipher
```