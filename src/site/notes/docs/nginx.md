---
{"dg-publish":true,"permalink":"/docs/nginx/","title":"nginx"}
---

일단 nginx는 전형적인 웹 서버이다. 웹 서버는 정적 웹을 호스팅하는 서버로, URL 형식을 바꾸거나 내부적으로 리디렉션을 처리하거나 여러대의 서버를 매핑하는 등의 일을 수행한다.

단순히 정적 파일을 호스팅하기만 했으면 아무도 거들떠 보지도 않았을 것이다. 웹 서버의 진가는 바로 **리버스 프록시**에 있다.

리버스 프록시는 포워드 프록시, 즉 그냥 프록시가 클라이언트에 붙어서 요청을 처리하는 것에 반해 WAS(Web Application Server)에 붙어서 요청을 처리하는 것을 의미한다. WAS로는 장고, 스프링, NodeJS 등이 있다. 

프록시라는 이름 자체는 일종의 메시지 전달과정에서의 중간자라는 뜻이다. 클라이언트에 붙는 포워드 프록시의 경우 클라이언트 트래픽을 감시하거나 악의적인 클라이언트 공격을 막아내는 등의 역할을 할 수 있다. 회사 내의 컴퓨터로 인터넷에 접속할때 프록시를 경유하여 인증된 안전한 사이트만 접속하도록 강제하는 것을 예로 들 수 있다.

리버스 프록시는 백엔드 서버들을 연결하는데 사용된다. 응답들을 캐싱하여 성능을 향상할 수도 있다. 많은 유저를 감당하여야 하는 대형 서버를 운영할 경우, 같은 기능을 담당하는 여러대의 서버 중 idle한 서버에게 요청을 전가하는 일을 맡을 수도 있는데, 이것이 바로 **로드 밸런싱**이다. **게이트웨이**의 역할도 할 수 있다. API 게이트웨이는 클라이언트에 단일 주소를 제공하고 클라이언트 요청을 적절한 서비스로 라우팅하는 역할을 한다. 하나의 도메인에 여러 서비스(앱)을 제공해야 하는 경우, 게이트웨이를 사용해야한다.

# Blocks

<https://docs.nginx.com/nginx/admin-guide/web-server/web-server/>

- **`server`** | [docs](https://nginx.org/en/docs/http/ngx_http_core_module.html#server) | nginx 서버가 요청을 보낼 가상 서버를 정의한다. 동일 기계일 경우 포트번호를 다르게 할 수 있으며, 아예 외부 링크를 연결해 줄 수도 있다.
	- **`listen`** 주어진 포트를 개방한다.
	- **`location`** URI를 재배치한다. 예를 들어 `/` 요청을 `/data/www/` 쪽으로 보내고 싶은 경우, `/images/`  요청을 `/data/` 쪽으로 보내고 싶은 경우 활용 가능하다.
- context: 
- **`upstream`** | [docs](https://nginx.org/en/docs/http/ngx_http_upstream_module.html#upstream) | 여러대의 `server`를 정의하는 묶음이다. 위에서부터 차례로 읽어가며 로드 밸런싱을 진행한다.
- 

## Troubleshooting

[[docs/Nginx가 multipart-form-data 요청을 제대로 전달하지 못하는 문제\|Nginx가 multipart-form-data 요청을 제대로 전달하지 못하는 문제]]