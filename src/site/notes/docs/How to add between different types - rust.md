---
{"dg-publish":true,"permalink":"/docs/How to add between different types - rust/","title":"How to add between different types - rust"}
---

- https://users.rust-lang.org/t/how-to-add-different-types/79178

```rust
impl std::ops::Add<B> for A {
    type Output = B;
    fn add(self, rhs: B) -> Self::Output { todo!() }
}
impl std::ops::Add<A> for B {
    type Output = B;
    fn add(self, rhs: A) -> Self::Output { todo!() }
}
```
