---
{"dg-publish":true,"permalink":"/docs/supplemental page table 만들기 {pintos} {swjungle}/","title":"supplemental page table 만들기 {pintos} {swjungle}"}
---

- [[docs/week07-10 {swjungle} {pintos}\|week07-10 {swjungle} {pintos}]]
___

## 정의

→ 각각의 페이지에 대해서 데이터가 존재하는 곳(frame, disk, swap 중 어디에 존재하는지), 이에 상응하는 커널 가상주소를 가리키는 포인터 정보, active인지 inactive 인지 등

page fault 발생시 swapped out 여부 판단 및 swap in 장소를 고르는 데 사용되고 반대로 swap out할 페이지를 고르는데에도 사용된다.
