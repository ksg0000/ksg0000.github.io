---
title: Flutter
tags: flutter
---

**출처 : https://www.youtube.com/@codingchef**

## Widget

* Stateless Widget

    이전 상호작용의 어떠한 값도 저장하지 않음

* Stateful Widget

    Value 값을 지속적으로 추적 보존

* Inherited Widget

## Widget tree

* Widget들은 tree 구조로 정리 된다. 한 Widget에 여러 자식 Widget이 있을 수 있다.

* Parent Widget은 Widget Container라고도 한다.

<img src="/assets/images/widgetTree.png" title="참고 이미지" alt="이미지" />

MyApp

- 최상위 Widget. Custom Widget. 이름 바꿔도 된다.

MaterialApp

- 실질적으로 앱을 빌드하는 Widget. 여기서 Flutter SDK에서 제공하는 Widget들을 사용할 수 있다.

MyHomePage

- 앱의 디자인, 기능들이 만들어지는 Widget. Custom Widget. 이름 바꿔도 된다.

<span style="color:#2D3748; background-color:#fff5b1">**Scaffold**</span>

- 앱 화면과 기능을 구성하기 위한 빈 페이지를 준비해주는 Widget. 앱의 구성요소(AppBar, 이미지, 버튼, 텍스트, 센터, 컬럼, 패딩 등...)들이 위치하는 공간.

## Widget LifrCycle

Stateless Widget은 생병주가가 없다.

Stateful Widget은 10단계의 생명주기가 있다.

* <span style="color:#2D3748; background-color:#fff5b1">createState()</span>

    **Widget의 상태를 생성**

* <span style="color:#2D3748; background-color:#fff5b1">mounted == true</span>

    mounted가 true면 buildContext 클래스에 접근할 수 있다.
    buildContext가 활성화돼야 setState()를 이용할 수 있다.

* <span style="color:#2D3748; background-color:#fff5b1">initState()</span>

    **Widget을 초기화 한다.**

    처음 필요한 데이터를 주고받을 때 한 번만 사용.

* <span style="color:#2D3748; background-color:#fff5b1">didChangeDependencies()</span>

    **의존성이 변경되면 호출한다**

    상속받은 위젯을 사용할 때 피상속자가 변경되면 호출

* <span style="color:#2D3748; background-color:#fff5b1">build()</span>

    **Widget을 화면에 표시한다.**

* <span style="color:#2D3748; background-color:#fff5b1">didUpdateWidget()</span>

    **위젯을 갱신한다.**

    부모 Widget이나 데이터가 변경되어 위젯을 갱신해야 할 때 호출

* <span style="color:#2D3748; background-color:#fff5b1">setState()</span>

    **Widget의 상태를 갱신한다.**

* <span style="color:#2D3748; background-color:#fff5b1">deactivate()</span>

    **Widget의 상태 관리를 중지한다.**

    State 객체가 플러터 구성 트리로부터 제거될 때 호출

* <span style="color:#2D3748; background-color:#fff5b1">dispose()</span>

    **Widget의 상태 관리를 완전히 끝낸다.**

    State 객체를 메모리에서 없앤다.

* <span style="color:#2D3748; background-color:#fff5b1">mounted == false</span>

    **생명주기 끝**

## Class와 생성자

* 보통의 생성자

```dart
Person(String name, int age){
    this.name = name;
    this.age = age;
}
```

* named argument

    argument를 중괄호(curly brackets)로 묶어 원하는 것만 입력할 수 있다.

```dart
Person({String name, int age}){
    this.name = name;
    this.age = age;
}
```

즉, 우리가 만들던 MaterialApp, Scaffold도 클래스이고 생성자를 통해 구현하고 있던 것이다.

```dart
MaterialApp(
      title: 'gyun',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MaterialFlutterApp(),
    );
```

## Widget

* Appbar

    화면 상단 위젯

  * 속성

      leading : 아이콘 버튼이나 간단한 위젯을 **왼쪽**에 배치할 때 사용

      actions : 복수의 아이콘 버튼 등을 **오른쪽**에 배치할 때 사용

      onPressed : 함수의 형태로 버튼을 터치했을 때 일어나는 이벤트를 정의하는 곳

* Drawer

  화면 옆 튀어나오는 메뉴

  * 속성
        
    child: ListView()를 이용해 만들 것 이다.

    UserAccountDrawerHeader() : Drawer 상단 부분

    ListTile() : ListView의 children으로 여러개 존재할 수 있다.

* Button

  * FloatingActionButton

  이름이 바뀌고 Style 주는 문법이 변화했다.

  * FlatButton → TextButton

  * Outline Button → OutlinedButton

  * RaisedButton → ElevatedButton

  * 아이콘이 있는 버튼 만들기

    ```dart
    ElevatedButton.icon(
    onPressed: () {},
      icon: Icon(
        Icons.add, // 아이콘 모양
        size: 18, // 아이콘 크기
        color: Colors.black, // 아이콘 색깔
      ),
      label: Text("ICON BUTTON"),
    ),
    ```

  * 스타일 주기

    ```dart
    ElevatedButton(
      style: ElevatedButton.styleFrom(
        primary: Colors.red, // backgroundColor
        onPrimary: Colors.white, // foregroundColor
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(10),
        ),
        // 모서리 둥글게 만들기
        elevation: 0.0, // Drop Shadow 없애기
        minimumSize: Size(200, 30), // 버튼 크기
      ),
      onPressed: () {},
      child: Text('ElevatedButton'),
    ),
    ```

  * OutlinedButton 테두리 스타일

    ```dart
    OutlinedButton(
      style: OutlinedButton.styleFrom(
        side: BorderSide(
          color: Colors.red, // border 색깔
          width: 2.0, // border 두께
        )
      ),
      onPressed: () {},
      child: Text('OutlinedButton'),
    ),
    ```

  * 비활성화 버튼 만들기

    ```dart
    ElevatedButton(
      style: ElevatedButton.styleFrom(
        disabledForegroundColor: Colors.red.withOpacity(0.38),
        disabledBackgroundColor: Colors.red.withOpacity(0.12),
        // 비활성화 버튼 스타일 주기
      ),
      onPressed: null, // null
      child: Text('ElevatedButton'),
    ),
    ```

