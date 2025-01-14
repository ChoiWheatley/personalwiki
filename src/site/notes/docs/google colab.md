---
{"description":null,"aliases":null,"tags":null,"created":"2023-04-30T20:45:32","updated":"2023-07-15T21:33:04","title":"google colab","dg-publish":true,"permalink":"/docs/google colab/","dgPassFrontmatter":true}
---

- https://colab.research.google.com/ 에 들어가 당장 구글드라이브 기반 주피터 노트북 프로젝트를 생성하라!
- **Welcom To Google Colab** 기본 페이지에 들어가면 기초적인 수준의 노트북 활용부터 판다스나 케라스와 같은 데이터처리 모듈, GPU/TPU 사용법까지 친절하게 설명이 되어있으니 궁금한 거 생길때마다 찾아보자
- 원조 주피터 노트북과 **단축키**들이 모두 동일한 관계로, 더 빠르고 훌륭한 사용법을 위해서라면 몇개는 외워두는 편이 좋을 것 같다.
	- `Cmd + Enter` : 셀 실행
	- `Cmd + M, D` : 셀 삭제
	- `Option + Enter`: 셀 실행하고 다음 셀 저시기 하기
	- `Cmd + M, M` : 마크다운 기반 텍스트 블록 만들기
	- [[docs/google colab - shortcuts\|google colab - shortcuts]]
- **셀에 연결** 기능을 활용하면 프라이빗 모드에서도 해당 노트북 컨텐츠를 확인하고 실행까지 할 수 있다. (다만 수정은 안된다)
- **구글 드라이브에서 Colab 사용하기** 단지 드라이브 들어가서 새 파일을 누르고 google colab을 선택하기만 하면 된다. 이는 시작에 불과했으니...
	- **구글 드라이브 폴더 연동**을 하여 자유자재로 드라이브 파일과 저시기를 할 수 있다.

```python 
from google.colab import drive
drive.mount('/content/mountdrive') # 저시기 하려는 노트북 내부 파일 시스템의 경로를 지정
```

- _
	- ~~마운트를 위해선 auth 코드가 필요하다. 따라서 노트북이 안내하는 링크를 따라 들어가 로그인 한 뒤, 뱉어내는 코드를 복붙하면 된다.~~
	- 이제는 auth 코드를 붙여넣을 필요 없이 자동으로 저시기 해주넹
- **Linux command**를 그냥 사용할 수 있다. 주피터노트북에서는 `!`를 쳐야 실행이 됐는데, 구글콜랩은 조금 더 간단하다.
- [[docs/index/0014 Python 🐍\|0014 Python 🐍]] 과 연결됩니다.
- 