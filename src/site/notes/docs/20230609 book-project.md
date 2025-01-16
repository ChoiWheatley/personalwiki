---
{"dg-publish":true,"permalink":"/docs/20230609 book-project/","title":"20230609 book-project"}
---

- [[docs/django with ajax\|django with ajax]]부터 이어서 진행한다. ajax로 뭘 할 지 몰라서 아예 [이슈](https://github.com/ESTsoft-Book-Project/bookstore/issues/17)를 만들어 관리하기로 했다.
- [[docs/PATCH {HTTP}\|PATCH {HTTP}]]
	- `<domain>/users/profile` 엔드포인트를 관리하는 `profile` GET 함수는 일단 `HttpResponse`를 리턴한다. 하지만 그 안에 ajax 코드가 있는데, 걔가 "replace", "remove"를 서버에 요청한다.
