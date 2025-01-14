---
{"aliases":null,"tags":null,"description":null,"title":"left rotate를 수행하는 간단한 수도코드를 작성해보세요 {red black tree}","created":"2024-01-08T15:12:46","updated":"2024-01-10T02:03:15","dg-publish":true,"permalink":"/docs/left rotate를 수행하는 간단한 수도코드를 작성해보세요 {red black tree}/","dgPassFrontmatter":true}
---

- [[docs/index/0012 Career 💼\|0012 Career 💼]]
- [[docs/이진검색트리 red black tree\|red black tree]]
---
노드 u를 기준으로 왼쪽 회전하는 경우부터 설명하겠습니다. u의 오른쪽 자식을 r, 부모를 p라고 하겠습니다.

1. u가 루트노드인 경우, 루트노드를 r로 할당합니다.
2. u의 오른쪽 자식을 r.left로 수정합니다.
3. 마찬가지로 r.left.parent를 u로 수정합니다. 이로써 r의 왼쪽 자식의 서브트리가 u의 오른쪽 자식으로 편입됐습니다.
4. 만약 u가 p의 왼쪽 자식이었다면,
	1. u.p.left = r 으로 수정합니다.
5. 오른쪽 자식이었다면,
	1. u.p.right = r로 수정합니다. 원래 u 자리였던 노드를 r이 채웠기 때문입니다.
6. r.parent = p
7. u.parent = r
8. r.left = u

[[docs/assets/rbtree.rotate_left.excalidraw\|rbtree.rotate_left.excalidraw]]

![rbtree.rotate_left.excalidraw.png](/img/user/docs/assets/rbtree.rotate_left.excalidraw.png)
