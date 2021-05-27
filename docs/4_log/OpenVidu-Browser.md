# OpenVidu 클라이언트

- 오픈바이두 플랫폼 퍼포먼스

[OpenVidu load testing: a systematic study of OpenVidu platform performance](https://openvidu.medium.com/openvidu-load-testing-a-systematic-study-of-openvidu-platform-performance-b1aa3c475ba9)

# 개발 관련 메모

[OpenVidu Browser - v2.17.0](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/index.html)

## 영상 관련 설정 PublisherProperties

[https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/interfaces/publisherproperties.html](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/interfaces/publisherproperties.html)

- 영상 해상도 설정

```jsx
publisher = OV.initPublisher('publisher', {
                    audioSource: undefined, // The source of audio. If undefined default audio input
                    videoSource: undefined, // The source of video. If undefined default video input
                    publishAudio: true,     // Whether to start publishing with your audio unmuted or not
                    publishVideo: true,     // Whether to start publishing with your video enabled or not
                    resolution: '640x480',  // The resolution of your video
                    frameRate: 30,          // The frame rate of your video
                    insertMode: 'APPEND',   // How the video is inserted in target element 'video-container'
                    mirror: true            // Whether to mirror your local video or not
                });
```

Resolution of the video: `"320x240"`, `"640x480"`, `"1280x720"` (low, medium and high quality respectively)

default `"640x480"`

- 프레임 속도 frameRate

브라우저마다 default가 다름. chrome의 경우 사용자 컴퓨터의 성능에 따라 자동으로 선택함

- 오디오 설정 publishAudio
- 삽입 모드 InsertMode

    [https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html)

    해당 DOM에 어떤식으로 삽입될 것인지 명시

    - [AFTER](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html#after)
    - [APPEND](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html#append)
    - [BEFORE](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html#before)
    - [PREPEND](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html#prepend)
    - [REPLACE](https://docs.openvidu.io/en/2.17.0/api/openvidu-browser/enums/videoinsertmode.html#replace)

## 세션 Session

connect

disconnect

- 방안의 모든 참가자들이 서로를 `구독`하고 있음
- 연결이 끊기면 로컬 참가자의 세션 개체는 세션 연결 끊김 이벤트를 발송함
    - 이 이벤트는 세션의 모든 구독자 개체로부터 이탈 참가자를 자동으로 취소함
    - 또한 웹RTC peer 연결을 종료하고 각 구독자와 관련된 HTML 비디오 요소도 삭제함

forceDisconnect

- 강제로 영상 송출이 불가능하게 함

signal

- [https://docs.openvidu.io/en/2.17.0/cheatsheet/send-messages/](https://docs.openvidu.io/en/2.17.0/cheatsheet/send-messages/)
- 사용자간 문자 메시지 보낼 수 있음

subscribe

- HTML 비디오 요소 관련,,

## 백엔드와 소통

```jsx
/**
 * --------------------------
 * SERVER-SIDE RESPONSIBILITY
 * --------------------------
 * These methods retrieve the mandatory user token from OpenVidu Server.
 * This behavior MUST BE IN YOUR SERVER-SIDE IN PRODUCTION (by using
 * the API REST, openvidu-java-client or openvidu-node-client):
 *   1) Initialize a session in OpenVidu Server	(POST /api/sessions)
 *   2) Generate a token in OpenVidu Server		(POST /api/tokens)
 *   3) The token must be consumed in Sessi1on.connect() method
 */
```