* ButtonBar

  버튼을 가로방향으로 정렬하고 공간이 부족하면 세로방향 정렬한다.

  ```dart
  ButtonBar(
    children: [
      ElevatedButton(
        onPressed: null,
        child: Text('ElevatedButton'),
      ),
      ElevatedButton(
        onPressed: null,
        child: Text('ElevatedButton2'),
      ),
    ],
  ),
  ```

    

## BuildContext

* widget tree에서 현재 widget의 위치를 알 수 있는 정보를 갖고 있다.

    * build 함수는 Scaffold Widget을 return할 때 context를 넣어준다.

* 모든 widget은 자신만의 BuildContext를 갖고 있다. 이 BuildContext는 stateless widget이나 state build 메소드에 의해 return된 widget의 부모가 된다.

즉, Scaffold Widget의 위치를 알기 위해 Scaffold Widget context를 참조하면 해당 정보가 없으며 아래와 같은 에러가 나온다.   

```
Scaffold.of() called with a context that does not contain a Scaffold
```

이를 알려면 Scaffold Widget에서 build 메소드로 widget을 return해야 한다.   
이 widget은 진짜 Scaffold Widget context를 물려받는다.

```dart
@override
Widget build(BuildContext context)
```

여기서 context는 BuildContext 클래스의 인스턴스다.

### Scaffold.of(context) method

주어진 context에서 위로 올라가며 가장 가까운 Scaffold를 찾아서 반환하라는 의미이다.

즉, Something.of(context)는 위로 올라가며 가장 가까운 Something을 찾으라는 의미!

## Snack bar

### ScaffoldMessenger

Flutter 2.0 이전에는 Scaffold.of(context).showSnackBar()를 사용해 Snackbar를 구현했다.

하지만 이는 화면전환이 일어날 때 Snackbar를 계속 보여줄 수 없었다.

Scaffold.of(context)는 현재 context를 거슬러 올라가며 Scaffold를 찾아 그 widget에 Snackbar를 띄우지만, 화면전환이 일어나 Scaffold가 바뀌면 Snackbar도 사라지기 때문이다.

이를 해결하기 위해 ScaffoldMessenger가 생겼다. 이는 MaterialApp의 Default로 포함되어 있으며 흩어져 있는 모든 Scaffold를 관리하며 언제라도 Snackbar를 수신할 수 있게 한다.

```dart
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        appBar: AppBar(
          title: Text('앱바'),
        ),
        body: Builder(
          builder: (BuildContext ctx) {
            return Center(
              child: TextButton(
                style: TextButton.styleFrom(
                  foregroundColor: Colors.white, // foregroundColor
                  backgroundColor: Colors.red, // foregroundColor
                ),
                onPressed: () {
                  ScaffoldMessenger.of(ctx).showSnackBar(SnackBar(
                    content: Text('Hello'),
                  ));
                },
                child: Text('Show SnackBar'),
              ),
            );
            // 이제 Center는 return된 widget이므로 콤마대신에 세미콜론이다.
          },
        ),
      ),
    );
  }
```

스낵바를 보여주기 위해선 ScaffoldMessenger.of를 이용해 ScaffoldMessenger 찾아야 한다.

즉, MaterialApp widget 밑에 context를 만들어야 한다.

위 예제를 보면 Builder를 이용해 Scaffold Widget을 부모로 하는 context를 만들었다.

### Builder widget없이 Snack bar만들기

MySnackBar라는 custom widget을 Scaffold 밑에 만들어서 Snack bar를 구현할 것이다.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        appBar: AppBar(
          title: Text('앱바'),
        ),
        body: MySnackBar(),
      ),
    );
  }
}

class MySnackBar extends StatelessWidget {
  const MySnackBar({super.key});

  @override
  Widget build(BuildContext context) {
    return Center(
      child: ElevatedButton(
        style: ElevatedButton.styleFrom(
          backgroundColor: Colors.red, // backgroundColor
          foregroundColor: Colors.white, // foregroundColor
        ),
        onPressed: () {
          ScaffoldMessenger.of(context).showSnackBar(
            const SnackBar(
              content: Text(
                'hello',
                textAlign: TextAlign.center,
                style: TextStyle(color: Colors.white),
              ),
              backgroundColor: Colors.teal,
              duration: Duration(milliseconds: 1000),
            ),
          );
        },
        child: Text('Show SnackBar'),
      ),
    );
  }
}
```

### SnackBar action

<img src="/assets/images/snackbar-action.png" title="참고 이미지" alt="이미지" />

사진에 보이는 'Undo'버튼이 SnackBar action이다.

```dart
                  ScaffoldMessenger.of(ctx).showSnackBar(
                    SnackBar(
                      content: Text('Like a new Snack Bar!'),
                      action: SnackBarAction(
                          label: 'Undo',
                          onPressed: () {
                            print("취소");
                          }),
                    ),
                  );
```

### 예전 처럼 화면이동 시 SnackBar 없애기

* ScreenA

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      routes: {
        '/b': (context) => ScreenB(),
      },
      home: Scaffold(
        appBar: AppBar(
          title: Text('ScreenA'),
        ),
        body: Builder(
          builder: (BuildContext ctx) {
            return Center(
              child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  ElevatedButton(
                    onPressed: () {
                      Navigator.pushNamed(ctx, '/b');
                    },
                    child: Text('Go to the ScreenB'),
                  ),
                  ElevatedButton(
                    onPressed: () {
                      ScaffoldMessenger.of(ctx).showSnackBar(
                        SnackBar(
                          content: Text('Like a new Snack Bar!'),
                          duration: Duration(seconds: 5),
                          action: SnackBarAction(
                              label: 'Undo',
                              onPressed: () {
                                print("취소");
                              }),
                        ),
                      );
                    },
                    child: Text('Show SnackBar'),
                  ),
                ],
              ),
            );
          },
        ),
      ),
    );
  }
}
```

