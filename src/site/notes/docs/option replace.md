---
{"dg-publish":true,"permalink":"/docs/option replace/","title":"option replace"}
---

- https://doc.rust-lang.org/std/option/enum.Option.html#method.replace
- Replaces the actual value in the option by the value given in parameter, returning the old value if present, leaving a `Some` in its place without deinitializing either one.

```rust
pub fn replace(&mut self, value: T) -> Option<T>
```
