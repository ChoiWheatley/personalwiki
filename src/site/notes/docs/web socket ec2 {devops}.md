---
{"dg-publish":true,"permalink":"/docs/web socket ec2 {devops}/","title":"web socket ec2 {devops}"}
---

- [[docs/week14-18 {swjungle}{my own weapon}{nestjs, socketio}\|week14-18 {swjungle}{my own weapon}{nestjs, socketio}]]
___

## README

본 문서는 [[docs/week14-18 {swjungle}{my own weapon}{nestjs, socketio}\|week14-18 {swjungle}{my own weapon}{nestjs, socketio}]] 나만의 무기 만들기 프로젝트때 배포서버에 웹 소켓 프로토콜을 위한 로드 밸런서를 달기 위해서 삽질하다가 만들었습니다.

## 리스너 규칙

- [리스너 규칙 분석한 블로그](https://isn-t.tistory.com/35)

신기하게도, 리스너 규칙에 `Host`는 서브도메인으로 분리할 수도 있었다. 현재 나는 서브도메인을 Route53을 통해서 분리해놓았는데, 하나의 EC2 서버 안에서 두 서비스를 운영하는 경우(지금이 그렇다..!) 이 방법으로 적용해도 되겠다

## Try-Catch

**2023-11-25**

[다음 블로그](https://velog.io/@jupiter-j/Project-webrtc-ec2-%EC%8B%A4%ED%96%89) 글을 확인하며 웹 소켓 포트인 3002번에 대응하는 타겟그룹을 HTTP/S에 사용되는 일반적인 녀석으로 설정했다.

![recre-websocket-tg.jpg](/img/user/docs/assets/recre-websocket-tg.jpg)

브라우저는 wss 프로토콜로 요청을 계속 보내는데, Nestjs 서버는 반응을 안한다..

이게 보니까 타겟그룹을 HTTPS:3002 포트로 보내버려서 Nestjs 서버가 요청을 받지 못했던 것이다. 따라서 이를 HTTP:3000으로 수정했더니 101 Switching Protocols 응답을 확인했다.

하지만,

프로토콜 변경 이후에 Nestjs 콘솔에 로그가 찍히지 않는다..! nmap으로 ec2에 소켓 포트로 요청이 들어오는지 검사해봐야겠다.
