---
{"dg-publish":true,"permalink":"/docs/range-like feature in Javascript/","title":"range-like feature in Javascript"}
---

- https://stackoverflow.com/a/10050831

```javascript
console.log([...Array(5).keys()]);

for (const x of Array(5).keys()) {
	console.log(x);
}
```
