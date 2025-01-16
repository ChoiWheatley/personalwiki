---
{"dg-publish":true,"permalink":"/docs/unit tests in python + vscode debugging/","title":"unit tests in python + vscode debugging"}
---

- 파이썬이 [[docs/python package\|python package]] 에서 아주 골치아픈 일이 발생하리라고는 생각치도 못했다.
- 처음엔 [[docs/unittest module - python\|unittest module - python]]을 사용했는데, 자동으로 테스트 파일을 알아내지 못하여 [[docs/pytest module - python\|pytest module - python]]을 사용해 보았다.
- 아직은 모듈과 패키지 관계에 대한 이해가 부족해서 그냥 flat하게 테스트 코드와 구현 코드를 동일한 디렉토리에 처박아 두었다. `__init__.py` 파일도 몽땅 지워버림.
- 이제 터미널에서 `python3 -m unittest` 를 치면 내가 등록해 놓은 모든 text fixture들 내부에 있는 메서드들을 실행하는 것을 볼 수 있다. 하지만 나는 vscode 디버거와 연동하여 더 자세하게 뜯어보고 싶은 욕심이 생겼다.
- https://stackoverflow.com/questions/65116284/python-unittest-debugging-in-vscode 에 따라서 configure를 해주었더니 놀랍게도 fixture 메서드들 옆에 재생버튼이 생겼다. 개꿀.
