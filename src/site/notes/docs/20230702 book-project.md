---
{"dg-publish":true,"permalink":"/docs/20230702 book-project/","title":"20230702 book-project"}
---

- 어제 하던거: 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs/20230701-book-project/#w5jgh9" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



- [[docs/aws s3 static files in django\|aws s3 static files in django]] 

</div></div>

- [[docs/aws s3 static files in django\|aws s3 static files in django]] 마저 진행.
- media 파일들은 https://allbooks-choi-2.s3.amazonaws.com/media/product_images/asdf-1 이런 식으로 잘 들어오거든. 그런데 JS는 무지성으로 http://127.0.0.1:8000/static/js/getCookie.js 이렇게 로컬에 있는 정적파일을 가져온다. 무엇이 문제인가?
- EC2 docker compose로 빌드한 웹앱 중[[docs/kakaopay {django}\|kakaopay {django}]] 에서 발생한 에러

```
bookstore-django-1  | Internal Server Error: /purchases/kakaopay_start/
bookstore-django-1  | Traceback (most recent call last):
bookstore-django-1  |   File "/opt/venv/lib/python3.10/site-packages/django/core/handlers/exception.py", line 55, in inner
bookstore-django-1  |     response = get_response(request)
bookstore-django-1  |   File "/opt/venv/lib/python3.10/site-packages/django/core/handlers/base.py", line 197, in _get_response
bookstore-django-1  |     response = wrapped_callback(request, *callback_args, **callback_kwargs)
bookstore-django-1  |   File "/opt/venv/lib/python3.10/site-packages/django/contrib/auth/decorators.py", line 23, in _wrapper_view
bookstore-django-1  |     return view_func(request, *args, **kwargs)
bookstore-django-1  |   File "/app/purchases/views.py", line 190, in kakaopay_start
bookstore-django-1  |     purchase.kakaopay_checkout_tid = result['tid']
bookstore-django-1  | KeyError: 'tid'
```

- 진행한 저시기
	- https://developers.kakao.com/console 에 들어가 자기 앱 > 플랫폼 > Web  사이트 도메인에 포트를 포함한 IP 주소를 작성하면 된다.
