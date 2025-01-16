---
{"dg-publish":true,"permalink":"/docs/원소를 삭제하는 과정을 설명해보세요 {red black tree}/","title":"원소를 삭제하는 과정을 설명해보세요 {red black tree}"}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/이진검색트리 red black tree#Delete\|이진검색트리 red black tree#Delete]]
---
제거할 노드의 색상이 Red라면 그냥 지워도 됩니다. Black인 경우 문제가 되는데, 제거할 노드의 서브트리의 블랙 개수가 1 줄었기 때문입니다. 모든 경로의 Black 노드의 개수가 같아야 하기 때문에 형제 서브트리에서 잉여 블랙을 하나 훔쳐오는 방식으로 RBTree 제약조건을 다시 만족시키게 됩니다.
