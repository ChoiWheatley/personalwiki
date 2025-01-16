---
{"dg-publish":true,"permalink":"/docs/POST와 DELETE의 차이/","title":"POST와 DELETE의 차이"}
---

- 멱등성의 차이.
	- POST가 멱등성이 없다. => 서버의 상태를 계속 변경하다.
	- DELETE는 멱등성이 있다. => 여러번 수행해도 한 번만 수행한 것과 같다.
