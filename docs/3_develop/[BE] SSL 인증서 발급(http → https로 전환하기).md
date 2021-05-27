# [BE] SSL 인증서 발급(http → https로 전환하기)

위 [FE] SSL 인증서 발급(http → https로 전환하기) 에서 ssl인증서까지는 했으니까

### **Spring boot에서 인증서를 적용**

### 1. **Spring Boot 설정**

![Untitled](https://user-images.githubusercontent.com/43662673/115957358-dc71d300-a53c-11eb-9364-910d0cacab39.png)

Spring Boot를 실행합니다. 그후 `resources`하위에 `keystore.p12`를 드래그 드롭합니다. 그다음 [application.properties](http://application.properties) (나뭇잎) 파일을 열어 그림과 같이 설정합니다.

[![image](https://user-images.githubusercontent.com/43662673/115957383-07f4bd80-a53d-11eb-9466-778f02f9b37b.png)](https://t1.daumcdn.net/cfile/tistory/9926A4475D4C1B6C18)

그 후 위와 같이 간단히 Controller를 생성합니다.

![image](https://user-images.githubusercontent.com/43662673/115957390-14791600-a53d-11eb-9e55-1155ebef8e87.png)

서버를 실행한 뒤, 위와 같이 도메인을 입력하여 접속합니다. ([https://localhost:443](https://localhost/)) 443은 생략가능합니다.