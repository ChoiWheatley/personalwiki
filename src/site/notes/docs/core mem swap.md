---
{"dg-publish":true,"permalink":"/docs/core mem swap/","title":"core mem swap"}
---

- https://doc.rust-lang.org/nightly/core/mem/fn.swap.html
- Swaps the values at two mutable locations, without deinitializing either one.
- if you want to swap with a default or dummy value, see [[docs/core mem take\|core mem take]].
- if you want to swap with a passed value, returning the old value, see [[docs/core mem replace\|core mem replace]].
- 두 가변 변수의 위치를 사악 바꿔준다. 내부적으로 unsafe블록을 사용하지만 다른 아티팩트가 없기 때문에 안전하다.
