---
{"dg-publish":true,"permalink":"/docs/이차원 리스트 전치행렬로 만들기 {python}/","title":"이차원 리스트 전치행렬로 만들기 {python}"}
---

- [[docs/index/0014 Python 🐍\|0014 Python 🐍]]
___
[[docs/count-servers-that-communicate\|count-servers-that-communicate]] 문제를 풀다가 다른 이의 풀이법을 보고 무릎을 탁 쳤다.

```python
grid = [[1, 1, 0, 0], 
		[0, 0, 1, 0], 
		[0, 0, 1, 0], 
		[0, 0, 0, 1]]

print([list(e) for e in zip(*grid)])
"""
[[1, 0, 0, 0], 
 [1, 0, 0, 0], 
 [0, 1, 1, 0], 
 [0, 0, 0, 1]]
"""
```