* ScreenB

```dart
class ScreenB extends StatelessWidget {
  const ScreenB({super.key});

  @override
  Widget build(BuildContext context) {
    return ScaffoldMessenger(
      child: Scaffold(
        appBar: AppBar(
          title: Text('ScreenB'),
        ),
        body: Center(
          child: ElevatedButton(
            onPressed: () {
              ScaffoldMessenger.of(context).showSnackBar(
                SnackBar(
                  content: Text('ScreenB Snack Bar!'),
                  duration: Duration(seconds: 5),
                ),
              );
            },
            child: Text('Show SnackBar'),
          ),
        ),
      ),
    );
  }
}
```

ScreenB 코드를 중점적으로 보자.

Root ScaffoldMessenger(MaterialApp의 ScaffoldMessenger)가 아닌 개별적인 ScaffoldMessenger를 만들었다.

이제 Root ScaffoldMessenger는 ScreenB의 Scaffold를 정보를 갖고 있지 않다.

우리가 원하는 대로 ScreenA에서 Snackbar를 띄우고 ScreenB로 이동시 바로 Snackbar가 사라지는 것을 볼 수 있다.

하지만 이상하게 ScreenB에서 Snackbar를 띄우고 5초 안에 ScreenA로 가면 ScreenB의 Snackbar가 떠있는 것을 볼 수 있다.

이는 widget tree를 보면 쉽게 이해할 수 있다.

<img src="/assets/images/snackbar-widget-tree.png" title="참고 이미지" alt="이미지" />

ScaffoldMessenger.of에 전달된 context는 ScreenB의 context이고 widget tree 상 우리가 개별적으로 만든 ScaffoldMessenger의 위에 있기 때문이다.

아래와 같이 Builder로 해결할 수 있다.

```dart
class ScreenB extends StatelessWidget {
  const ScreenB({super.key});

  @override
  Widget build(BuildContext context) {
    return ScaffoldMessenger(
      child: Scaffold(
          appBar: AppBar(
            title: Text('ScreenB'),
          ),
          body: Builder(
            builder: (context2) => Center(
              child: ElevatedButton(
                onPressed: () {
                  ScaffoldMessenger.of(context2).showSnackBar(
                    SnackBar(
                      content: Text('ScreenB Snack Bar!'),
                      duration: Duration(seconds: 5),
                    ),
                  );
                },
                child: Text('Show SnackBar'),
              ),
            ),
          )),
    );
  }
}
```

## Toast

라이브러리 필수

Snack bar와 달리 Toast는 Scaffold를 참조할 필요가 없다. 즉, widget tree와 상관없다.

```dart
fluttertoast: ^8.2.4

import 'package:fluttertoast/fluttertoast.dart';
```

구현 코드

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        appBar: AppBar(
          title: Text('앱바'),
        ),
        body: Center(
          child: OutlinedButton(
            onPressed: () {
              flutterToast();
            },
            child: Text('Show Toast'),
          ),
        ),
      ),
    );
  }
}

void flutterToast() {
  Fluttertoast.showToast(
      msg: 'Toast',
      gravity: ToastGravity.BOTTOM, // 토스트 메시지 위치
      backgroundColor: Colors.redAccent,
      fontSize: 20.0,
      textColor: Colors.white,
      toastLength: Toast.LENGTH_SHORT // 토스트 메시지 duration
      );
}
```

## Container Widget

https://docs.flutter.dev/ui/widgets/layout#Single-child%20layout%20widgets

위 링크 <span style="color:#2D3748; background-color:#fff5b1">Single-child</span> layout widgets → Container에 아래와 같은 문구가 있다.

'Containers with no children try to be as big as possible'

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        backgroundColor: Colors.blue,
        
        body: Container(color: Colors.red),
      ),
    );
  }
}
```

<img src="/assets/images/flutter-red-background.png" title="참고 이미지" alt="이미지" />

Scaffold의 배경색은 파란색이고 Container는 빨간색이다. Container는 자식이 없으므로 최대한 많은 영역을 차지하고 앱 화면 전체가 빨간색이 된다.

---

'Containers with children size themselves to their children.'

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        backgroundColor: Colors.blue,
        body: Container(child: Text('hello'), color: Colors.red),
      ),
    );
  }
}
```

<img src="/assets/images/flutter-blue-background.png" title="참고 이미지" alt="이미지" />

Container에게 child로 Text를 줬다. Container는 자식을 갖게 되면 그 자식의 크기로 줄어든다.

## SafeArea

보여주길 원하는 컨텐츠를 화면 밖으로 빠져나가지 않게 한다.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        backgroundColor: Colors.blue,
        body: SafeArea(
          child: Container(
            child: Text('hello'),
            color: Colors.red,
          ),
        ),
      ),
    );
  }
}
```

<img src="/assets/images/flutter-safearea.png" title="참고 이미지" alt="이미지" />

## Column과 Row 그리고 Center

Column은 <span style="color:#2D3748; background-color:#fff5b1">세로축</span>으로 공간을 최대한 차지하며, <span style="color:#2D3748; background-color:#fff5b1">가로축</span>으로는 Childern 가로 크기만큼 차지한다

Center는 원래 Child를 <span style="color:#2D3748; background-color:#fff5b1">정중앙</span>에 위치시키는 위젯이나, Column을 Child로 갖는 경우 Column은 <span style="color:#2D3748; background-color:#fff5b1">세로축</span>공간을 최대한 차지하므로 Center는 세로축 가운데 정렬 기능을 잃어버린다.

