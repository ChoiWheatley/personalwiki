---
{"aliases":"에러, 장고, Error","tags":null,"description":null,"created":"2023-06-22T10:08:33","updated":"2023-07-15T21:33:03","title":"Unexpected token DOCTYPE... is not valid JSON SyntaxError {django}","dg-publish":true,"permalink":"/docs/Unexpected token DOCTYPE... is not valid JSON SyntaxError {django}/","dgPassFrontmatter":true}
---


```
SyntaxError: Unexpected token '<', "<!DOCTYPE "... is not valid JSON
```

- 원인: JSON을 필요로 하는데 갑자기 뜬금없이 html이 날아왔다.
	- `render`함수를 생각없이 썼을수도 있다.
	- 장고의 에러페이지가 되돌아왔을 수도 있다.

결국 html파일이 날아온 것이기 때문에 개발자도구의 Network 탭에서 해당 응답의 내용을 확인할 수 있고, 미리보기도 가능하다.

![Pasted image 20230622101114.png](/img/user/docs/assets/Pasted%20image%2020230622101114.png)
