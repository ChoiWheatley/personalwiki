---
{"dg-publish":true,"permalink":"/docs/array/","title":"array"}
---


> You can also initialize an array to contain the same value for each element by specifying the initial value, followed by a semicolon, and then the length of the array in square brackets, as shown here:

```rust
let a = [3; 5];
```

배열의 개수와 초기값으로 초기화 할 수 있다. 두 대괄호 안에 세미콜론을 두고 왼쪽에는 초기화할 값을, 오른쪽에는 배열의 길이를 명시하면 된다.  
참고로 러스트에서 배열은 fixed length이다. 가변길이를 원한다면 벡터를 쓰도록.
