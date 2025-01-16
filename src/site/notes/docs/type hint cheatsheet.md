---
{"dg-publish":true,"permalink":"/docs/type hint cheatsheet/","title":"type hint cheatsheet"}
---

<iframe src="https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

[[docs/generator function - python\|generator function - python]]

```python
# A generator function that yields ints is secretly just a function that
# returns an iterator of ints, so that's how we annotate it
def gen(n: int) -> Iterator[int]:
    i = 0
    while i < n:
        yield i
        i += 1
```