Column 세로축도 가운데 정렬하고 싶다면 아래와 같이 속성을 추가해주자.

```dart
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: <Widget>[
              ],
            ),
```

Column이 세로축 공간을 전부 차지하는 것이 싫다면 최소한의 공간만 차지하게 할 수 있다.

```dart
            child: Column(
              mainAxisSize: MainAxisSize.min,
              children: <Widget>[
              ],
            ),
```

Column의 Children을 아래서부터 위로 쌓을 수 있다.

```dart
            child: Column(
              verticalDirection: VerticalDirection.up,
              children: <Widget>[
              ],
            ),
```

Column의 Children을 같은 간격으로 정렬

```dart
            child: Column(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: <Widget>[
              ],
            ),
```

Column의 Children을 최상단, 중단, 최하단 정렬

```dart
            child: Column(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: <Widget>[
              ],
            ),
```

Column의 Children을 가로축 끝으로 정렬

```dart
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.end,
              children: <Widget>[
              ],
            ),
```

안 보이는 컨테이너를 활용해 나머지 컨테이너를 가로축 끝 정렬   
double.infinity - 가로축으로 갈 수 있는 곳 끝까지 간다.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter',
      theme: ThemeData(
          primarySwatch: Colors.red,
          visualDensity: VisualDensity.adaptivePlatformDensity),
      darkTheme: ThemeData.light(),
      home: Scaffold(
        backgroundColor: Colors.green,
        body: SafeArea(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.end,
            children: <Widget>[
              Container(
                width: 100,
                height: 100,
                color: Colors.white,
                child: Text('Container 1'),
              ),
              Container(
                width: 100,
                height: 100,
                color: Colors.blue,
                child: Text('Container 2'),
              ),
              Container(
                width: 100,
                height: 100,
                color: Colors.red,
                child: Text('Container 3'),
              ),
              Container(
                width: double.infinity,
                // invisible Container
              )
            ],
          ),
        ),
      ),
    );
  }
}
```

Column의 Children을 가로축으로 꽉 채우기   
children의 속성 중 width는 필요가 없다. 어짜피 가로축으로 꽉 채우기 때문.

```dart
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.stretch,
              children: <Widget>[
              ],
            ),
```

위에서 설명한 모든 속성은 <span style="color:#2D3748; background-color:#fff5b1">Row</span> widget에서도 똑같이 사용 가능하다.

## Navigator

* Route 개념

  스마트폰에서 하나의 페이지

* Stack 자료구조

  push, pop

* Navigator에 context가 필요한 이유?

  context가 갖고 있는 Widget tree의 위치 정보에 근거하여 현재 페이지를 확인하고 이 페이지 위에 push 함수를 이용해 이동하길 원하는 페이지를 Stack 구조로 쌓는다.

* MaterialPageRoute

  일반적인 화면 전환 애니메이션과 함께 Material Design 스타일의 새로운 페이지를 생성하는 클래스

```dart
  class FirstPage extends StatelessWidget {
  const FirstPage({super.key});

  @override
  Widget build(BuildContext context2) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Page'),
      ),
      backgroundColor: Colors.green,
      body: SafeArea(
        child: Center(
          child: OutlinedButton(
            onPressed: () {
              Navigator.push(
                context2,
                MaterialPageRoute(builder: (context) => SecondPage()),
                // 다른 context를 사용하는 것을 방지하기 위해 builder 사용
              );
            },
            child: Text('페이지 전환'),
          ),
        ),
      ),
    );
  }
}
```

### Navigator.pushNamed();

Navigator.pushNamed를 사용하기 위해선 경로 정의가 필요하다.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      initialRoute: '/',
      // '/'는 index.html과 같은 의미이다.
      routes: {
        '/': (context) => ScreenA(),
        '/b': (context) => ScreenB(),
        '/c': (context) => ScreenC(),
      },
      // 경로 정의
    );
  }
}
```

* ScreenA

```dart
class ScreenA extends StatelessWidget {
  const ScreenA({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("A"),
      ),
      body: Center(
          child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/b');
              // 여기서 context는 ScreenA 것 이다.
            },
            child: Text("ScreenB"),
          ),
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/c');
            },
            child: Text("ScreenC"),
          ),
        ],
      )),
    );
  }
}
```

### home과 initialRoute가 공존한다면?

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: ScreenA(),
      initialRoute: '/',
      routes: {
        '/': (context) => ScreenA(),
        '/b': (context) => ScreenB(),
        '/c': (context) => ScreenC(),
      },
    );
  }
}
```

아래와 같은 에러가 뜬다.

```dart
If the home property is specified, the routes table cannot include an entry for "/", since it would be redundant.
'package:flutter/src/widgets/app.dart':
Failed assertion: line 354 pos 10: 'home == null ||
         !routes.containsKey(Navigator.defaultRouteName)'
```

### Navigator와 context 이해

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Center(
        child: ElevatedButton(
          onPressed: () => Navigator.push(
              context, MaterialPageRoute(builder: (_) => ScreenA())),
          child: Text("페이지 이동"),
        ),
      ),
    );
  }
}
```

위와 같이 하고 버튼을 누르면 아래와 같은 에러가 난다.

```
FlutterError (Navigator operation requested with a context that does not include a Navigator.
The context used to push or pop routes from the Navigator must be that of a widget that is a descendant of a Navigator widget.)
```

여기서 context는 MyApp의 context다. 즉, widget treet상 MaterialApp의 부모이다.

모든 widget은 MaterialApp의 자식(child)이여야 한다.

해결 방법으로는 MaterialApp의 context를 물려받는 widget을 만들거나, Builder를 통해 해결할 수 있다.

