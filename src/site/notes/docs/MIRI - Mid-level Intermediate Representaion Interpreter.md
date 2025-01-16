---
{"dg-publish":true,"permalink":"/docs/MIRI - Mid-level Intermediate Representaion Interpreter/","title":"MIRI - Mid-level Intermediate Representaion Interpreter"}
---

- https://github.com/rust-lang/miri
- unsafe 코드를 작성할 때 발생할 수 있는 undefined behaviour를 사전에 잡아줄 수 있는 실험적인 미들웨어.
- 설치방법은 다음과 같다.

```bash
rustup +nightly component add miri
cargo +nightly miri test
```
