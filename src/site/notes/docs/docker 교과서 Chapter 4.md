---
{"dg-publish":true,"permalink":"/docs/docker 교과서 Chapter 4/","title":"docker 교과서 Chapter 4"}
---


## 도커를 빌드 도구로 활용하기

- 소프트웨어 빌드 도구로 활용 가능한 도커
	- 빌드 과정이 복잡한 경우 중간에 사용하느 빌드 도구의 환경을 동일하게 맞추는 것도 어려울 수 있다. 이 경우 빌드 툴체인을 공유할 수 있다. 
	- 예를 들어 프로그램을 빌드 하기 위해 참여하는 링커, 컴파일러, 패키지 관리자, 런타임 환경 전부 도커파일 안에 정의할 수 있다.
- 빌드 도구와 도커 스테이징은 무슨 관계이지?
	- 각 스테이지별로 사용하는 기반 이미지 `FROM`이 다를수도 있다. 이 경우 기반 이미지를 한데 모아서 큰 기반 이미지를 만들어도 되지만 스테이징을 하여 관리할 수도 있다.
	- 각 단계별로 목적이 뚜렷한 경우 스테이징 할 수 있다. 빌드 스테이지, 테스트 스테이지 등과 같이 말이다. 이때 각 스테이징을 위해 사용하는 기반 이미지에 별칭을 붙일 수 있는데, `AS` 키워드를 사용할 수 있다.
		- `AS` 키워드로 정의한 스테이지 별칭은 `COPY --from=<stage>` 에서 참조할 수 있다. 이전 스테이지의 산출물을 공유하지 않기 때문에 꼭 `COPY` 명령어를 써주는 것 같다.
- `RUN` 인스트럭션은 컨테이너 안에서 실행할 명령어를 정의한다. 셸 스크립트로 작성한다.

```mermaid
flowchart TD
    subgraph Build Stage
        A[Input: diamol/base] --> B[RUN echo 'Building...' > /build.txt]
        B --> C[Output: /build.txt]
    end

    subgraph Test Stage
        D[Input: diamol/base + /build.txt from Build Stage] --> E[RUN echo 'Testing...' >> /build.txt]
        E --> F[Output: /build.txt]
    end

    subgraph Final Stage
        G[Input: diamol/base + /build.txt from Test Stage] --> H[CMD cat /build.txt]
        H --> I[Output: /build.txt displayed]
    end

    C --> D
    F --> G
```

- 빌드 서버는 소스코드와 도커파일을 가지고  `docker build`를 하여 아티팩트가 포함된 이미지를 생성한다.
- 배포서버는 아티팩트가 포함된 이미지를 pull 받아 단순히 `doker run`을 한다.
- 위 두 작업을 자동화 해주는 녀석이 CI (Continuous Integration) 인 것이다.

## CMD와 ENTRYPOINT의 차이점이 뭔가요?

### Key Differences:

1. **Overriding**:
    - `CMD` can be overridden by providing a command at the end of `docker run`.
    - `ENTRYPOINT` cannot be overridden by `docker run` arguments (unless you explicitly use `--entrypoint`).
2. **Intent**:
    - Use `CMD` for default, flexible commands that can be overridden.
    - Use `ENTRYPOINT` when you want a fixed command that will always run.

In summary, `CMD` is better suited for default commands that can be changed, while `ENTRYPOINT` is used for mandatory commands that should always be executed when the container starts.

## 도커 가상 네트워크

<https://docs.docker.com/engine/network/>

도커 컨테이너끼리 통신을 주고받기 위해선 가상 네트워크 (로컬 네트워크)를 구축하고 그 안에 컨테이너들을 할당해주어야 한다. 그러면 그 안에서 가상 IP주소를 발급받게 되고 EXPOSE한 포트번호를 통하여 네트워크 통신을 하게 된다.

```
docker container network <docker-network-name>
```

> [!question] docker network 안에 정의된 컨테이너끼리 요청을 주고받는 챕터 4.4가 이해가 안된다. image-gallery도 컨테이너 안에서 80번 포트를 listen하고 access-log도 컨테이너 안에서 80번 포트를 listen한다. 단지 EXPOSE하는 포트가 다를 뿐이다. 

⇒ 같은 네트워크일뿐 같은 컨테이너가 아니기 때문에 가능한 일이다.

