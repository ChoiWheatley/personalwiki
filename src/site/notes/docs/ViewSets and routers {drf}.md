---
{"dg-publish":true,"permalink":"/docs/ViewSets and routers {drf}/","title":"ViewSets and routers {drf}"}
---


# INDEX

- [doc](https://www.django-rest-framework.org/api-guide/viewsets/#viewsets)
- [[docs/drf 에서 redirect url에 대한 정보를 ViewSet에 담는법 {drf}\|drf 에서 redirect url에 대한 정보를 ViewSet에 담는법 {drf}]]

# urlconf를 자동으로 생성해주는 `View`들의 집합

[routers {doc}](https://www.django-rest-framework.org/api-guide/routers/#routers)

`Router` 객체를 통하여 `urlpatterns`를 자동으로 생성할 수 있다. 그러기 위해선 `ViewSet`을 구현하여야 하며, `list`, `retrieve` 메서드를 구현하여야 한다. 이름에서부터 알 수 있듯이, 두 메서드는 각각 모든 데이터 참조와 구체적인 데이터 하나 참조를 의미한다.

`core/urls.py`

```python
from django.contrib import admin
from django.urls import path
from rest_framework.routers import DefaultRouter
from users.views import MemberViewSet

router = DefaultRouter()
router.register(r"users", MemberViewSet, basename="user")

urlpatterns = [
    path("admin/", admin.site.urls),
] + router.urls
```

때로 `include`와 접두사를 붙여 이것이 API임을 확실하게 명시하기도 하는데..

```python
urlpatterns = [
    path('forgot-password/', ForgotPasswordFormView.as_view()),
    path('api/', include(router.urls, 'app_name')),
]
```

## 추가 `@action`을 url에 삽입하자

- [action decorator {doc}](https://www.django-rest-framework.org/api-guide/routers/#routing-for-extra-actions)
- [customizing dynamic routes {doc}](https://www.django-rest-framework.org/api-guide/routers/#customizing-dynamic-routes)

기본적인 `ViewSet`의 경우 CRUD 또는 기본 HTTP 메서드들에 대한 라우팅을 제공한다. 그것 말고도 추가적인 기능을 제공하는 엔드포인트를 만들고 싶을땐 `@action` 데코레이터를 붙이면 된다. URL 패턴의 이름은 메서드 자체의 이름이 되고, URL path의 이름은 `ViewSet.basename`에서 정의한 바와 URL 패턴의 이름을 `-`를 구분자로 취한 이름이 된다.

- URL pattern: `^users/{pk}/set_password/$`
	- 말 그대로 `urlpatterns`와 실제 주소에서 사용할 이름
- URL name: `user-set-password`
	- reverse할 때 사용할 이름, 참고로 rest framework에서의 리버싱은 [[docs/ViewSet.reverse_action {drf}\|ViewSet.reverse_action {drf}]]이다.

## `detail` argument in dynamic routes

[Customizing dynamic routes](https://www.django-rest-framework.org/api-guide/routers/#customizing-dynamic-routes)에 따르면, list-based, detail-based route로 구분이 되어진다고 하고, 이 사이를 구분하는 인자가 바로 `detail` 키워드 인자인 것 같다.

[Simple router](https://www.django-rest-framework.org/api-guide/routers/#simplerouter)에서는 URL 스타일에 따라 `detail=True`, `detail=False`를 결정하기도 함.

[sof](https://stackoverflow.com/a/54430929/21369350) 대화를 보니까 원래는 `@action`을 안 쓰고 `detail_route`와 `detail_route`를 사용했었고, 현재 deprecated 되었다고 한다. `detail_route`가 `detail=True`가 되었고 반대쪽도 마찬가지.

> Use detail=True when this method will account for a single instance of the Model represented by that endpoint and False when it needs to represent a Queryset of that model
