---
{"description":null,"aliases":null,"tags":null,"created":"2023-03-01T23:00:09","updated":"2023-07-15T21:33:04","title":"immutable to mutable","dg-publish":true,"permalink":"/docs/immutable to mutable/","dgPassFrontmatter":true}
---

객체의 소유권을 건네주는 상황에서 객체의 불변 여부를 변경할 수 있다. 이는 c++과는 다른 점이다.

```rust
let v1 = vec![1, 2, 3];
let mut v2 = v1; // v2는 v1으로부터 소유권을 인계받았다.
```
