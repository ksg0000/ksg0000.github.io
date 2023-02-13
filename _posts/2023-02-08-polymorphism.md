---
title: Polymorphism
tags: java
---

Program.java
-------------

```java

package com.newlecture.web.poly;

public class Program {

	public static void main(String[] args) {
//		다형성
//		하나의 프로그램을 여러 곳에서 쓸 때 달라져야할 부분이 있다
//		코드의 일부분을 쉽게 바꿔낄수있는 방법이 필요하다

		Lib lib = new Lib();

		Banner banner = new ICTBanner();
//		interface Banner를 구현한 모든 객체는 참조형으로 Banner를 참조할 수 있다
//		ICTBanner는 interface 구현 목적이지 객체, 부품으로써의 의미는 크지 않다
//		새로운 Class로 interface를 구현해도 ICTBanner Class자체가 완전체로 객체의 의미가 아니다
//		따라서 별도의 Class로 interface를 구현해 객체(부품)를 증가시키는 것은 좋은 방법이 아니다

//		Program에 interface결합 부분을 꺼내놓은 이유
//		사용자가 interface를 구현할 수 있게 열어 놓은 것 뿐 / 열어 놓지 않았다면 Lib가 구현했어야 할 기능

		banner.print();
//		메소드 인터페이스, 일부 기능을 분리한 인터페이스

		lib.printIntro(banner);
//		interface를 사용한 서비스와 interface Banner를 구현한 ICTBanner를 결합했다
//		ICTBanner객체를 함수의 인자로 넘겨줬다 / 어떤 것을 print()할지는 ICTBanner가 결정

//		----------------------------------------------------------------------------------------------

//		메소드 내부 클래스
//		새로운 클래스 파일 생성이 의미 없어보였다

		class AAA implements Banner {
//		interface의 약속을 구현할 수 있는 방법이 class뿐이여서 class를 꼭 새로운 파일로 만들어야한다는 문제가 있었다
//		ICTBanner class를 만들고 new로 객체로 만들어야 하는 불편함이 있었다
//		자바 1.5부터 함수(해당 실습에선 main) 안에서 클래스 정의가 가능해졌다 / interface구현목적으로만 사용하자
			@Override
			public void print() {
				System.out.println("   AAA 교육센터   ");
			}
		}

		Banner banner2 = new AAA();

		lib.printIntro(banner2);

//		----------------------------------------------------------------------------------------------

//		익명 클래스
//		클래스 생성이 의미 없어보였다

		Banner banner3 = new Banner() {
//			인터페이스 구현블록
			@Override
			public void print() {
				System.out.println("   익명 교육센터   ");
			}
		};
//		대입연산 때문에 ;을 붙여줬다

		lib.printIntro(banner3);

//		----------------------------------------------------------------------------------------------

//		객체 생성도 의미가 없어보였다
		lib.printIntro(new Banner() {
			@Override
			public void print() {
				System.out.println("   BBB 교육센터   ");
			}
		});
//		인수가 너무 비대하다 / 인수로는 람다함수를 사용해 주는게 좋다

//		람다식을 활용한 익명함수 / 자바에선 메소드 인터페이스에서만 사용
//		하나의 함수만 약속된 interface만 구현 가능하다 / 함수가 2개 이상이라면 람다가 어떤함수를 정의했는지 알 수 없다
		lib.printIntro(() -> {
//			print 함수를 구현했기 때문에 {}를 써줬다
			System.out.println("  lambda 익명 교육센터  ");
		});

	}
}

```

Lib.java
-------------

```java

package com.newlecture.web.poly;

public class Lib {

	public void printIntro(Banner banner) {
//		인자(파라미터)를 ICTBanner형식으로 한정하는 것이 아닌 Banner형식으로 받게 했다 / 재사용 가능
		System.out.println("┌───────────────────────┐");
		banner.print();
//		구현되지 않은 print()매서드를 사용했다 / 이후 ICTBanner에서 구현 / 메소드의 내에 일부 코드를 분리한 인터페이스

//		System.out.println("뉴렉처 교육 프로그램"); 대신 banner.print();으로 특정 교육센터 이름이 들어간 부분을 분리했다
		System.out.println("└───────────────────────┘");
	}
//	Lib.java는 jar파일로 재사용했다고 생각해라 / 라이브러리처럼 생각 / 해당 실습에선 재사용을 생략했다
//	public대신 static을 사용했다면 Lib객체를 생성하지 않아도 printIntro()사용 가능

}

```

Banner.java
-------------

```java

package com.newlecture.web.poly;

public interface Banner {
//	Banner는 interface형식으로 약속 수반한 자료형이다 / Class가 아니다 / 캡슐이 아니다

//	interface - 부품의 분리를 생각할 때 부품을 구현하는 클래스가 만족해야할 최소한의 기능, 규칙, 규약을 정의하는 도구 / 코드가 분리되었을 때 해결해주는 중간부분

//	--------------------------------------------------------------------------------------

//	interface를 구현하는 방법 3가지
//	1. 부품으로 분리되는 형태 / 개체 단위로 코드를 분리
//		캡슐 분리
//		여러개의 메소드를 갖고 있다 / 하나의 부품이 갖고 있어야 할 모든 목록을 다 정의한다

//	2. 일부 기능 단위의 코드를 분리
//		일부 기능(메소드) 분리

//	3. 메소드의 내에 일부 코드를 분리
//		구현코드의 일부를 분리
//		메소드 내에서만 interface를 사용하기 때문에 메소드의 매개변수를 통해 전달 

//	--------------------------------------------------------------------------------------

//	추상 클래스와 인터페이스의 차이

//	추상 클래스
//	추상 클래스는 이미 구현된 추상 클래스와 추상 클래스를 상속받은 객체 중 골라서 사용한다 / 같은 계열의 객체
//	추상 클래스 였다면 Banner의 자식으로 ICTBanner가 있다 / 추상 클래스 Banner가 아닌 약속으로써의 Banner가 필요하다

//	인터페이스
//	인터페이스는 틀만 정리된 interface로 서비스를 만들어 놓고 추후에 interface를 구현한 부품을 서비스에 끼워서 사용한다 / 구조가 다른 객체
//	추상화와 달리 집중화 목적이 아니다 / 코드 분리 목적

//	--------------------------------------------------------------------------------------

	void print();
//	interface는 구현하는 것이 아닌 약속만 정의하는 것이다 / Banner 기능에 대한 목록 / 약속에 대한 명세를 쓰는 것이다
//	public(데이터 서비스) private(숨기기)는 데이터를 갖고 있거나 기능을 구현하고있는 캡슐에서만 의미가 있다
//	interface Banner에 들어온 Class가 print()를 구현하고 있어야 한다는 약속이다

//	int x;
//	구현이라는 자체를 하지 않기 때문에 안 된다 / 말이 안 된다
}

```

ICTBanner.java
-------------

```java

package com.newlecture.web.poly;

public class ICTBanner implements Banner {
//	implements Banner - Banner라는 interface가 부탁한 기능을 구현했다는 의미
//	class상속 / 부모 클래스를 물려받는다
//	interface상속(구현) / 물려받는게 없다 / 하나의 클래스에서 여러개의 인터페이스를 구현할 수 있다
//	interface 약속 구현이 중요한 것이지 꼭 class로 구현하지 않아도 된다

//	틀만 정리된 Banner interface를 사용한 서비스(Lib의 printIntro())를 받고 싶어서 Banner를 구현했다 / 필요에 따른 결합

	@Override
	public void print() {
		System.out.println("   ICT 교육센터   ");
	}

}

```