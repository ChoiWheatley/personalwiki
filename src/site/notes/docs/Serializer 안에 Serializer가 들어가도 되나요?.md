---
{"dg-publish":true,"permalink":"/docs/Serializer 안에 Serializer가 들어가도 되나요?/","title":"Serializer 안에 Serializer가 들어가도 되나요?"}
---

- ref
	- <https://www.django-rest-framework.org/api-guide/relations/#nested-relationships>

---

## 네, 됩니다.

```python
class TrackSerializer(serializers.ModelSerializer):
    class Meta:
        model = Track
        fields = ['order', 'title', 'duration']

class AlbumSerializer(serializers.ModelSerializer):
    tracks = TrackSerializer(many=True, read_only=True)

    class Meta:
        model = Album
        fields = ['album_name', 'artist', 'tracks']
```
