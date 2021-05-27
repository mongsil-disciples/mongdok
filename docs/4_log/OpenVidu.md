# OpenVidu 서버 구축

## 1. 기본환경 설정

### JDK + Maven설치
```
sudo apt-get install -y openjdk-11-jdk
sudo apt-get install -y maven
```

## 2. OpenVidu Clone
```
mkdir openvidu-server
cd openvidu-server/
git clone https://github.com/OpenVidu/openvidu.git
```

## 3. Configuration
```
cd src/main/resources
vim application.properties
```

### application.properties 설정
* DOMAIN_OR_PUBLIC_IP=k4a401.p.ssafy.io
* OPENVIDU_SECRET=MY_SECRET
* KMS_URIS=["ws://k4a401.p.ssafy.io:8888/kurento"]

### application-container.properties 설정
* DOMAIN_OR_PUBLIC_IP=k4a401.a.ssafy.io
* OPENVIDU_SECRET=MY_SECRET
* HTTPS_PORT=4443

## 2. On-premise에 OpenVidu Deploy(1번 방법과 다른 방법이다.) - LINUX(Amazon EC2)
### reference
[deploying-on-premises](https://docs.openvidu.io/en/2.13.0/deployment/deploying-on-premises)

### Prerequisites
* [Install docker & docker-compose](https://lab.ssafy.com/s04-final/s04p31a401/blob/develop/docs/4_log/Docker.md)

### Configure a Domain Name
OpenVidu는 WebRTC를 사용해야 하므로 HTTPS를 사용하여 배포됩니다. 만약 도메인 이름이 없으면 자동 생성된 SSL인증서가 사용되고 사이트에 들어가면 사용자에게 보기 흉한 경고가 나타납니다. 그리고 물론 중간에서 공격을 받을 수도 있습니다. 따라서 컴퓨터의 공용 IP를 가리키는 도메인 이름을 구성하는 것이 좋습니다. 설치 프로세스에서 암호화를 사용하여 유효한 SSL인증서를 자동으로 생성할 수 있습니다. 고유하고 유효한 SSL 인증서가 이미 있는 경우 해당 인증서를 구성할 수도 있습니다.

### Port configuration in the server
외부 공격을 방지하기 위해 포트 닫기 섹션에는 방화벽을 구성하는 ufw샘플을 가지고 있습니다.
* 22 TCP: to connect using SSH to admin OpenVidu.
* 80 TCP: if you select Let's Encrypt to generate an SSL certificate this port is used by the generation process.
* 443 TCP: OpenVidu server and application are published by default in standard https port.
* 3478 TCP+UDP: used by TURN server to resolve clients IPs.
* 40000 - 57000 TCP+UDP: used by Kurento Media Server to establish media connections.
* 57001 - 65535 TCP+UDP: used by TURN server to establish relayed media connections.

### Close all other ports
OpenVidu 내부 서비스에 대한 외부 공격을 피하는 것이 매우 중요합니다. [자세한 내용](https://docs.openvidu.io/en/2.17.0/deployment/deploying-on-premises/#close-ports-to-avoid-external-attacks)을 보려면 포트 닫기 섹션을 선택하여 외부 공격을 방지합니다.

### Free ports inside the server
OpenVidu 플랫폼 서비스를 사용하려면 시스템에서 80, 443, 3478, 5442, 5443, 6379 및 8888 포트를 사용할 수 있어야 합니다. 이러한 포트 중 일부를 프로세스에서 사용하는 경우 OpenVidu 플랫폼이 올바르게 작동하지 않습니다. OpenVidu를 설치하기 전에 시스템에 NGINX 프로세스가 있는 것은 일반적인 오류입니다. 제거하십시오.
```
$ sudo apt-get remove nginx nginx-common # 설정 파일을 제외한 모든 파일을 제거합니다.
$ sudo apt-get purge nginx nginx-common  # 모든 것을 제거합니다.
$ sudo apt-get autoremove # 위의 명령을 사용한 후에는 더 이상 필요하지 않은 nginx에서 사용하는 종속성을 제거하기 위해이 명령을 사용하십시오.
```

## Deployment
### Root Permission
```
$ sudo su
```

### Change Path
openvidu를 설치하는 권장 폴더는 /opt입니다. On Premise와 관련된 문서의 모든 지침은 이 설치 경로로 가정한다.
```
$ cd /opt
```

### Installation
다음 명령을 실행하여 설치 스크립트를 다운로드하고 실행합니다.
```
curl https://s3-eu-west-1.amazonaws.com/aws.openvidu.io/install_openvidu_latest.sh | bash
```
이렇게 하면 모든 필수 파일이 openvidu폴더로 다운로드 되고 아래와 같이 기본적인 명령어 메시지가 나타납니다.
```
=======================================
Openvidu Platform successfully installed.
=======================================

1. Go to openvidu folder:
$ cd openvidu

2. Configure DOMAIN_OR_PUBLIC_IP and OPENVIDU_SECRET in .env file:
$ nano .env

3. Start OpenVidu
$ ./openvidu start

For more information, check:
https://docs.openvidu.io/en/2.17.0/deployment/deploying-on-premises/
```