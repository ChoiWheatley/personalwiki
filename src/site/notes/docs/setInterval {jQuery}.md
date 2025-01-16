---
{"dg-publish":true,"permalink":"/docs/setInterval {jQuery}/","title":"setInterval {jQuery}"}
---

- [SOF](https://stackoverflow.com/questions/5484205/call-function-with-setinterval-in-jquery)

# Answer

To write the best code, you "should" use the latter approach, with a function reference:

```javascript
var refreshId = setInterval(function() {}, 5000);
```

or

```javascript
function test() {}
var refreshId = setInterval(test, 5000);
```

but your approach of

```javascript
function test() {}
var refreshId = setInterval("test()", 5000);
```

is basically valid, too (as long as `test()` is global).

Note that there is no such thing really as "in jQuery". You're still writing the Javascript language; you're just using some pre-made functions that are the jQuery library.
