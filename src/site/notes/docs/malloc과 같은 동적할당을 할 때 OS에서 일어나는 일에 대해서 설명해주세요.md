---
{"dg-publish":true,"permalink":"/docs/malloc과 같은 동적할당을 할 때 OS에서 일어나는 일에 대해서 설명해주세요/","title":"malloc과 같은 동적할당을 할 때 OS에서 일어나는 일에 대해서 설명해주세요"}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/malloclab\|malloclab]]
---
malloc을 기준으로 본다면 두 가지 중에 하나의 작업을 수행하게 됩니다. brk 아래 공간에 할당할 수 있다면 필요한 개수만큼의 블럭을 할당상태로 만들고 그 첫 주소를 리턴합니다. 아니라면 `sbrk` 시스템 콜을 호출해 힙 영역 자체의 크기를 늘린 뒤에 할당해줍니다. 

32bit 기준 8바이트 크기의 가용 블럭을 찾는다면 반환하고
