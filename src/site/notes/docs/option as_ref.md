---
{"dg-publish":true,"permalink":"/docs/option as_ref/","title":"option as_ref"}
---

- https://doc.rust-lang.org/std/option/enum.Option.html#method.as_ref
- Converts from `&Option<T>` to `Option<&T>`

# example

Calculates the length of an `Option<String>` as an `Option<usize>` without moving the String. The map method takes the self argument by value, consuming the original, so this technique uses as_ref to first take an Option to a reference to the value inside the original.

```rust
let text: Option<String> = Some("Hello, world!".to_string());
// First, cast `Option<String>` to `Option<&String>` with `as_ref`,
// then consume *that* with `map`, leaving `text` on the stack.
let text_length: Option<usize> = text.as_ref().map(|s| s.len());
println!("still can print text: {text:?}");
```

[[docs/AsRef trait\|AsRef trait]]도 있다!
