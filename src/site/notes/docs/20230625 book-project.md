---
{"aliases":null,"tags":null,"description":null,"created":"2023-06-25T12:13:32","updated":"2023-07-15T21:30:21","title":"20230625 book-project","dg-publish":true,"permalink":"/docs/20230625 book-project/","dgPassFrontmatter":true}
---

- [[docs/reverse를 사용해야 하는 이유 {django}\|reverse를 사용해야 하는 이유 {django}]]
- [[docs/PUT이 필요한 부분 book-project {refactoring}\|PUT이 필요한 부분 book-project {refactoring}]]
- 이름을 좀 더 semantic하게...
	- `cart_list` => render
		- `carts/view`
	- `product_list` => jsonresponse
		- `carts/list`
- order_detail도 이름을 좀 더 semantic하게...
	- `order_detail` => render
		- `carts/checkout/view`
	- `order_product_detail` => jsonresponse
		- `carts/checkout/list`
