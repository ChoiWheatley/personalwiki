---
{"dg-publish":true,"permalink":"/docs/five terrible horseman of making unsafe Rust collections/","title":"five terrible horseman of making unsafe Rust collections"}
---

- [[docs/0013.1 Scrapped 🦀\|0013.1 Scrapped 🦀]]
- https://rust-unofficial.github.io/too-many-lists/sixth-variance.html
- There are five terrible horsemen of making unsafe Rust collections:

1.  [Variance](https://doc.rust-lang.org/nightly/nomicon/subtyping.html)
2.  [Drop Check](https://doc.rust-lang.org/nightly/nomicon/dropck.html)
3.  [NonNull Optimizations](https://doc.rust-lang.org/nightly/std/ptr/struct.NonNull.html)
4.  [The isize::MAX Allocation Rule](https://doc.rust-lang.org/nightly/nomicon/vec/vec-alloc.html)
5.  [Zero-Sized Types](https://doc.rust-lang.org/nightly/nomicon/vec/vec-zsts.html)

Mercifully, the last 2 aren't going to be a problem for us.
