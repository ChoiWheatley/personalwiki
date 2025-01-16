---
{"dg-publish":true,"permalink":"/docs/django generate new secret key/","title":"django generate new secret key"}
---

- <https://stackoverflow.com/a/57678930/21369350>

1.  `django-admin shell` 명령을 통해 인터랙티브 파이썬 셸을 연다.
2. 다음 코드를 친다.

```python
from django.core.management.utils import get_random_secret_key  
get_random_secret_key()
```