> [!question] image-gallery 프로젝트의 `main.go` 파일을 보면 POST 요청을 보내는 대상이 `ACCESS_API_URL`이다. 값이 `http://accesslog/access-log`로 되어있다.  엉뚱한 곳으로 POST를 보내고 있는거 아닌가?

⇒ access-log 프로젝트를 실행할때 옵션을 다시 살펴보자. 

```
docker container run --name accesslog -d -p 801:80 --network nat access-log
```

`http://accesslog`는 같은 네트워크 nat 안에 정의된 호스트를 제일 먼저 찾게된다. 그래서 컨테이너 이름으로 정의된 `accesslog`를 찾게되어 localhost로 변환해준 뒤에 801번 포트로 POST 요청을 보내게 된 것이다.

> containers can communicate with each other using container IP addresses or container names. [docker#user-defined-networks](https://docs.docker.com/engine/network/#user-defined-networks)

## 멀티스테이지빌드는 각각의 스테이지가 별도의 이미지로 분리된다고?

> p.99 최종 애플리케이션 이미지에 Go 빌드 도구가 포함이 되지 않아 750MB나 달하는 용량을 줄일 수 있는 것이다.

그 증거로 다음 명령어를 통해서 이미지별 정보를 출력해보면...

```
$ docker image ls -f reference=diamol/golang -f reference=image-gallery
REPOSITORY      TAG       IMAGE ID       CREATED              SIZE
image-gallery   latest    12b68e489c57   About a minute ago   17.1MB
diamol/golang   latest    119cb20c3f56   4 years ago          803MB
```

go 프로젝트 배포를 위한 Dockerfile은 두 가지 스테이지로 구분되어있다.

1. golang 빌드 ⇒ `FROM diamol/golang` | SIZE 803MB
2. go 바이너리 실행 ⇒ `FROM diamol/base` | SIZE 17.1MB

이렇게 하면 이미지를 배포할때 굳이 필요없는 빌드도구를 포함하지 않고 가벼운 상태로 레지스트리에 올리고 실행할때에도 용량을 적게 먹을 것 같다.

## 연습문제

> [!note] 다음 도커파일을 빌드하면 이미지가 500MB가 된다.  도커파일을 수정하여 이미지 크기를 약 20MB 정도로 최적화하고 HTML 파일이 변경되어도 재수행하는 빌드 단계가 한단계가 되도록 하라.

```Dockerfile
FROM diamol/golang 

WORKDIR web
COPY index.html .
COPY main.go .

RUN go build -o /web/server
RUN chmod +x /web/server

CMD ["/web/server"]
ENV USER=sixeyed
EXPOSE 80
```

**1. HTML 파일이 변경되어도 재수행하는 빌드 단계가 한 단계가 되도록 하는 방법은 `COPY index.html .` 명령을 맨 뒤로 옮기면 된다.**

```diff
 FROM diamol/golang

 WORKDIR web  
-COPY index.html .  
 COPY main.go .

 RUN go build -o /web/server

 CMD ["/web/server"]  
 ENV USER=sixeyed  
+COPY index.html .^M  
```

**2. 이미지의 크기를 줄이기 위해서는 멀티 스테이지 빌드 전략을 취하면 된다.**

```diff
-FROM diamol/golang
+FROM diamol/golang AS builder

 WORKDIR web
 COPY main.go .

 RUN go build -o /web/server
 RUN chmod +x /web/server

+FROM diamol/base

 CMD ["/web/server"]
 ENV USER=sixeyed
 EXPOSE 80
 
+WORKDIR web
+COPY --from=builder /web .
COPY index.html .
```

 이제 이미지 빌드 결과가 다음과 같이 16.9MB가 되었다:

```
REPOSITORY   TAG            IMAGE ID       CREATED              SIZE
ch04-lab     choiwheatley   33a8bc68d237   About a minute ago   16.9MB
```

**3. 마지막으로 빌드 레이어의 수를 줄여보자.**

굳이 builder 스테이지에서 WORKDIR을 정의할 필요는 없다.

```diff
 FROM diamol/golang AS builder
 
-WORKDIR web
 COPY main.go .

-RUN go build -o /web/server
-RUN chmod +x /web/server
+RUN go build -o /server
+RUN chmod +x /server

 FROM diamol/base

@@ -13,5 +12,5 @@ ENV USER=sixeyed
 EXPOSE 80

 WORKDIR web
-COPY --from=builder /web .
+COPY --from=builder /server .
 COPY index.html .
```

이렇게 하면 빌드 레이어가 12스텝에서 11스텝으로 줄었다.
