---
{"dg-publish":true,"permalink":"/docs/flat map in python/","title":"flat map in python"}
---

- <https://dev.to/turbaszek/flat-map-in-python-3g98>

# TL;DR

double list comprehension with 10_000 * 10 class objects => 4.5945 ms

```python
flat_map = lambda f, xs: [y for ys in xs for y in f(ys)]

ls = [[1, 2, 3], [4, 5, 6]]
flat_map(lambda ys: ys, ls)

ls = ['a,b,c', 'd,e,f', 'g,h,i', 'j,k,l']
flat_map(lambda ys: ys.split(','), ls)
```

`for` and `extend` with 10_000 * 10 class objects => 2.7347ms

```python
def flat_map(f, xs):
	ys = []
	for x in xs:
		ys.extend(f(x))
	return ys
```

## 2023-08-15 추가: 2차원 리스트를 1차원 리스트로

```python
[x for sublist in wholelist for x in sublist],
```
