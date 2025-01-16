---
{"dg-publish":true,"permalink":"/docs/is there a way to iterate through the values of an enum/","title":"is there a way to iterate through the values of an enum"}
---

- https://stackoverflow.com/questions/21371534/in-rust-is-there-a-way-to-iterate-through-the-values-of-an-enum
- 스태틱 배열을 직접 선언하면 된다.

```rust
pub enum Direction {
    North,
    South,
    East,
    West,
}

impl Direction {
    pub fn iterator() -> Iter<'static, Direction> {
        static DIRECTIONS: [Direction; 4] = [North, South, East, West];
        DIRECTIONS.iter()
    }
}
```
