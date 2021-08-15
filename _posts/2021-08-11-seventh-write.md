---
layout: post
title: "자바의 정석"
date: 2021-08-11 10:36:00
image: '/assets/img/'
description: 'java'
tags:
- java
- study
---

# **자바의 정석 Chapter6**

- 인스턴스의 멤버변수값을 따로 정의해주지 않으면 해당 변수의 타입의 기본값?으로 노출된다.

ex) int channel 의 경우 → 0

![chapter_6](assets/img/chapter6_1.png)
![chapter_6](assets/img/chapter6_2.png)

- t1은 참조변수이므로, 인스턴스의 주소를 저장하고 있다. `t2 = t1` 을 수행하게 되면，t2가 가지고 있던 값은 잃어버리게 되고 저장되어 있던 값이 t2에 저장되게 된다. 그렇게 되면 t2 역시 참조
하고 있던 인스턴스를 같이 참조하게 되고, t2가 원래 참조하고 있던 인스턴스는 더 이상 사용할 수
없게 된다. 이때 t2가 원래 참조하고 있던 인스턴스는 참조변수가 없어 더 이상 사용되어질 수 없으므로 ‘가비지 컬렉터(Garbage Collector)’에 의해서 자동적으로 메모리에서 제거된다

![chapter_6](assets/img/chapter6_3.png)

- 배열 선언 방법

![chapter_6](assets/img/chapter6_4.png)

- 객체를 생성하지 않고도 메서드를 호출할 수 있으려면，메서드 앞에 ‘static’을 붙여야 한다.

![chapter_6](assets/img/chapter6_5.png)

- 인스턴스멤버(인스턴스변수와 인스턴스메서드)는 반드시 객체를 생성한 후에만 참조 또는 호출이 가능하기 때문에 클래스멤버가 인스턴스멤버를 참조, 호출하기 위해서는 객체를 생성하여야 한다. 하지만, 인스턴스 멤버간의 호출에는 아무런 문제가 없다.

![chapter_6](assets/img/chapter6_6.png)

- 오버로딩
(1) 메서드 이름이 같아야한다.
(2) 매개변수의 개수 또는 타입이 달라야한다.

- 생성자
(1) 이름은 클래스의 이름과 같아야한다.
(2) 생성자는 리턴 값이 없다.
* 생성자가 인스턴스를 생성하는 게 아니다.

- 인스턴스 변수 x는 초기화 해주지 않아도 자동적으로 int형의 기본값인 0으로 초기화되나, method1()의 지역변수 i는 자동적으로 초기돠회지 않아 컴파일 에러 발생

```java
class InitTest {
	int x; //인스턴스 변수
	int y = x; //인스턴스 변수

	void method1() {
		int i; //지역변수
		int j = i; //에러
	}
```

- 인스턴스 변수의 초기화는 주로 생성자를 사용하고, 인스턴스 초기화 블럭은 모든 생성자에서 공통으로 수행해야 하는 코드를 넣는데 사용한다.

![chapter_6](assets/img/chapter6_7.png)
