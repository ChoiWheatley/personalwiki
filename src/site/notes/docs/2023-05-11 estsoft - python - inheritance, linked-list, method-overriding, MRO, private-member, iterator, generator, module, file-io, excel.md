---
{"dg-publish":true,"permalink":"/docs/2023-05-11 estsoft - python - inheritance, linked-list, method-overriding, MRO, private-member, iterator, generator, module, file-io, excel/","title":"2023-05-11 estsoft - python - inheritance, linked-list, method-overriding, MRO, private-member, iterator, generator, module, file-io, excel"}
---

어디까지 했더라

# Class 이어하기

## Inheritance re

아쉽게도, 상속을 하는 *이유*에 대하여 설명이 조금 부족했던 것 같기도 하다. 파이썬에서의 상속도 Java, C++등 다른 OOP 언어들의 패러다임을 그대로 가지고 있겠지? 잠만... 파이썬에는 인터페이스가 없나?


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/docs//" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





- [?] 파이썬에는 인터페이스가 없나? 그냥 모든 것을 덕타이핑으로 처리하나??? 
	- [그렇다](https://stackoverflow.com/a/372121). 정말 대단한 언어군. 인터페이스랍시고 구현체가 없는 새 클래스를 만들어 docstring으로 열심히 문서화 하면 그것이 인터페이스라고 한다.......


</div></div>


상속은 전에 확인했을 때 부모 클래스의 클래스 attr를 상속받는다고 했다. 하지만 인스턴스 attr은 상속받지 않는다. 다만, 애초에 파이썬의 인스턴스 attr의 개념이 다른 언어랑은 확연하게 다른지라... 그냥 코에 걸면 코걸이 식으로 된다고 이해하자.

## Linked List

이거 공부할 때만 해도 이터레이터를 배우지 않아서 걍 `next` 체이닝 했다. 이번엔 `LinkedList` 객체와 그 이터레이터 만들 수 있을지도!

==TODO== : [[docs/Linked List in python\|Linked List in python]]

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
    
    def link_to(self, next):
        self.next = next


노드1 = Node(10)
노드2 = Node(20)
노드3 = Node(30)

노드1.link_to(노드2)
노드2.link_to(노드3)
노드3.link_to(노드1)


print(노드1.data)
print(노드1.next.data)
print(노드1.next.next.data)
print(노드1.next.next.next.data)
```

## Method Overriding

정의: 부모에게서 상속받은 attr를 같은 이름으로 재선언하여 사용하는 것.

## Multiple Inheritance and `mro` builtin function

[[docs/Multiple Inheritance and mro builtin function\|Multiple Inheritance and mro builtin function]]

## Private Attributes

[[docs/private attributes (python)\|private attributes (python)]]

# Iterator

[[docs/custom iterator with __iter__ in python\|custom iterator with __iter__ in python]]

# Decorator

[[docs/decorator - python\|decorator - python]]으로 옮겨감

# 모듈

[[docs/module and package (python)\|module and package (python)]]

# 파일 입출력

[[docs/file-io (python)\|file-io (python)]]
