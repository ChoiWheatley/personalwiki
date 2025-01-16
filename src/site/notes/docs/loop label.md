---
{"dg-publish":true,"permalink":"/docs/loop label/","title":"loop label"}
---

기본적으로 `break` 나 `continue` 구문은 가장 안쪽의 반복문에 연관이 있지만 이것을 명시적으로 바꿀 수 있다.

```rust
'L1: loop {
	'L2: loop {
		'L3: loop{
			break 'L1;
		}
	}
}
```