* Builder를 통한 해결 방법

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Builder(
        builder: (context2) => Center(
          child: ElevatedButton(
            onPressed: () => Navigator.push(
                context2, MaterialPageRoute(builder: (_) => ScreenA())),
            child: Text("페이지 이동"),
          ),
        ),
      ),
    );
  }
}
```

Builder widget을 통해 MaterialApp의 밑에 context2를 만들었고 이를 이용해 페이지를 이동했다.

### 뒤로가기 버튼 자동생성

Scaffold의 Appbar사용한다면 Navigator로 페이지 이동 시 Appbar 좌측에 자동으로 뒤로가기 화살표 버튼을 만들어 준다.

## String Interpolation

문자열 중간중간 변수를 끼워넣는 것

```dart
  @override
  Widget build(BuildContext context) {
    String name = '김개똥';
    return Scaffold(
      appBar: AppBar(
        title: Text("$name님 반갑습니다"),
      ),
    );
  }
```

## On-boarding Screen

On-boarding Screen이란 앱을 처음 실행시켰을 때 앱을 소개할 수 있다.

```yaml
introduction_screen: ^3.1.12 # pubspec.yaml에 추가
```

* main.dart

  ```dart
  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    const MyApp({super.key});

    @override
    Widget build(BuildContext context) {
      return const MaterialApp(
        home: OnBoardingPage(),
      );
    }
  }
  ```

앱을 첫 실행 시 OnBoardingPage()로 보낸다.

* OnBoardingPage.dart

  ```dart
  class OnBoardingPage extends StatelessWidget {
    const OnBoardingPage({super.key});

    @override
    Widget build(BuildContext context) {
      return IntroductionScreen(
        pages: [
          PageViewModel(
            title: 'Welcome',
            body: '1',
            image: Image.asset('image/1.png'),
            decoration: getPageDecoration(),
          ),
          PageViewModel(
            title: 'Welcome',
            body: '2',
            image: Image.asset('image/2.png'),
            decoration: getPageDecoration(),
          ),
          PageViewModel(
            title: 'Welcome',
            body: '3',
            image: Image.asset('image/3.png'),
            decoration: getPageDecoration(),
          ),
        ],

        // 스킵 버튼
        showSkipButton: true, // 스킵 버튼 활성화
        skip: const Text('Skip'), // 스킵 버튼 텍스트

        // 화면을 스와이프 해서 넘겨도 되지만 이 버튼을 탭 해도 된다.
        next: const Icon(Icons.arrow_forward),

        // 앱 하단 점들에 대한 스타일
        dotsDecorator: DotsDecorator(
          color: Colors.cyan,
          size: Size(10, 10),
          // active - 점이 활성화 됐을 때(현재 화면일 때) 스타일
          activeSize: Size(22, 10),
          activeShape: RoundedRectangleBorder(
            borderRadius: BorderRadius.circular(24),
          ),
          activeColor: Colors.red,
        ),

        // 하단 점 혹은 버튼으로 화면전환 시 애니메이션 효과
        curve: Curves.bounceOut, // IDE에서 마우스 올리면 링크가 뜨며 애니메이션을 미리 볼 수 있다.

        // 온보딩 스크린을 끝까지 봤을때 무엇을 할지 지정해 주는 버튼
        done: const Text('done'),
        onDone: () {
          Navigator.of(context)
              .pushReplacement(MaterialPageRoute(builder: (BuildContext _) {
            // pushReplacement는 기존 stack 쌓이지 않고 widget을 교체해 버린다.
            // 그러므로 뒤로가기 버튼이 사라진다.
            return const MyPage();
            // On-Boarding을 마치면 MyPage()로 보낸다.
          }));
        }, // onDone은 Button의 onPressed와 똑같다.
      );
    }

    PageDecoration getPageDecoration() {
      return const PageDecoration(
        titleTextStyle: TextStyle(
          fontSize: 28,
          fontWeight: FontWeight.bold,
        ),
        bodyTextStyle: TextStyle(
          fontSize: 18,
          color: Colors.blue,
        ),
        imagePadding: EdgeInsets.only(top: 40), // 이미지 윗 패딩
        pageColor: Colors.orange, // 배경색
      );
    }
  }
  ```

## ListView

리스트(Image, Title, Description) 만들기

### GestureDetector, Inkwell

제스쳐 기능을 지원하지 않는 widget을 GestureDetector 혹은 Inkwell로 감싸주면 onTap() 사용가능

Inkwell은 사용자가 터치했을 때 잉크가 퍼지는 효과를 보여준다.

### Card widget

https://api.flutter.dev/flutter/material/Card-class.html

머티리얼 디자인 카드를 쉽게 구현할 수 있다.

### ListView vs ListView.builder

* 공통점

  스크롤이 가능한 배열형 위젯

* 차이점

  ListView - 모든 데이터를 한 번에 불러온다.

  ListView.builder - **그때그때 필요한 만큼만 데이터를 불러온다.**

### ListView 구현 코드 1

ListView의 item은 Card형식으로 만들 것이고, ListView의 item을 터치하면 현재 데이터를 Dialog로 띄울 것이다.

```dart
class ListViewPage extends StatefulWidget {
  const ListViewPage({super.key});

  @override
  State<ListViewPage> createState() => _ListViewPageState();
}

class _ListViewPageState extends State<ListViewPage> {
  // 필요한 변수들 정의
  var titleList = [
    'title1',
    'title2',
    'title3',
  ];

  // 이미지는 각자 준비하자
  var imageList = [
    'image/1.png',
    'image/2.png',
    'image/3.png',
  ];

  var description = [
    'description1 description1 description1 description1 description1 description1 description1 description1',
    'description2 description2 description2 description2 description2 description2 description2 description2',
    'description3 description3 description3 description3 description3 description3 description3 description3',
  ];

