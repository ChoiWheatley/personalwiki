---
{"dg-publish":true,"permalink":"/docs/How can I see the raw SQL queries Django is running/","title":"How can I see the raw SQL queries Django is running"}
---

- ref: <https://docs.djangoproject.com/en/5.1/faq/models/#faq-see-raw-sql-queries>
---

## TL;DR

```python
>>> from django.db import connection
>>> connection.queries
[{'sql': 'SELECT polls_polls.id, polls_polls.question, polls_polls.pub_date FROM polls_polls',
'time': '0.002'}]

>>> from django.db import reset_queries
>>> reset_queries() # empty connection.queries
```

django shell에서 인터랙티브하게 쿼리를 확인하면서 [[docs/N+1 problem with select_related, prefetch_related {django query}\|N+1 problem with select_related, prefetch_related {django query}]] 문제도 찾을 수 있을 것이다.
