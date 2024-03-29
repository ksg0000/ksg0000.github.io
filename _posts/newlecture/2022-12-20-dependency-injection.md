---
title: Dependency Injection
tags: java
---

**DI(Dependency Injection) 의존성 주입**, 부품 결합으로 이해하자

A제품에 B부품(Dependency)이 있을 경우 A와 B를 조립(Injection)하는 것을 DI라 한다.   
조립(Injection)의 방법은 Setter Injection(조립형)과 Construction Injection(조립형)이 있다.

A가 B를 의존할 때 의존대상 B가 변하면, 그것이 A에 영향을 미친다.   
B의 기능이 추가 또는 변경되거나 형식이 바뀌면 그 영향이 A에 미친다.

**Setter Injection**

```java
B b = new B();
A a = new A();

a.set(b);
```

**Construction Injection**

```java
B b = new B();
A a = new A(b);
```
