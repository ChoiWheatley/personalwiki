---
{"dg-publish":true,"permalink":"/docs/AI 기반 Saas 솔루션 - 백엔드 (Python) 개발 직무 제스트/","title":"AI 기반 Saas 솔루션 - 백엔드 (Python) 개발 직무 제스트"}
---


## 서류전형 합격 🎉 커피챗 준비 ☕️

경력직 2~6년인데 그래도 서류합격이라니! 역시 절대라는 건 없다!

면접 전형 들어가기에 앞서 2024-08-23 금요일 13시에 30분여 시간동안 커피챗(화상)을 실시한다고 한다. 그래서 제스트 주식회사를 조사하면서 아래에 질문할 것들을 모아보려고 한다.

[saramin link](https://www.saramin.co.kr/zf_user/jobs/relay/view?isMypage=no&rec_idx=48790931&recommend_ids=eJxNj7sRBDEMQqu53EgyQvEW4v67OO9nbIcMDyFCwZByCPjlFaJK0qhmj8xCSyw3ipYbVotyn7K90gm3lZ0wYNPleyp7py9JJpELlvmdXbBachdZDxxPJm3mNky3x%2BXXG2U8nkQr21nQtN1Z1GEHXNWxFy054hsREXeafxGBRHk%3D&view_type=search&searchword=제스트&searchType=search&gz=1&t_ref_content=generic&t_ref=search&relayNonce=4b37f44c33b6cf4015c0&paid_fl=n&search_uuid=b33a0dbd-a93b-4e0c-bf82-cc21cc5aee14&immediately_apply_layer_open=n#seq=0)

> 제스트(ZEST)는 "건설산업의 디지털 전환을 통한 탄소중립의 실현"이라는 미션을 품고, 건설산업이 기후변화 시대에 적응해 나갈 수 있도록 공급망 관리 시스템을 제공하는 GX(Green Transformation) 기업입니다.

공급망 관리 디지털화를 통한 디지털 트랜스포메이션, 지속 가능한 건설, 건설 프로젝트 관리 플랫폼 등등 여러 추상적인 키워드들이 떠다닌다. 공급망 관리 디지털화는 아래 사이트에서 이미 운영중이다.

[제스트 자재인증 검색 사이트](https://zest.im)

> 2024년 기준으로 13만개가 넘는 건설자재들이 인증을 받았지만, 여전히 해당 자재를 검색하고 구매하는 것은 쉽지가 않습니다. 이에 본 서비스는 친환경 건설자재에 대한 정보를 쉽게 제공하는 것에 목표를 두고 개발되었습니다.

친환경 인증서를 요청하면 아래 사진과 같이 타 서비스에 API를 요청하여 PDF 파일을 가져오는 것으로 보인다. 즉석에서 만드는 것 같지는 않고 CDN 서버를 통해 파일을 가져오는듯.

![Screenshot 2024-08-23 at 01.35.28.png](/img/user/docs/assets/Screenshot%202024-08-23%20at%2001.35.28.png)![Screenshot 2024-08-23 at 01.35.55.png](/img/user/docs/assets/Screenshot%202024-08-23%20at%2001.35.55.png)

## 검색결과 분석해보자

- Count: 검색결과 N건 / M
- 대분류, 중분류, 한번 더 검색: 건설자재 분류를 통한 필터링 (FE)
- `+`: 버튼 누르면 아래에 "최승현 님의 프로젝트 | 현재 자제 N건" 으로 뜨고 내가 눌러놓은 제품들이 나타난다. 일종의 찜하기네
- 인증서: 녹색으로 표시되면 저 **환경표지 인증서** 받아볼 수 있다는 뜻임.

![Screenshot 2024-08-23 at 01.38.55.png](/img/user/docs/assets/Screenshot%202024-08-23%20at%2001.38.55.png)

## 질문들

> [!question] 이력서에 Django 경험을 구체적으로 적지 않았는데도 커피챗을 요청한 이유가 궁금해요  

> [!question] 13만 건이나 되는 자재정보는 어떻게 관리하고 추가 / 업데이트 하나요? 에코스퀘어에 open api가 있네요!

> [!question] 향후 건설산업의 디지털 트랜스포메이션을 위해서 도입하고자 하는 서비스에 또 어떤 것들이 있나요?

> [!question] 인공지능 서비스를 활용하게 된다면 건설자재 추천 시스템, 챗봇, 반정형 데이터 정제 등으로 활용할 것 같아요, 제스트는 인공지능을 어떻게 활용할 수 있을까요?

