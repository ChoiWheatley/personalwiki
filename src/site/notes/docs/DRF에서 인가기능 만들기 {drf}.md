---
{"aliases":null,"tags":["drf/permissions drf/authorization"],"description":"사용자에게 적절한 권한 부여하기","title":"DRF에서 인가기능 만들기 {drf}","created":"2023-08-02T09:42:38","updated":"2023-08-04T00:35:18","dg-publish":true,"permalink":"/docs/DRF에서 인가기능 만들기 {drf}/","dgPassFrontmatter":true}
---

- links:
	- [[docs/index/0014.1 Django 🎈\|0014.1 Django 🎈]]
	- [[docs/index/0014.1.1 drf {django rest framework} 😴\|0014.1.1 drf {django rest framework} 😴]]  
	- [[docs/DRF에서 인증기능 만들기 {drf}\|DRF에서 인증기능 만들기 {drf}]]
		<iframe title="Django Rest Framework Series - Permissions and Custom Permissions - Part-2" src="https://www.youtube.com/embed/5AOn0BmSXyE?feature=oembed" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- 인증의 범위로 따진다면 | [permissions {doc}](https://www.django-rest-framework.org/api-guide/permissions/#setting-the-permission-policy)
	- project level permissions
	- object level permissions
	- view level permissions
- 인증의 효력으로 따진다면 | [permissions {doc}](https://www.django-rest-framework.org/api-guide/permissions/)
	- `AllowAny`
	- `IsAuthenticated`
	- `IsAdminUser`
	- `IsAuthenticatedOrReadOnly`
- 인증의 수단으로 따진다면 | [authentication {doc}](https://www.django-rest-framework.org/api-guide/authentication/#api-reference) | [[docs/DRF에서 인증기능 만들기 {drf}\|DRF에서 인증기능 만들기 {drf}]]
	- Token based authentication
	- Session based authentication
