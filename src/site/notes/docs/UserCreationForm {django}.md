---
{"dg-publish":true,"permalink":"/docs/UserCreationForm {django}/","title":"UserCreationForm {django}"}
---

- [[docs/django forms\|django forms]]
- [Using the Django authentication system {doc}](https://docs.djangoproject.com/en/4.2/topics/auth/default/)
	- [models.User {doc}](https://docs.djangoproject.com/en/4.2/ref/contrib/auth/#django.contrib.auth.models.User)
	- 장고의 인증(authentication) 시스템은 인가(authorization)시스템과 결합되어있다. `User` 객체는 확장이 용이한 기본적인 형태의 인증 시스템으로, 회원가입, 로그인 절차와 밀접한 연관을 갖고 있다.
	- username, password, email, first_name, last_name 외에도 많은 attribute들이 있지만 걔네들은 다 옵셔널임.
- [forms.UserCreationForm {doc}](https://docs.djangoproject.com/en/4.1/topics/auth/default/#django.contrib.auth.forms.UserCreationForm) | [[docs/django forms\|django forms]]
	- 세개의 필드를 가지고 있다. username, password1, password2
	- 추가하고 싶은 필드가 있으면... 뭐 그냥 상속하면 된다. 그래서 아래 코드의 `UserRegisterForm`의 필드로 `email`이 들어있는거다.
		- 심지어 email 필드에 대한 기본정의조차 장고에서 제공해준다... | `forms.EmailField`

[[docs/index/0014.1 Django 🎈\|0014.1 Django 🎈]]에서 회원가입 폼을 만들 때 사용한 클래스를 한 번 보자. 이메일은 기본으로 제공이 안되어 내가 추가한 걸 볼 수 있는데, `Meta` 얘는 도대체 뭐냐?

```python
from django import forms
from django.contrib.auth.models import User
from django.contrib.auth.forms import UserCreationForm


class UserRegisterForm(UserCreationForm):
    """pre-built user registration forms.... SICK!"""
    email = forms.EmailField()

    class Meta:
        """details"""
        model = User
        fields = ['username', 'email', 'password1', 'password2']
```


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs/django-internal-class-meta/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




- [doc](https://docs.djangoproject.com/en/4.1/ref/models/options/)

모델의 메타데이터를 정의한다. 메타데이터란, 필드가 아닌 모든 모델을 정의하는 데이터들을 의미한다.

> Model metadata is “anything that’s not a field”, such as ordering options ([`ordering`](https://docs.djangoproject.com/en/4.1/ref/models/options/#django.db.models.Options.ordering "django.db.models.Options.ordering")), database table name ([`db_table`](https://docs.djangoproject.com/en/4.1/ref/models/options/#django.db.models.Options.db_table "django.db.models.Options.db_table")), or human-readable singular and plural names ([`verbose_name`](https://docs.djangoproject.com/en/4.1/ref/models/options/#django.db.models.Options.verbose_name "django.db.models.Options.verbose_name") and [`verbose_name_plural`](https://docs.djangoproject.com/en/4.1/ref/models/options/#django.db.models.Options.verbose_name_plural "django.db.models.Options.verbose_name_plural")). None are required, and adding `class Meta` to a model is completely optional.

# Model Meta

https://docs.djangoproject.com/en/4.1/ref/models/options/

# Form Meta

https://docs.djangoproject.com/en/4.1/ref/forms/fields/


</div></div>

