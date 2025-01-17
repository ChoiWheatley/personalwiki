---
{"dg-publish":true,"permalink":"/docs/week 01~03 {swjungle} {ALGORITHMS}/","title":"week 01~03 {swjungle} {ALGORITHMS}"}
---


## INDEX

- [[docs/swjungle 🤖\|swjungle 🤖]]
- [swjungle 정보페이지](https://jungle7-7610626261f4.herokuapp.com/pages/W01-problem-solving.html)
- [문제모음집](https://docs.google.com/spreadsheets/d/1z4a3pSM-h76kwdUAlPXXmbwcpP-VKFYFK92TCQtjXV4/edit#gid=0)
- [swjungle-week-01 {GH}](https://github.com/ChoiWheatley/swjungle-week-01)
- [P7-Week01-03 목요일 시험 문제 답안 제출용 리포지토리 {GH}](https://github.com/SWJungle/P7-Week01-03)
- [[docs/Doit 자료구조와 함께 배우는 알고리즘 기초 파이썬 편\|Doit 자료구조와 함께 배우는 알고리즘 기초 파이썬 편]]
- [[docs/index/0015.1 CSAPP Third Edition Bryant, Randal E. O'Hallaron, David. 💻\|0015.1 CSAPP Third Edition Bryant, Randal E. O'Hallaron, David. 💻]]
- [[docs/index/0015 OS {ssu2021-2nd} 💻\|0015 OS {ssu2021-2nd} 💻]]
- [[docs/Linux IPC Programming {inflearn archive}\|Linux IPC Programming {inflearn archive}]]

## CSAPP

- WEEK01: ~1.4. 프로세서는 메모리에 저장된 인스트럭션을 읽고 해석한다
- WEEK02: 1.5. 캐시가 중요하다 ~ 1.7. 운영체제는 하드웨어를 관리한다
- WEEK03: 1장 끝까지
- Extra: 3장. 프로그램의 기계수준 표현 (특히 3.2, 3.4, 3.7, 3.8)

## 컴퓨팅사고로의 전환

개발자는 컴퓨터에게 일을 잘 시켜야 한다. 그럼 일을 잘 시킨다는 건 뭐임? 

- Halting Problem: 컴퓨터가 답을 내게 만들어야 함 (멈춰야 함.) 무한루프는 생각보다 치명적인 에러임 이미 컴퓨터가 풀 수 있는 문제들을 여러분에게 주어지고 그 문제를 풀 능력을 기르는 것이 이번 주차의 목표.

백준문제 풀기: 키워드 위주로. 기초문제는 오늘 안에로 다 풀어주시고. 파이썬 언어로 풀기를 바람

==시험==

- 매주 목요일 오전 10:00 ~ 11:30
- 깃헙에 풀 리퀘스트를 생성하여 제출.
- 풀이를 리뷰할 사람을 정해 코드리뷰.

## WEEK01

- [x] [[docs/Daily Notes/2023-08-12\|블로그를 하나 만들어 에세이를 작성하시오. ~= 12일 자정까지]]

### TIPS

[[docs/index/0014 Python 🐍\|0014 Python 🐍]]으로 옮겨적을것
___
- [[docs/20230501 estsoft - python - convention, types, variables, int, float\|floating point formatting]]
- [[docs/iterator를 꺼내 문자열로 만드는 방법{sof}\|iterator를 꺼내 문자열로 만드는 방법{sof}]]
- [[docs/lower bound with bisect_left (python)\|lower bound with bisect_left (python)]]
- [[docs/20230517 estsoft - python - linked list - dataclass - typing Self cast type union - __getitem__ - slice.indices\|colon slicing]] boj 2588
- `my_single_element_tuple = 1,`
- `this_is_not_a_tuple = (1)`
- [?] `a, b = [1, 2, 3, 4]` => 오류남 참조할 곳이 없게 되어서. None과 null의 차이가 뭐냐?
	- 리턴문이 없는 함수는 None을 리턴하는데, 왜 쟤네들은 에러냐?

### 문제풀이

[[docs/index/0011 Algorithms ♾️#문제풀이 회고용\|0011 Algorithms ♾️#문제풀이 회고용]] 페이지에 추가할 것

- [swjungle-week-01 {GH}](https://github.com/ChoiWheatley/swjungle-week-01)를 참고하세요. 문제푼것들, 교재 실습한 것들 코드 위주로 올라갑니다. 

- [ ] [[docs/next_permutation 구현#일곱 난쟁이\|next_permutation 구현#일곱 난쟁이]] 직접 next_permutation 구현해 볼 것
- [x] [[docs/algorithms/10819 차이를 최대로 {boj} {permutation}\|10819 차이를 최대로 {boj} {permutation}]]
- [x] [[docs/10927 외판원 순회 2 {boj} {완전탐색}\|10927 외판원 순회 2 {boj} {완전탐색}]]
- [x] [[docs/algorithms/1629 곱셈\|1629 곱셈]]
- [x] [[docs/10830 행렬제곱 {boj}\|10830 행렬제곱 {boj}]] 행렬 대각화 사용하여 풀어볼 것
- [x] [[docs/2805 나무자르기 {boj}\|2805 나무자르기 {boj}]]
- [x] [[docs/2110 공유기 설치 {boj} {parametric search}\|2110 공유기 설치 {boj} {parametric search}]]

## WEEK02

- 스택, 큐, 우선순위큐, 그래프(vertex, edge, node, arc), BFS, DFS, 위상정렬
- 읽어야 할 단원
	- 4-1 스택
	- 4-2 큐
	- 6-8 힙 정렬
	- 9-1 트리
	- 9-2 이진트리와 이진검색트리
- CSAPP
	- 1.5 캐시가 중요하다
	- 1.6 ?
	- 1.7 운영체제는 하드웨어를 관리한다
- Day01: Stack
	- [PR: 10828, 17608](https://github.com/ChoiWheatley/swjungle-week-02/pull/2)
- Day02: Queue
	- [PR: 17608, 10828, 2504, 2493, 2812, 18258, 2164 ](https://github.com/ChoiWheatley/swjungle-week-02/pull/8)
- Day03: PriorityQueue, Graph
	- [[docs/graph 기초\|그래프]]
	- [PR1: 원 영역, 최대 힙](https://github.com/ChoiWheatley/swjungle-week-02/pull/11)
	- [PR2: 가운데를 말해요, 카드 정렬하기](https://github.com/ChoiWheatley/swjungle-week-02/pull/13)
- Day04: DFS
	- [PR](https://github.com/ChoiWheatley/swjungle-week-02/pull/15)
- [[docs/위상정렬\|위상정렬]]  

### Doit!

[[docs/Doit 자료구조와 함께 배우는 알고리즘 기초 파이썬 편#Chapter04 스택과 힙\|Doit 자료구조와 함께 배우는 알고리즘 기초 파이썬 편#Chapter04 스택과 힙]]

### TIPS

- [[docs/index/0014 Python 🐍\|0014 Python 🐍]]으로 옮겨적었습니다.
	- `Exception`을 상속하는 클래스는 `raise`가 가능해지는구나 ==p.157==
	- `try` - `except` - `else` - `finally` 
		- `try`: 원래 처리할 내용
		- `except`: 예상 에러 발생시 처리할 내용
		- `else`: 에러 미발생시 처리할 내용
		- `finally`: 심지어 중간에 리턴을 했을지라도 에러 발생여부 상관없이 무조건 실행하는 내용
	- `BaseException`과 `Exception` 간의 차이
	- `__contains__`: `in` 문법 사용 가능
	- [[docs/dataclass ValueError mutable default class list is not allowed, use default_factory {python}\|dataclass ValueError mutable default class list is not allowed, use default_factory {python}]]

### 문제풀이

- [[docs/2812 크게 만들기 {boj} {stack}\|2812 크게 만들기 {boj} {stack}]] -> int, str 형변환을 자주 하지 말자
- [[docs/18258 큐 2 {boj} {queue}\|18258 큐 2 {boj} {queue}]]
- [[docs/algorithms/11279 최대 힙 {boj} {heap} {python class Heap}\|11279 최대 힙 {boj} {heap} {python class Heap}]]
- [[docs/algorithms/1655 가운데를 말해요 {boj} {heapq}\|1655 가운데를 말해요 {boj} {heapq}]]
- [[docs/1715 카드 정렬하기 {boj}\|1715 카드 정렬하기 {boj}]] →수열을 더하는데 괄호를 어디에 배치하느냐에 따라 달라지는 결과값 중 최소를 구하는 문제인듯
- [[docs/13334 철로 {boj} {priorityqueue}\|13334 철로 {boj} {priorityqueue}]]  
- [[docs/21606(아침산책) {boj} {dfs}\|21606(아침산책) {boj} {dfs}]]  
- [[docs/algorithms/network_delay_time\|network_delay_time]]  
- [[docs/이분 그래프\|이분 그래프]]  
- [[docs/2617 구슬찾기 {boj} {플로이드워셜}\|2617 구슬찾기 {boj} {플로이드워셜}]]  
- [[docs/1948 임계경로 {boj} {위상정렬}\|1948 임계경로 {boj} {위상정렬}]]

### 다시 풀 문제

- ~~[[docs/13334 철로 {boj} {priorityqueue}\|13334 철로 {boj} {priorityqueue}]] → 길이 d의 모든 선분 L에 대하여 집과 사무실의 위치가 모두 L에 포함되는 사람들의 최대 수를 구하는 문제가 힙이야?~~  
~~- 11725(트리부모찾기): 멍청하게 10_000 ** 2 크기의 행렬을 생성하려고 했다.
- ~~1707(이분그래프): 20분동안 문제를 다르게 바라보았다. 그래도 실마리는 찾은 것 같다.~~  
	- ~~집합 안에서 정점끼리 인접하지 않아야 한다. DFS 돌면서 핑퐁하면서 집합을 다르게 준다. 두 개의 집합으로부터 중복되는 원소가 있다면 `set.교집합()` 결과가 비어있지 않으면 이건 이분그래프가 아니게 된다는 것임~~	
- [[docs/21606(아침산책) {boj} {dfs}\|21606(아침산책) {boj} {dfs}]]: 73점, 
	- Ai = 0인 케이스, Ai = 1인 i는 2개 이하인 케이스, N<= 100인 케이스는 모두 맞추었으나
	- 1 <= i < N 인 모든 정수 i에 대해 트리의 i번 정점과 i+1번 정점 사이에 간선이 존재하는 경우 (35점)과 추가 제한조건 없는(92점) 케이스는 틀렸다.
- ~~2573(빙산): 시간초과~~
	- ~~대충봐도 비효율적이긴 한데... 시간 안에 구현하려면 깊게 생각할 시간이 부족해지지 않나???~~
- ~~10000(원 영역): 시간초과~~
	- [[docs/Union Find\|Union Find]]이 여기서 왜 나와?

> 문제를 풀 때가 아니다, 머리에 든 게 없다 [[docs/graph 기초\|그래프]]를 다시 공부하자.

### Prerequisites

- [[docs/algorithms/1197 최소 스패닝 트리 {boj}\|1197 최소 스패닝 트리 {boj}]]와 [[docs/Union Find\|Union Find]]를 공부하며 서로소집합이 무엇인지 알아야 한다.
- 서로소집합을 알아야 [[docs/단절점 {TODO}\|단절점 {TODO}]]을 이해할 수 있다.

## WEEK 03

동적 프로그래밍 & 그리디 알고리즘

WEEK 04에서 C를 들어가는데, 미리미리 준비해주는 것이 좋을 것 같다. C '언어'를 배우는 게 아니다. C는 사실 제공되는 기능이 거의 없다. 기계를 이해하는 것, CPU 구조를 이해하는 데 중요하다. | [[docs/index/0015.1 CSAPP Third Edition Bryant, Randal E. O'Hallaron, David. 💻\|0015.1 CSAPP Third Edition Bryant, Randal E. O'Hallaron, David. 💻]]

- INDEX
	- [문제풀이링크 {GH}](https://github.com/Designated-Hitter/Week03----algorithm/pull/4) | 루트 README로 문제풀이현황을 체크하고 각 문제 폴더 안 README에 각종 고민들 풀고
		- ⚠️ 마크들은 블로그 글 또는 팀원 코드를 참고하여 맞춘 문제이므로 언제든 다시 돌아와 문제 풀것
- Problems
	- [[docs/2624 동전 바꿔주기{boj}\|2624 동전 바꿔주기{boj}]]
	- [[docs/9084 동전 {boj}\|9084 동전 {boj}]]
	- [[docs/2294 동전 2{boj}\|2294 동전 2{boj}]]
	- 9251 LCS {boj} → [[docs/LCS 가장 긴 공통 부분수열\|LCS 가장 긴 공통 부분수열]] 참고하세요 과거의 나에게 압도적 감사
	- 11053 가장 긴 증가하는 부분 수열 {boj} {LIS} | [[docs/LIS 가장 긴 증가하는 부분수열\|LIS 가장 긴 증가하는 부분수열]]
	- [[docs/16500 문자열 판별 {boj} {dp, hash}\|16500 문자열 판별 {boj} {dp, hash}]]
	- [[docs/2629 양팔저울 {boj} {dp, DFS}\|2629 양팔저울 {boj} {dp, DFS}]]
	- [[docs/1782 컵라면 {boj} {greedy}\|1782 컵라면 {boj} {greedy}]]
	- [[docs/11049 행렬 곱셈 순서 {boj}\|11049 행렬 곱셈 순서 {boj}]]

### 일정

- 8월 30일(수) 14:00까지 모든 DP 문제 완료
	- '상' 문제는 얻어가려고 시간 낭비하지 말고 ✅ 채우는 데에 집중하자.
- 8월 30일(수) 20:00 CSAPP 브리핑(1장 전체)
	- 질문거리와 요약내용 최대한 압축해서 정리하자.
	- **미리미리 읽어놓아야 문제없겠지?**
