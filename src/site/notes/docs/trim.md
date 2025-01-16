---
{"dg-publish":true,"permalink":"/docs/trim/","title":"trim"}
---

string을 파싱하기 전엔 무조건 트림을 해야 하는구나...

```rust
let mut guess = String::new(); io::stdin()
	.read_line(&mut guess) 
	.expect("Failed to read line"); 
let guess: u32 = guess.trim().parse().expect("Please type a number!");
```
