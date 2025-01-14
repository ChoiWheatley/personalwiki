---
{"aliases":null,"tags":null,"description":null,"title":"메모리를 할당하는데 왜 블럭단위로 할당하는지 설명해 보시오 {malloc-lab}","created":"2024-01-08T17:38:32","updated":"2024-01-08T17:38:55","dg-publish":true,"permalink":"/docs/메모리를 할당하는데 왜 블럭단위로 할당하는지 설명해 보시오 {malloc-lab}/","dgPassFrontmatter":true}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/malloclab\|malloclab]]
---
- 임의 크기로 할당하다보면 외부 단편화가 많이 발생한다. 블록 단위로 하면 외부 단편화를 줄일 수 있다. 
- 모든 primitive 자료형을 담을 수 있는 최소한의 크기를 블럭으로 지정해 놓음으로써 일관성있게 메모리를 사용할 수 있게 하기 위해서.
