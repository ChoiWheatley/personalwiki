---
{"dg-publish":true,"permalink":"/docs/20230603 book-project/","title":"20230603 book-project"}
---

- [[docs/index/0014.1 Django 🎈\|0014.1 Django 🎈]]
- [[docs/주니어 백엔드 개발자, 그 이상으로 🚀{book-project}\|주니어 백엔드 개발자, 그 이상으로 🚀{book-project}]]
- [[docs/git commit message 규칙\|git commit message 규칙]]
- 오늘은 세팅만 하다가 끝날듯. 뭔가 엄청나게 더딘데? 어디에서 막히는지, 세팅을 어떻게 하는지, 플랫폼 별로 어떻게 진행하면 되는지 설명할 필요가 있어보인다.
	- 가상환경
		- 파이썬 설치는 되어있다고 가정함. python version 3.11.3
		- requirements.txt <-- requirements/requirements.in
		- 가상환경 진입법 (매번)
		- vscode 인터프리터 설정
		- 패키지
			- decouple
			- ~~pip-tools~~
			- `django==4.2`
			- `python-decouple` => secret_key 를 다른 파일(`core/.env` 파일)로 옮기고 구분하기 쉽게 이름을 바꾸고 이걸 내 본 서버에 들여오는 역할을 수행함.
	- git 관련
		- git clone, gitignore, 
		- SECRET_KEY 깃허브에 올리지 않기 위해서 + decouple
	- django 관련
		- static폴더 연결 (CSS)
		- template 폴더
		- app (core, users)
		- createsuperuser
		- urls.py 안에 

core/env.py 의 목적 https://github.com/ESTsoft-Book-Project/bookstore/blob/main/core/env.py  
	열심히 숨긴 `.env` 파일의 secret_key를 꺼내올 때 사용함. `decouple`을 의존함.

TODO: [[docs/postman\|postman]] => 페이지 열 필요 없이 API만 설계할 수 있게끔

static 도 나중에 gitignore 해주어야 한다.

TODO: PR하는 방법 평일에 강의.

form.save() 의 역할이 뭐지?
