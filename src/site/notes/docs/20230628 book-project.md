---
{"aliases":null,"tags":null,"description":null,"created":"2023-06-28T14:01:49","updated":"2023-07-15T21:30:21","title":"20230628 book-project","dg-publish":true,"permalink":"/docs/20230628 book-project/","dgPassFrontmatter":true}
---

[[docs/EC2 Postgresql을 장고 기본 데이터베이스로 활용하기\|EC2 Postgresql을 장고 기본 데이터베이스로 활용하기]] 마저 진행하기

# TODO


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs/20230627-book-project/#u6tdmc" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



- [ ] 프로필 페이지 비번 없이 삭제되고 수정하기 누르면 그냥 수정됨.  

</div></div>


## updatepassword

[[docs/index/0014.1.1 drf {django rest framework} 😴\|0014.1.1 drf {django rest framework} 😴]] 를 공부하면서 구현하는 비밀번호 변경 로직

Serializer를 사용해서 수정하는 건 된다. 문제는 signout으로 리다이렉트가 안된다. js 단에서 `window.location.href`를 하는 것 가지고선 요청이 날아가지 않는다는 것을 알았다. 그러면 이번에도 fetch를 해야하나? 애초에 redirection 자체가 아닌걸.

@김영민 message랑 redirect url을 왜 다 백엔드에서 보내냐?진짜 필요할 때에만 보내야지, 사실은 status code만 오가도 동작하게 만들어야 한다.

https://realpython.com/django-rest-framework-quick-start/ 다음 튜토리얼을 봐봐. view 함수들이 죄다 간결하게 `serializer.data` 또는 `serializer.errors` 또는 `status`만을 실어서 보내고 있잖아.

[[docs/fetch api error handling {js}\|fetch api error handling {js}]]

아, validator들을 어떻게 실패시켜야 할지 전혀 감이 오지 않아..
