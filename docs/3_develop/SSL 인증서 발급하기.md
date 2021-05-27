# SSL 인증서 발급 (http → https로 전환하기)

1. 예전 방법

    ```
    $ wget https://raw.githubusercontent.com/certbot/certbot/7f0fa18c570942238a7de73ed99945c3710408b4/letsencrypt-auto-source/letsencrypt-auto -O /opt/certbot-auto

    $ chmod 755 /opt/certbot-auto

    $ mv /opt/certbot-auto /기존설치경로/certbot-auto
    ```

2. certbot 홈페이지 가서 하라는 대로 하기

    우리 서버는 ubuntu 20.04니까

    ![https://user-images.githubusercontent.com/43662673/112248319-124f3d80-8c99-11eb-9226-5a855c359aeb.png](https://user-images.githubusercontent.com/43662673/112248319-124f3d80-8c99-11eb-9226-5a855c359aeb.png)

    위와 같이 들어가서 하라는 대로 따라한다.

    ```
    $ sudo snap install core; sudo snap refresh core
    $ sudo snap install --classic certbot
    $ sudo ln -s /snap/bin/certbot /usr/bin/certbot
    $ sudo certbot --nginx
    ```

![https://user-images.githubusercontent.com/43662673/112247741-2e9eaa80-8c98-11eb-9105-563d0357961a.png](https://user-images.githubusercontent.com/43662673/112247741-2e9eaa80-8c98-11eb-9105-563d0357961a.png)

```
# openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out keystore.p12 -name airpageserver -CAfile chain.pem -caname root
```

![https://user-images.githubusercontent.com/43662673/112248011-93f29b80-8c98-11eb-9577-e12008deb9fc.png](https://user-images.githubusercontent.com/43662673/112248011-93f29b80-8c98-11eb-9577-e12008deb9fc.png)

비밀번호는 귀찮으니 그냥 root로 ㅎㅎ

어쨌든 위의 명령어를 치고 나면 keystore.p12가 생성된다.

![https://user-images.githubusercontent.com/43662673/112248118-c0a6b300-8c98-11eb-884b-a3bc1da1202c.png](https://user-images.githubusercontent.com/43662673/112248118-c0a6b300-8c98-11eb-884b-a3bc1da1202c.png)

mv하라고 하지만 무서우니까 cp로 home 디렉토리로 이동

![https://user-images.githubusercontent.com/43662673/112248175-df0cae80-8c98-11eb-946a-6b5bd0533088.png](https://user-images.githubusercontent.com/43662673/112248175-df0cae80-8c98-11eb-946a-6b5bd0533088.png)

그런 다음 사이트로 이동해서 확인

```jsx
https://j4a401.p.ssafy.io/
```

리다이렉트 후

```jsx
[http://j4a401.p.ssafy.io/](http://j4a401.p.ssafy.io/) -> https://j4a401.p.ssafy.io/ 이동됨 확인하기
```