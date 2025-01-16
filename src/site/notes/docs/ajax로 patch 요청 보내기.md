---
{"dg-publish":true,"permalink":"/docs/ajax로 patch 요청 보내기/","title":"ajax로 patch 요청 보내기"}
---

[sof](https://stackoverflow.com/q/27914559)

```javascript
$('div#question_preview <some button selector>').click(function (event) {
    $.ajax({
        url: 'questions/' + question_id,
        type: 'PATCH',
        data: {status: 'some status'}
    });
});
```
