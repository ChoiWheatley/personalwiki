---
{"dg-publish":true,"permalink":"/docs/Exploring Virtual Memory and Page Structures {blog}/","title":"Exploring Virtual Memory and Page Structures {blog}"}
---

- <https://blog.xenoscr.net/2021/09/06/Exploring-Virtual-Memory-and-Page-Structures.html>
- [[docs/week07-10 {swjungle} {pintos}\|week07-10 {swjungle} {pintos}]]
___

## 요약

프로세스마다 독립적인 가상메모리 공간을 제공하기 위해서 인텔은 CR3라는 레지스터를 사용한다. 이 레지스터는 PML4T base address를 가리키는 값으로, 프로세스별로 고유하다. 이 값을 기준으로 가상주소로부터 PDPT base address를 가리키는 PML4E (E for entry)를, PDT base address를 가리키는 PDPE를, PT base address를 가리키는 PDE를, 물리페이지 base address를 가리키는 PTE를, 마지막으로 물리주소를 가리키도록 만들 수 있게된다.

참고로, 모든 페이지 엔트리들이 가지고 있는 값들은 가상주소가 아니라 물리주소이다. [[docs/week07-10 {swjungle} {pintos}\|week07-10 {swjungle} {pintos}]]에서 페이지 테이블을 walk하면서 알아냈다.

> [!question] CR3 레지스터가 담고있는 값도 물리주소임?

![Figure 01: 4 Level Page Mode Overview](https://blog.xenoscr.net/resources/images/2021-09-06-Exploring-Virtual-Memory-and-Page-Structures/image-20210831220831378.png)

![img](https://blog.xenoscr.net/resources/images/2021-09-06-Exploring-Virtual-Memory-and-Page-Structures/image-20210906150913412.png)

- [?] 어째서 pml4e가 pdpt base address를 찾는데 24비트밖에 사용하지 않는거지?? 물리주소를 담고 있어야 하잖아

12~36비트만이 PDPT Base address를 찾는데 쓰인다. 24개의 base address 비트 from PML4E + 9개의 비트의 오프셋 from va

```
PML4E + PDPT_Offset * 8
```

![Pasted image 20231014154612.png](/img/user/docs/assets/Pasted%20image%2020231014154612.png)

- [?] 왜 40비트인가?
