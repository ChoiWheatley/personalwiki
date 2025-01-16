---
{"dg-publish":true,"permalink":"/docs/condition variable이란 {feat.monitor}/","title":"condition variable이란 {feat.monitor}"}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/week07 - Threads {pintos} {swjungle}\|week07 - Threads {pintos} {swjungle}]]
- [pintos-kaist/appendix/synchronization/monitors](https://casys-kaist.github.io/pintos-kaist/appendix/synchronization.html#monitors)
- [[docs/monitors {synchronization}\|monitors {synchronization}]]
- [[docs/synchronization {pintos} {semaphore} {lock} {monitor}\|synchronization {pintos} {semaphore} {lock} {monitor}]]
---

## Answer

유명한 동기화 도구 중 하나인 Monitor를 구현하기 위해 있는 일종의 waiting list입니다. 모니터 설명을 안할 수가 없는데, 순차적으로 모니터에 들어가기 위한 lock과 그 안에 여러 조건들이 만족될 때 까지 기다리는 condition variable 들로 이루어져 있습니다. 

스레드는 각각의 컨디션에 맞는 조건에 cond_wait를 하게 되며, 일정 조건이 만족되었을 경우 signal을 보내 하나의 스레드를 꺼내거나, broadcast를 보내 모든 스레드를 깨울수도 있습니다.
