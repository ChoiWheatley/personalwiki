---
{"dg-publish":true,"permalink":"/docs/2024-03-09 wishfunding pagination, reqtype, 친구API, 배송지 API, 서버 플랫폼 구축/","title":"2024-03-09 wishfunding pagination, reqtype, 친구API, 배송지 티AP,I서버 플랫폼 구축끌모아펀딩 회의록"}
---

---
- pagination on notification API  
- notification 백에서 이름을 맞춰야 할 것 같다. 알림문구 처리해야 할 때  
- 들어오는 친구요청  
- 내 요청에 대한 친구의 수락 / 거절  
- 내 펀딩의 마감기한 (actor: System)  
- 내 펀딩 달성: 마감기한 상관없이 100% 채워지면 자동으로 append  
- 내가 후원한 펀딩 마감  
- 감사인사 작성권유 (펀딩 마감시 자동으로 추가)  
- 내가 개설한 펀딩이 새로운 후원이 들어왔을 때 =>  
- ReqType 의미: (나와 친구 사이의 관계를 정의). OR (감사인사 작성하기 상태를 정의).  
프론트에서 notiType에 따라서 사용하는 reqType도 달라지니까 이거 잘 구분해서 써야할 듯. 감사인사 작성 상태에 따라 JOIN해야 하는 테이블들이 다 달라가지고 알림목록 넘기는게 오래 걸릴 것 같아서 알림 보여줄 때 감사인사가 작성됐는지 아닌지, 응답을 했는지 안했는지를 자체적으로 가지고 있는다.  
notiType에 따라서 알림 카드를 눌렀을 때 redirect 되는 페이지가 다름. 버튼 말고 알림 자체를 클릭하면 펀딩상세페이지로 넘어가는 것이 맞다고 생각함. subId의 의미가 그런거임.  

> Q. 메인에서 다른사람들의 펀딩 리스트를 일부만 보여줄때 메인에서 받는 펀딩 리스트들의 정보를 요청하는 API는 어떻게 하는가? => pagination  

- /api/user/:userId/fundings => /api/fundings 와 충돌하는듯. 하나의 API에서 할 수 있는 일이 많아지는 거잖아. => DB 접근하는 게 async라서 문제없음. => 프로필 페이지에서 보일 진행중인 / 종료된 펀딩들 각각 API를 두 개 보내서  
- 썸네일용 이미지는 저해상도로 저장해놓고 빨리 불러오게끔.  
- banktype enum 추가함. 배송지랑 계좌랑 연관된 API가 필요할지도..  

### /api/friend  

- userId가 friendId에게 '어떤'요청을 보냅니다. 근데 상태가 세가지가 있음. Friend: 친구인 상태, Rejected: 거절, Request: 요청  
- 수락 거절 구분을 의한 `isAccepted` 칼럼을 추가함. Nullable  
- 친구검색 기능이 있어야 하지 않을까?  

## 배송지 관련 API  

### /api/address/ GET  

- access token만 있으면 바로 사용자의 주소 얻어올 수 있음.  
- 주소검색은 외부 API 알아낸 뒤 어떤 response가 튀어나오는지 알아봐야 함.  
- 세준이가 나머지 API세부 추가할 예정.  
  
Q. 내가 펀딩을 올린 후원에 금액이 다 모으면 남은 금액은 계좌로 쏘고 우리가 비회원으로 주문하고 **주문번호**를 고객한테 넘겨주면 고객이 언제 오는지 배송추적 할 수 있으니까. 반품요청할 때엔 돈이 우리한테 돌아오니까.  
  
- AccessToken에 어떤 정보를 넣을지도 생각해봐야함.

## 서버 및 플랫폼 구축  

~~RDS postgresql 프리티어 쓰기 위해선 사용하는 엔진의 버전을 낮추어야 한다. 12버전  ~~

> The Amazon RDS Free Tier is available to you for 12 months. Each calendar month, the free tier will allow you to use the Amazon RDS resources listed below for free:  
>   
> 750 hrs of Amazon RDS in a Single-AZ db.t2.micro, db.t3.micro or db.t4g.micro Instance.  
> 20 GB of General Purpose Storage (SSD).  
> 20 GB for automated backup storage and any user-initiated DB Snapshots.  

금액이 떠도 상관 ㄴㄴ해.

## 하루 끝나기 전 마지막 목표

- [ ] funding API Pagination, TypeORM을 뺀 기능 작동하게 만들자
- [x] .env 로드 [[docs/Nest .env 파일 관리법 (.dev.env, .local.env 등등)\|Nest .env 파일 관리법 (.dev.env, .local.env 등등)]]
