---
{"dg-publish":true,"permalink":"/docs/axum routing Router/","title":"axum routing Router"}
---

- [`axum::routing::Router` ](https://docs.rs/axum/latest/axum/struct.Router.html)
- router type can compose handler(methods) and services.

```rust
let routes = Router::new().route(
	"/hello", // path
	axum::routhing::get(|| async { // method router
		Html("hello world")
	}),
);
```

- [[docs/axum routing method_routing get\|get]] can handle router handler as `GET` method
- 
