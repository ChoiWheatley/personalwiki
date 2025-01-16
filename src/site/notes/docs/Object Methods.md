---
{"dg-publish":true,"permalink":"/docs/Object Methods/","title":"Object Methods"}
---


- `Object.assign(init, target)`: init 객체에 target 객체를 덮어씌운 새 객체를 리턴
	- `const user2 = user` 이런 식으로 쓰면 안된다. 같은 주소값을 가리키기 때문.
- `Object.keys(obj)`: 키값만 배열로 반환
- `Object.values(obj)`: 밸류값들만 배열로 반환
- `Object.entries(obj)`: 키, 밸류를 가진 이차원 배열을 반환
- `Object.fromEntries(arr)`: 키, 밸류를 가진 이차원 배열로부터 객체 생성