  // Dialog를 보여주기 위한 함수 하나 정의
  void showPopup(context, title, image, description) {
    showDialog(
        context: context,
        builder: (BuildContext context) {
          return Dialog(
            child: Container(
              // Dialog의 width는 현재 화면 크기 * 0.6
              width: MediaQuery.sizeOf(context).width * 0.6,
              height: 380,
              decoration: BoxDecoration(
                  borderRadius: BorderRadius.circular(10), color: Colors.white),
              child: Column(
                children: [
                  // 이미지를 사각형 모양으로 출력하는 위젯
                  ClipRRect(
                    borderRadius: BorderRadius.circular(10),
                    child: Image.asset(
                      image,
                      width: 150,
                      height: 150,
                    ),
                  ),
                  // 이미지와 텍스트를 띄워놓기 위한 위젯. Margin과 같은 역할
                  const SizedBox(
                    height: 10,
                  ),
                  Text(
                    title,
                    style: const TextStyle(
                      fontSize: 25,
                      fontWeight: FontWeight.bold,
                      color: Colors.grey,
                    ),
                  ),
                  Padding(
                    padding: const EdgeInsets.all(8),
                    child: Text(
                      description,
                      // Text를 최대 3줄까지 보여준다
                      maxLines: 3,
                      style: TextStyle(
                        fontSize: 15,
                        color: Colors.grey[500],
                      ),
                      textAlign: TextAlign.center,
                    ),
                  ),
                  // 닫기 버튼
                  ElevatedButton.icon(
                    onPressed: () {
                      Navigator.pop(context);
                    },
                    icon: const Icon(Icons.close),
                    label: const Text('Close'),
                  ),
                ],
              ),
            ),
          );
        });
  }

  // 위젯 빌드 시작
  @override
  Widget build(BuildContext context) {
    double width = MediaQuery.sizeOf(context).width * 0.6;

    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'ListView',
          style: TextStyle(
            color: Colors.grey,
          ),
        ),
        backgroundColor: Colors.white,
        elevation: 0,
      ),
      body: ListView.builder(
        // 총 아이템 갯수
        itemCount: titleList.length,
        // 아이템 갯수만큼 반복하며 만든다.
        itemBuilder: (context, index) {
          // List가 터치되야 하므로 InkWell로 감쌋다.
          return InkWell(
            onTap: () {
              // 터치 시 팝업 띄우기
              showPopup(context, titleList[index], imageList[index],
                  description[index]);
            },
            child: Card(
              child: Row(
                children: [
                  SizedBox(
                    width: 100,
                    height: 100,
                    child: Image.asset(imageList[index]),
                  ),
                  Padding(
                    padding: const EdgeInsets.all(10),
                    child: Column(
                      children: [
                        Text(
                          titleList[index],
                          style: const TextStyle(
                            fontSize: 22,
                            fontWeight: FontWeight.bold,
                            color: Colors.grey,
                          ),
                        ),
                        SizedBox(
                          width: width,
                          child: Text(
                            description[index],
                            style: TextStyle(
                              fontSize: 15,
                              color: Colors.grey[500],
                            ),
                          ),
                        ),
                      ],
                    ),
                  )
                ],
              ),
            ),
          );
        },
      ),
    );
  }
}
```

### ListView 구현 코드 2

ListView의 item을 터치하면 현재 데이터를 다른 페이지로 넘겨서 보여줄 것이다.

* model.dart

  Animal 클래스를 정의하였다.

  ```dart
  class Animal {
    final String name;
    final String imgPath;
    final String location;

    Animal(this.name, this.imgPath, this.location);
  }
  ```

* mypage.dart

  ```dart
  class MyPage extends StatefulWidget {
    const MyPage({super.key});

    @override
    State<MyPage> createState() => _MyPageState();
  }

  class _MyPageState extends State<MyPage> {
    // 필요한 List 정리
    static List<String> animalName = [
      'bear',
      'camel',
      'deer',
    ];

    // 이미지는 알아서 준비하자
    static List<String> animalImagePath = [
      'image/bear.png',
      'image/camel.png',
      'image/deer.png',
    ];

    static List<String> animalLocation = [
      'mountain',
      'dessert',
      'forest',
    ];

    // animalLocation길이 수 만큼(3번) 반복하면서 index(0, 1, 2)를 이용해 Animal인스턴스 생성
    final List<Animal> animalData = List.generate(
      animalLocation.length,
      (index) => Animal(
        animalName[index],
        animalImagePath[index],
        animalLocation[index],
      ),
    );

    // 위젯 빌드 시작
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('ListView'),
        ),
        body: ListView.builder(
          // animalData의 길이만큼 item 생성
          itemCount: animalData.length,
          itemBuilder: (BuildContext context, int index) {
            return Card(
              // ListTile은 행의 높이가 고정되어 있다.
              child: ListTile(
                title: Text(animalData[index].name),
                leading: SizedBox(
                  height: 50,
                  width: 50,
                  child: Image.asset(animalImagePath[index]),
                ),
                onTap: () {
                  Navigator.of(context).push(MaterialPageRoute(
                    // 데이터를 전달하려면 AnimalPage 생성자에서 Animal을 받게 만들어야 한다.
                    builder: (context) => AnimalPage(animal: animalData[index]),
                  ));
                },
              ),
            );
          },
        ),
      );
    }
  }
  ```

* animal_page.dart

  ```dart
  class AnimalPage extends StatelessWidget {
    // animal변수는 Null 값을 가질 수 없으므로 required를 붙여줬다.
    // this.animal는 선택적으로 구현할 수 있는 Named argument이나 required인해 필수가 되었다.
    const AnimalPage({super.key, required this.animal});

    // 페이지 이동시 Animal을 받기위해 animal 속성을 만들고 위 생성자에 추가해 줬다.
    final Animal animal;

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text(animal.name),
        ),
        body: Center(
          child: Column(children: [
            Image.asset(animal.imgPath),
            Text(animal.location),
          ]),
        ),
      );
    }
  }
  ```

## 좋아요 버튼 만들기

```yaml
like_button: ^2.0.5
```

```dart
LikeButton(
          size: 30,
          isLiked: false,
          likeCount: 1,
)
```

## 반응형 웹

### MediaQuery class

MediaQuery.of - 현재 디바이스의 사이즈를 알아낼 수 있다.

MediaQuery.of를 사용하면 필드가 변경될 때마다(예: 사용자가 장치를 회전하는 경우) 위젯이 자동으로 다시 빌드된다.

```dart
// 전체 width의 0.6만 사용하기
double width = MediaQuery.of(context).size.width * 0.6;

