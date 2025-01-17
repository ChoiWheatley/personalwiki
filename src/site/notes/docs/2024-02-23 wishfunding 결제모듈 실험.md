---
{"dg-publish":true,"permalink":"/docs/2024-02-23 wishfunding 결제모듈 실험/","title":"2024-02-23 wishfunding티끌모아펀딩 결제모듈 실험"}
---


- [카카오페이 개발자센터](https://developers.kakaopay.com/docs/payment/online/common)
	- 애플리케이션 등록 → Client ID, Secret Key 발급하여 Mockup 결제 페이지로 넘어감  
	- [가맹점 심사](https://biz.kakaopay.com/applications) → CID 가맹점 코드를 발급받아 사업자 등록을 완료하여야 함. 크라우드 펀딩과 같이 서비스 제공 완료 기간이 길거나 불명확한 경우 심사 빠꾸먹을 수도 있다고. 그런데 [프레제뉴](https://www.bizno.net/article/6073676144) 는 "도매 및 소매업"으로 올렸더라
- [네이버페이센터](https://developer.pay.naver.com/introduce/naverpay)
	- [결제형 vs 주문형 차이](https://admin.pay.naver.com/notice/view?id=200010243) 
		- 주문형은 '네이버페이 구매하기' 버튼이 노출되는 쇼핑몰
		- 결제형은 자사몰 주문서 내 결제수단으로 '네이버페이'가 제공되는 유형.
	- ![스크린샷 2024-02-23 오후 5.04.46.png|400](/img/user/docs/assets/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202024-02-23%20%EC%98%A4%ED%9B%84%205.04.46.png)
		- 네이버페이 서비스를 위한 네이버 회원가입을 따로해야되나봄. 단체회원 가입시에 사업자 등록번호를 작성해야 해서 더 이상 넘어가지 못했음.

- [국세청 / 사업자등록 신청](https://www.nts.go.kr/nts/cm/cntnts/cntntsView.do?mi=2444&cntntsId=7777)

## Before 사업자등록

mock 결제페이지 정도는 카카오나 네이버나 다 지원함. 아래에 결제플로우에 관하여 서술하겠음.

- [카카오페이 / 온라인 결제 / 단건 결제](https://developers.kakaopay.com/docs/payment/online/single-payment)

request:

```json
{
"cid": "TC0ONETIME",
"partner_order_id": "partner_order_id",
"partner_user_id": "partner_user_id",
"item_name": "itemName",
"quantity": 100,
"total_amount": 10000,
"tax_free_amount": 10000,
"approval_url": "{{APPROVAL_URL}}",
"cancel_url": "{{CANCEL_URL}}",
"fail_url": "{{FAIL_URL}}"
}
```

response:

```json
{

"tid": "T5df1cc6196d5d20e31e",

"tms_result": false,

"created_at": "2024-02-28T20:45:10",

"next_redirect_pc_url": "https://online-pay.kakao.com/mockup/v1/12618e7f0f21086a0173f2c2d68032deb64f7cfd7103f86aa476531c1344d562/info",

"next_redirect_mobile_url": "https://online-pay.kakao.com/mockup/v1/12618e7f0f21086a0173f2c2d68032deb64f7cfd7103f86aa476531c1344d562/mInfo",

"next_redirect_app_url": "https://online-pay.kakao.com/mockup/v1/12618e7f0f21086a0173f2c2d68032deb64f7cfd7103f86aa476531c1344d562/aInfo",

"android_app_scheme": "kakaotalk://kakaopay/pg?url=https://online-pay.kakao.com/pay/mockup/12618e7f0f21086a0173f2c2d68032deb64f7cfd7103f86aa476531c1344d562",

"ios_app_scheme": "kakaotalk://kakaopay/pg?url=https://online-pay.kakao.com/pay/mockup/12618e7f0f21086a0173f2c2d68032deb64f7cfd7103f86aa476531c1344d562"

}
```

postman screenshot

![스크린샷 2024-02-28 오후 9.16.17.png](/img/user/docs/assets/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202024-02-28%20%EC%98%A4%ED%9B%84%209.16.17.png)

`next_redirect_pc_url` 로 들어가서 QR을 찍었을때 카카오톡으로 전환됐을 경우 스크린샷:

![IMG_3514.png|300](/img/user/docs/assets/IMG_3514.png)

결제가 완료된 후 등록한 리다이렉트 url로 이동한 스크린샷:

![스크린샷 2024-02-28 오후 9.26.37.png](/img/user/docs/assets/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202024-02-28%20%EC%98%A4%ED%9B%84%209.26.37.png)
