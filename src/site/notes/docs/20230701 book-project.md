---
{"dg-publish":true,"permalink":"/docs/20230701 book-project/","title":"20230701 book-project"}
---

- [[docs/EC2 Postgresql을 장고 기본 데이터베이스로 활용하기\|EC2 Postgresql을 장고 기본 데이터베이스로 활용하기]] 해결
- [[docs/aws s3 static files in django\|aws s3 static files in django]]
{ #w5jgh9}

	- 지금 도커(로컬)에서의 문제상황이... media 파일들은 잘 S3 URL에 요청을 하고 있는데, js 파일들은 로컬URL을 요청하고 있다는 것이다. 왜 `docker-compose up -d --build`를 하는데 문제가 발생한 거지?
	- `STATIC_ROOT` 설정이 제대로 안 됐나?
	- [[docs/docker-compose 명령어 모음\|docker-compose 명령어 모음]]
