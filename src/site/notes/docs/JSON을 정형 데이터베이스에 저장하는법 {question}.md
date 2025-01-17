---
{"dg-publish":true,"permalink":"/docs/JSON을 정형 데이터베이스에 저장하는법 {question}/","title":"JSON을 정형 데이터베이스에 저장하는법 {question}"}
---


# Q.

안녕하세요! 오르미1기 최승현이라고 합니다! 데이터베이스 설계시 JSON을 처리하는 방법이 궁금하여 메시지 보내게 되었습니다. openai의 응답이 반정형 데이터인 JSON으로 구성되어있기 때문에 정형 데이터로 변환하기 위한 과정이 필요한 상황에 놓이게 되었습니다. 향후 openai의 스키마 변경에 유연하게 대응하기 위해 데이터베이스 컬럼을 key, value만 가지고 있게 만들어 보았습니다만, 이대로는 계층구조를 표현할수가 없더라고요. 멘토님의 조언 부탁드립니다! ERD 함께 첨부해드립니다.

`Prompt`: 명상서비스에 필요한 프롬프트 (현재 상태, 목표, 기타) 그리고 유저의 응답을 저장하는 테이블입니다.

`ChatBotConfig`: ai 모델, temperature, max tokens 등을 선택할 용도로 사용할 계획입니다.

`ChatBotReply`: openai 응답을 저장할 테이블입니다.

![Pasted image 20230727111104.png](/img/user/docs/assets/Pasted%20image%2020230727111104.png)

openai 문서의 예시 Response 스니펫을 보여드릴게요

```json
{
  "id": "chatcmpl-123",
  "object": "chat.completion",
  "created": 1677652288,
  "choices": [{
    "index": 0,
    "message": {
      "role": "assistant",
      "content": "\n\nHello there, how may I assist you today?",
    },
    "finish_reason": "stop"
  }],
  "usage": {
    "prompt_tokens": 9,
    "completion_tokens": 12,
    "total_tokens": 21
  }
}
```

보시다시피 message, usage는 한 단계가 더 들어가기 때문에 정형 데이터베이스로는 테이블을 하나 더 만들어야 하는 상황에 놓이게 되더라구요. 현재 프로젝트에서는 이걸 굳이 다 저장할 필요는 없겠지만 그래도 언젠간 다계층 JSON 객체를 저장할 날이 올 것만 같은 기분이 들더군요;;  꼭 그래야 한다면 MongoDB를 사용해야만 할까요?

# A.

굳이 `key`, `value` 쌍을 사용할 필요가 있을까 싶다. 이미 구체적으로 스키마가 정해져 있기도 하고, `model`, `temperature` 와 같은 내용만 담으면 되는데 이렇게 자유롭게 만들 필요는 없다. 충분히 독립적이고, 이미 충분히 확장성이 있다.

> [!note] 테이블을 추가/삭제 하더라도 다른 엔티티에 영향이 가지 않으면 확장성이 높다고 말할 수 있죠.

JSON의 계층구조는 테이블을 하나 더 두는 식으로 해결이 가능하다. 위의 예제에 `choices`의 경우도 그러하다. `ChatBotReply`와 `ChatBotMessage` 간의 일대다 관계를 구성하면 그만.

또 다른 방법으로는 모든 걸 DB에 저장하고 모든걸 DB에서만 꺼내려고 노력하지 않아도 된다는 것이다. 예를 들어 6개 7개 정도 되는 테이블을 한 번에 JOIN하는 건 그 자체로 귀찮기도 하고 심지어 성능도 떨어진다. 필요에 따라 프론트에서도 데이터를 조합할 줄 알아야 한다.

정 JSON을 통째로 저장해야만 한다면 MongoDB를 사용해도 된다. 이번 프로젝트 요구사항에 구체적으로 어떤 DB를 쓰라는 말이 없으니까 가능하다. 

아, 그리고 테이블을 추가할 때 `migrate`를 하느라 서버가 정지하는 것이 치명적일 정도의 서비스를 운영한다면, 서버를 두 대 이상 돌려 순차적으로 마이그레이션을 진행할 수 있을 것이다. 서버가 꺼진 동안에는 게이트웨이나 로드밸런서가 다른 서버에게 요청을 전달하면 되기 때문!
