---
{"dg-publish":true,"permalink":"/docs/multi level feedback queue가 무엇인가요/","title":"multi level feedback queue가 무엇인가요"}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/week07 - Threads {pintos} {swjungle}\|week07 - Threads {pintos} {swjungle}]]
- [[docs/Multi Level Feedback Queue {swjungle}{pintos}\|Multi Level Feedback Queue {swjungle}{pintos}]]
---

## Answer

스레드에 명시적으로 우선순위를 부여하는 대신, cpu burst time에 따라 우선순위를 동적으로 조절하는 방법을 의미합니다. aging으로 인해 하나의 스레드가 너무 오랫동안 CPU를 점유하면 우선순위를 떨어뜨려 반응성을 향상시킬 수 있습니다.