// toStringAsFixed(2) 소숫점 2자리 까지만 출력
var width = MediaQuery.of(context).size.width.toStringAsFixed(2);

var height = MediaQuery.of(context).size.height.toStringAsFixed(2);

// 가로, 세로 비율
var aspectRatio = MediaQuery.of(context).size.aspectRatio.toString(); 

// 화면의 방향(세로 모드 (포트레이트)와 가로 모드 (랜드스케이프))
var orientation = MediaQuery.of(context).orientation; 
```

### LayoutBuilder Class

https://api.flutter.dev/flutter/widgets/LayoutBuilder-class.html

부모위젯 크기에 따라 위젯트리를 빌드한다

즉, 기기 전체 화면의 크기가 아니라 위젯의 크기를 알아내는 것이 목표

빌더 메소드가 호출되는 상황 4가지, 이번 예제는 2번째 상황을 이용한다.

* The first time the widget is laid out.
* When the parent widget passes different layout constraints.
* When the parent widget updates this widget.
* When the dependencies that the builder function subscribes to change.

## Stateless vs Stateful

State란? UI가 변경되도록 영향을 주는 데이터(서버에서 받아온 값, 체크박스 체크 여부, 텍스트 필드에 값이 입력되고 있는지)

Statelss란? State가 변하지 않는 위젯. rebuild되지 않는 한 상태가 변하지 않는다. (rebuild는 비용이 저렴하다!)

조금매운맛 2번 강좌 한 번 더보기!@!@!

## Flutter의 final, const

final, const는 모두 한 번만 초기화 가능하다.

### final (run-time constant)

* final

  ```dart
  class Aminal {
    final String name;
    final String imgPath;
    final String location;
  }
  ```

* 앱이 실행되기 전까지 타입을 정할 수 없는 경우가 있다.
즉, 런타임 때 변수를 초기화 하기 위해 사용한다.

* final초기화 방법
  1. 변수 생성시 초기값 주기
  2. 객체 생성자를 통해 final 변수 초기값 전달

* final 변수는 rebuild를 통해 새로운 값으로 바꿀 수 있다

```dart
class MyWidget extends StatelessWidget {
  const MyWidget({super.key, required this.score});

  final score;

  @override
  Widget build(BuildContext context) {
    return Text(score);
  }
}

// 위와 같은 위젯이 있다면...

MyWidget(score: '30')

MyWidget(score: '100')

// 이런 식으로..
```

### const (compile-time constant)

* 컴파일 과정에서 상수가 된다.

* const초기화 방법
  1. 변수 선언과 동시에 초기화 해야한다.

* Static 데이터. 즉, 한 번 정해지면 바뀌지 않는 데이터를 사용하는 widget 앞에 const를 붙이면 좋다.   
화면이 rebuild 될때 const가 붙은 widget은 rebuild하지 않고 재사용한다. **성능↑**

* 만약 컴파일 시에 변하지 않는 상수값이라면 당연히 런타임 시에도 변하지 않을 것이다.

### 예시

```dart
const time = DateTime.now();
// 현재 시간은 런타임 환경에서 알 수 있으므로 에러난다.
final time = DateTime.now();
// 가능
```

## Null safety

primitive type은 기본적으로 null을 허용하지 않는다. 예를들어 int형은 기본적으로 덧셈과 같은 기능이 가능해야 하므로 null은 올 수 없다.

### lazy initialization

```dart
class Person {
  late int age = calculate();
}

int calculate(){
  return 30;
}

void main() {
  Person p = Person();
  print('abcd');
  print(p.age);
}

// 출력 순서
// abcd
// 30
```

즉 main 함수 첫 번째 Person 객체가 생성될 때 calculate()함수가 실행되지 않는다.
마지막에 print(p.age);로 age변수가 참조될 때 age를 초기화 하는 것을 lazy initialization이라고 한다.

## WidgetsFlutterBinding.ensureInitialized();
main함수에서 runApp()이 호출되기 전까진 플러터 엔진이 초기화되지 않는다. 하지만 Firebase.initializeApp()같은 비동기 함수는 플러터와 통신을 하길 원한다. 즉, main함수 내에서 플러터 엔진 초기화 후에 Firebase초기화 해야한다. 플러터 코어 엔진 초기화 하는 함수가 바로 WidgetsFlutterBinding.ensureInitialized(); 이다.

## Tip

* onTap(), onPressed() 차이?

    기능상 거의 동일

    onPressed() - 주로 버튼에 사용

    onTap() - gestureDetector, InkWell에 사용, 길게누르기 두 번 탭하기에 사용

* _ (언더스코어)

  필요없는, 안쓰는 매개변수를 나타낸다.

* static

* SizedBox와 Container

  * Container는 다양한 속성과 메소드를 갖고 있다.
  * SizedBox는 width, height, child 같이 필요한 속성만 갖고 있다.

  단순히 공간을 차지하는 widget을 생성(인스턴스화)한다면 SizedBox를 써주는 게 효율적이다.

  SizedBox는 const생성자를 갖고 있기 때문에 Runtime 인스턴스를 생성할 필요가 없기 때문이다. **성능↑**


## 고민들..

* 화면 내 Widget 분리 시 함수 vs Class

  * Class 장점

    * 부모위젯이 rebuild를 하여도 const를 붙여주면 Class로 분리한 위젯은 rebuild 안함

    * buildcontext를 갖고 있다.

## 안드로이드 키 생성

```
keytool -genkey -v -keystore ~/키파일명.jks -keyalg RSA -keysize 2048 -validity 10000 -alias 키별칭
```

나는 사용자 루트 디렉토리 ~/ 에 키를 생성했다. 키 파일명은 test-keystore.jks. 별칭은 test로 했다.

### 키 확인 방법

```
keytool -list -v -keystore ~/test-keystore.jks -alias test
```

위 명령어를 통해 키 확인이 가능하다.

## Error

VScode와 FVM을 사용하던 도중 Terminal에서 'fvm flutter run'을 사용하면 앱이 켜지지만, VScode의 'Start Debugging'버튼을 누르면 fvm으로 설정한 version이 아니라 다른 flutter version으로 실행됐다.

버전 차이로 앱은 켜지지도 않았다.

Flutter Project내에 .dart_tool/version 파일을 확인하면 'Start Debugging'버튼을 눌렀을 때 flutter version이 바뀌는 걸 확인할 수 있다.

```
/Users/<사용자 이름>/Library/Application Support/Code/User/settings.json
```

위 파일 "dart.flutterSdkPath" 부분이 VScode flutter sdk를 고정시켜 놓은 것 이었다. 주석 처리하자...

---

VScode에서 The Flutter Daemon has terminated. 알림이 뜨며 내 안드로이드 기기가 인식되지 않았다.

```
cd ~/Library/Android/sdk/platform-tools/

