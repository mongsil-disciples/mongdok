# Docker & docker-compose install

## 1. 적절한 패키지 인덱스 및 설치 패키지를 업데이트한 후 HTTPS를 통해 저장소를 사용할 수 있도록 합니다.
```
 $ sudo apt-get update
 $ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

## 2. docker의 공식 GPG키를 추가한다.
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## 3. stable repository를 세팅하기 위한 명령어를 실행한다.
```
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

## 4. 가장 최신 버전의 docker 엔진을 설치한다.
```
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## 5. docker 설치 확인
```
$ docker -v
```

## 6. docker-compose의 현재 안정적인 릴리스를 다운로드 합니다.
```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

## 7. docker-compose의 파일 권한을 부여합니다.
```
$ sudo chmod +x /usr/local/bin/docker-compose
```

## 8. docker-compose 설치여부를 확인합니다.
```
$ docker-compose --version
docker-compose version 1.29.1, build 1110ad01
```