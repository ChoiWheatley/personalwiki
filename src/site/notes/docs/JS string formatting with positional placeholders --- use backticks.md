---
{"dg-publish":true,"permalink":"/docs/JS string formatting with positional placeholders --- use backticks/","title":"JS string formatting with positional placeholders"}
---
 use backticks
---
- [string format with positional placeholders](https://stackoverflow.com/questions/43905269/string-format-with-positioned-placeholders-or-equivalent) \` 와 \` 사이에 `${}` 를 사용하면 된다.

```javascript
var st1 = 'name';
var st2 = 'javascript';
var sentence = `My ${st1} is ${st2}`;
console.log(sentence);
```
