---
{"description":null,"aliases":null,"tags":null,"created":"2023-06-01T17:38:44","updated":"2023-07-15T21:33:03","title":"setting up python environment venv requirenemts.txt","dg-publish":true,"permalink":"/docs/setting up python environment venv requirenemts.txt/","dgPassFrontmatter":true}
---

- https://frankcorso.dev/setting-up-python-environment-venv-requirements.html

`venv` 사용하는 방법은 알고있지? `python -m venv .venv`

- `pip` 설치목록을 가지고 의존성을 뽑아내기
	- `pip freeze > requirements.txt`
- `requirements.txt`를 가지고 의존성 설치하기
	- `pip install -r requirements.txt`
