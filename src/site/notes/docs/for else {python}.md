---
{"dg-publish":true,"permalink":"/docs/for else {python}/","title":"for else {python}"}
---

break 구문을 만나면 실행되지 않는 코드조각

```python
for x in range(6):
  if x == 3: break
  print(x)
else:
  print("Finally finished!")

#If the loop breaks, the else block is not executed.
```
