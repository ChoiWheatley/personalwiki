---
{"aliases":null,"tags":null,"description":null,"title":"암시적 리스트와 명시적 리스트에 관해 설명해주세요 {{malloc-lab}}","created":"2024-01-08T17:15:21","updated":"2024-01-08T17:37:34","dg-publish":true,"permalink":"/docs/암시적 리스트와 명시적 리스트에 관해 설명해주세요 {{malloc-lab}}/","dgPassFrontmatter":true}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/malloclab\|malloclab]]
---
암시적 리스트는 블록 헤더에 적혀있는 블록크기를 사용하여 블록을 순회합니다. 이때 할당여부 상관없이 블록들을 순회하기 때문에 헤더에 다음 free block의 위치를 저장한 방식인 명시적 리스트가 탄생했습니다.

`cmu_system_programming/19-malloc-basic.pptx`  
![explicit-list, implicit-list.png](/img/user/docs/assets/explicit-list,%20implicit-list.png)
