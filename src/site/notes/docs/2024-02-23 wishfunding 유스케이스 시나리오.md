---
{"dg-publish":true,"permalink":"/docs/2024-02-23 wishfunding 유스케이스 시나리오/","title":"2024-02-23 wishfunding티끌모아펀딩 유스케이스 시나리오"}
---


### before meeting

티끌모아펀딩 유스케이스 시나리오

#### 액터  

- fundraiser: 펀딩을 기획하는 자. 예상유저로는 생일자, 결혼당사자, 모금활동을 진행하는자  
- patron: 후원자. 펀딩에 응하여 fundraiser에게 돈을 지불할 용의가 있는 자  
- manager: 펀딩 서비스 관리자. 유저들과의 상담 진행, 펀딩 현황 관리, 만기 펀딩에 대한 후속조치 진행(상품 배송, 추가입금요구, 송금)  

#### 유스케이스  

- fundraiser “create a new funding":  
user preferences, list of (선물 구매링크, 목표펀딩금액, 선물 이미지), 기한일, 펀딩 제목, 펀딩 게시글, 공개여부 설정
  
- fundraiser "set default user preferences":  
선물 수령자 이름, 선물 수령 주소, 크레딧 환급시 필요한 계좌: { 은행, 계좌번호 }, 수령자의 전화번호

- fundraiser "copy url for funding"  
펀딩현황을 공유하고 엉뚱한 선물을 받지 않기 위해선 fundraiser는 자신의 펀딩페이지를 주변 사람들에게 공유하여야 한다. 그 과정을 간소화 하기 위해서 url 복사버튼이 존재해야 한다.

- fundraiser "add new article for a funding":  
펀딩 페이지에 펀드기획자는 게시글을 추가로 올릴 수 있다.
  
- patron "invest a funding"  
결제옵션 선택(카카오페이, 네이버페이, stripe), 결제금액 선택, 후원카드 선택, 후원카드에 넣을 한 마디 작성, 결제 실패/성공시 안내받을 연락처, (로그인 된 상태라면) 사용할 크레딧 설정
  
- patron "leave a message on articles"  
fundraiser가 올린 게시글에 댓글을 단다.

- patron "subscribe new event for a funding"  
후원자는 펀딩에 대하여 알림을 신청할 수 있다. 카카오톡채널을 통해 알림을 받을 수도 있고, 이메일을 통하여 받을 수도 있다. 

- funraiser | patron "ask a question to a manager"  
시스템만으론 알 수 없는 현황을 문의할 수 있다. 문의 시스템의 품질이 곧 본 서비스의 품질과도 직결되는 문제일 것이다. 배송추적, 상품 문제 등등에 관한 트러블슈팅, 크레딧 환불 등등
