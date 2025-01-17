---
{"dg-publish":true,"permalink":"/docs/week09 - Virtual Memory {pintos} {swjungle}/","title":"week09 - Virtual Memory {pintos} {swjungle}"}
---


### INDEX

- [[docs/각종 QNA 정리 {swjungle}{pintos}{project3}\|각종 QNA 정리 {swjungle}{pintos}{project3}]]
- [[docs/pintos3 {pdf} {pintos}\|pintos3 {pdf} {pintos}]] ⟶ Top-Down Approach
- pintos-kaist gitbook
	- [Introduction](https://casys-kaist.github.io/pintos-kaist/project3/introduction.html)
	- [FAQ](https://casys-kaist.github.io/pintos-kaist/project3/FAQ.html)
	- [한글번역 {Notion}](https://www.notion.so/PROJECT-3-VIRTUAL-MEMORY-d16fc8d04f4d4829b7e25691a235901c)
- CSAPP: [[docs/9. Virtual Memory {CSAPP}\|9. Virtual Memory {CSAPP}]]
- Yujip Won slides
	- [[2022_Pintos_Part3_VirtualMemory_01_DemandPaging 1.pdf]]
	- [[2022_Pintos_Part3_VirtualMemory_02_Swapping_etc.pdf]]
- [github repository link](https://github.com/ChoiWheatley/swjungle-week07-09)

### 2023-10-10 발제

- 지난주에는...
	- stack argument passing을 했었지 function call을 흉내낸 것이다.
	- intel의 ring 구조, privileged inst를 사용하기 위해 시스템 콜을 만들었다
- 이번주에는...
	- virtual memory의 4-level tree구조 특별히 radix tree라고..!
	- SPT (Supplemental page table) : 페이지 테이블 말고 뭔가를 더 만들어야 한다. 가상메모리의 존재 이유를 다시 생각해보자.
		- isolation
		- **space sharing** ⟶ swap에 도움이 되는 정보
		- stack growth: 스택 전용 페이지를 따로 줘. 페이지가 터지면 다른 페이지 할당해서 붙여서 유지. 이젠 페이지가 스택용인지, text용인지 힙용인지
	- `mmap`, `munmap` 구현
	- 스와핑 구현

PintOS 취지 ⟶ debugging 하는 법을 배워가야 아이디어 구현에 도움이 될것.

### 2023-10-11

- Introduction 파트 읽고
	- [[docs/supplemental page table 만들기 {pintos} {swjungle}\|supplemental page table 만들기 {pintos} {swjungle}]]
	- union 공부
	- page operations 생성 (struct page는 이미 있음.)
- before impl...
	- clone repo
	- [p] code review from Project 1 & 2
	- [p] live coding show

#### [[docs/pintos3 {pdf} {pintos}\|pintos3 {pdf} {pintos}]]

### 2023-10-12

- [[docs/Memory Management {pintos} {gitbook}\|Memory Management {pintos} {gitbook}]]
- [[docs/각종 QNA 정리 {swjungle}{pintos}{project3}\|각종 QNA 정리 {swjungle}{pintos}{project3}]]

#### [[docs/정글 대 토론회 {swjungle} {pintos}\|정글 대 토론회 {swjungle} {pintos}]]

### 2023-10-13

- [[docs/lazy load segment {pintos}\|lazy load segment {pintos}]]
- [[docs/try handle fault + page claiming {pintos}\|try handle fault + page claiming {pintos}]]
- [[docs/virtual address, physical address, user pool, kernel pool {pintos}\|virtual address, physical address, user pool, kernel pool {pintos}]]

### 2023-10-14

[[docs/pintos3 {pdf} {pintos}\|pintos3 {pdf} {pintos}]]  
[[docs/Exploring Virtual Memory and Page Structures {blog}\|Exploring Virtual Memory and Page Structures {blog}]]

### 2023-10-15

- [[docs/2023-10-15 pintos briefing {lazy_load_segment} {stack growth} {swjungle}\|2023-10-15 pintos briefing {lazy_load_segment} {stack growth} {swjungle}]]
- pml4 get page와 set page의 차이점은 안에서 create 옵션을 끄고 켠 채로 pmlt walk를 수행하는 것밖에 없다.
- [[docs/upage vs kpage vs physical memory {pintos} {swjungle} {qna archieve}\|upage vs kpage vs physical memory {pintos} {swjungle} {qna archieve}]]
- [[docs/Memory Management {pintos} {gitbook}\|Memory Management {pintos} {gitbook}]]
- [[docs/Anonymous Page {pintos} {gitbook}\|Anonymous Page {pintos} {gitbook}]]
- [[docs/Stack Growth {pintos} {gitbook}\|Stack Growth {pintos} {gitbook}]]

### 2023-10-16

- [[docs/args-many debugging {pintos} {swjungle}\|args-many debugging {pintos} {swjungle}]]

### 2023-10-17

- [[docs/mmap {pintos}{swjungle}\|mmap {pintos}{swjungle}]]

### 2023-10-20

- [[docs/page-merge-par debugging {pintos}{swjungle}\|page-merge-par debugging {pintos}{swjungle}]]

### 2023-10-22

- [[docs/Copy On Write {pintos}{swjungle}\|Copy On Write {pintos}{swjungle}]]

### 2023-10-23

- [[docs/week 09 WIL 및 발표준비 {swjungle}\|week 09 WIL 및 발표준비 {swjungle}]]