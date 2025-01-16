---
{"dg-publish":true,"permalink":"/docs/Store informations related to User, but not authorization-related {django}/","title":"Store informations related to User, but not authorization-related {django}"}
---

- [doc](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/#extending-the-existing-user-model)

> If you wish to store information related to `User`, you can use a [`OneToOneField`](https://docs.djangoproject.com/en/4.2/ref/models/fields/#django.db.models.OneToOneField "django.db.models.OneToOneField") to a model containing the fields for additional information. This one-to-one model is often called a profile model, as it might store non-auth related information about a site user. For example you might create an Employee model
