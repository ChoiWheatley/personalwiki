---
{"dg-publish":true,"permalink":"/docs/DateTimeField {auto_now_add} {auto_now} {django}/","title":"DateTimeField {auto_now_add} {auto_now} {django}"}
---

- tldr: 
	- `Model.save` 하면 자동으로 날짜가 수정 ==> `auto_now`
	- Model을 생성하면 자동으로 날짜가 등록 ==> `auto_now_add`  
[sof](https://stackoverflow.com/a/1737078/6428901)

```python
class User(models.Model):
    created = models.DateTimeField(auto_now_add=True)
    modified = models.DateTimeField(auto_now=True)
```
