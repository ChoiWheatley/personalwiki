---
{"dg-publish":true,"permalink":"/docs/abstract data type과 interface, class와의 차이/","title":"abstract data type과 interface, class와의 차이"}
---


## TL;DR

- ADT는 데이터와 연관 동작과의 관계만을 정의함. OOP적인 개념인 상속과 관련한 내용은 없음.

An **Abstract Data Type (ADT)** is a purely theoretical entity that bundles data with a set of related operations². It behaves in the same way as a built-in type does². However, it does not inherit from other classes, nor does it serve as the base for other derived classes².

On the other hand, an **interface** is a contract that specifies a set of methods that a class must implement¹. It can only have constants and method stubs¹. An interface cannot contain data fields³.

In summary, an ADT defines a data structure with a set of operations, while an interface defines a set of methods that a class must implement. Would you like more information on this topic?

Source: Conversation with Bing, 5/17/2023  
(1) java - Abstract Data Type and Interface - Stack Overflow. <https://stackoverflow.com/questions/19239471/abstract-data-type-and-interface.>  
(2) What is the difference between an interface and abstract class?. <https://stackoverflow.com/questions/1913098/what-is-the-difference-between-an-interface-and-abstract-class/.>  
(3) Abstract Class vs Interface in Java – Difference Between Them - Guru99. <https://www.guru99.com/interface-vs-abstract-class-java.html.>  
(4) Relationship between Interfaces and Abstract Data Type in Java. <https://stackoverflow.com/questions/24899427/relationship-between-interfaces-and-abstract-data-type-in-java.>