./adb devices
```

위 명령어를 치면 아래와 같은 문구가 떳다.

```
* failed to start daemon
adb: failed to check server version: cannot connect to daemon 
```

컴퓨터 재부팅을 하니 해결됐다.

---

```
C:\Users\Administrator\Desktop\flutterPractice\android\app\src\debug\AndroidManifest.xml Error:
	uses-sdk:minSdkVersion 19 cannot be smaller than version 21 declared in library [:fluttertoast] C:\Users\Administrator\Desktop\flutterPractice\build\fluttertoast\intermediates\merged_manifest\debug\AndroidManifest.xml as the library might be using APIs not available in 19
	Suggestion: use a compatible library with a minSdk of at most 19,
		or increase this project's minSdk version to at least 21,
		or use tools:overrideLibrary="io.github.ponnamkarthik.toast.fluttertoast" to force usage (may lead to runtime failures)

┌─ Flutter Fix ─────────────────────────────────────────────────────────────────────────────────┐
│ The plugin fluttertoast requires a higher Android SDK version.                                │
│ Fix this issue by adding the following to the file                                            │
│ C:\Users\Administrator\Desktop\flutterPractice\android\app\build.gradle:                      │
│ android {                                                                                     │
│   defaultConfig {                                                                             │
│     minSdkVersion 21                                                                          │
│   }                                                                                           │
│ }                                                                                             │
│                                                                                               │
│ Following this change, your app will not be available to users running Android SDKs below 21. │
│ Consider searching for a version of this plugin that supports these lower versions of the     │
│ Android SDK instead.                                                                          │
│ For more information, see:                                                                    │
│ https://docs.flutter.dev/deployment/android#reviewing-the-gradle-build-configuration          │
└───────────────────────────────────────────────────────────────────────────────────────────────┘
Exception: Gradle task assembleDebug failed with exit code 1
```

flutter project 내에 android/app/build.gradle 파일을 열고 아래와 같이 바꾸니 해결 됐다.

```gradle
minSdkVersion flutter.minSdkVersion
↓
minSdkVersion 21
```

---

```
Vertical viewport was given unbounded height.

Horizontal viewport was given unbounded height.

RenderFlex children have non-zero flex but incoming height constraints are unbounded.
```

**발단**

페이지 구성 중 위젯의 height를 주지 않고(MediaQuery 포함) 위젯의 자식에 크기에 따라 부모의 height가 결정되게 만들고 싶었다.

**문제**

스크롤이 되는 리스트에 또 스크롤이 되는 리스트를 넣을 때 혹은 SingleChildScrollView → Column → Expanded 구조일때 에러가 났다.

찾아보니 SingleChildScrollView는 자식 위젯의 높이 제약을 없앤다고 한다.

Column → Column → Expanded 및 SingleChildScrollView → Column → Expanded도 안되는 듯 하다.

**해결 및 다른 문제들..**

SingleChildScrollView → Column → ListView의 shrinkWrap을 true

하지만 scrollDirection: Axis.horizontal(수평 스크롤)은 여전히 height를 줘야 했다.

리스트 안에 리스트가 있는 경우 Sliver를 사용하는 것이 좋다고 한다.

참고

https://velog.io/@vrdhan212/%ED%94%8C%EB%9F%AC%ED%84%B0-%EC%A0%9C%EC%95%BD-%EC%A1%B0%EA%B1%B4

https://zzaebok.github.io/flutter/flutter-nested-listview/

---

Container를 width, height없이 Padding과 자식의 크기로 디자인 하려고 했다. 하지만 부모의 크기만큼 최대로 확장되길래 찾아봤더니 이런 문구가 있었다

Flutter 공식문서 첨부...

```
If the widget has no child, no height, no width, no constraints, and no alignment, but the parent provides bounded constraints, then Container expands to fit the constraints provided by the parent.
```

해결방법

Container를 Align으로 감싸면 된다.

https://stackoverflow.com/questions/54225462/flutter-why-is-container-width-not-honoured?rq=3

---

안드로이드 빌드 중 아래와 같은 에러가 났다.

```
A failure occurred while executing com.android.build.gradle.internal.tasks.CheckAarMetadataWorkAction
```

**해결**

android 폴더 경로에서

```
./gradlew clean
./gradlew build
```

---
