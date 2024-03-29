---
title: HTML Summary
tags: html
---

Link: [Html4][id]

[id]: https://ksg0000.github.io/2023/01/18/html4.html

HTML summary
-------------

```

HTML
Hyper Text Markup Language

문서를 구성하는 요소

1. 콘텐츠(Contents)
	사용자의 접근성을 높이기 위해 text로 표현한다.

2. 구조
	콘텐츠를 구분짓는 형태이다.
	콘텐츠는 ‘tag(태그)’를 통해 구분한다.
	ex) 제목, 문장 , 목록, 표 , 폼 (`블록 타입 태그들`)

3. 스타일(Style)

-------------------------------------------------------------------------------

웹문서 = 링크 + 문서

HyperText : link가 연결되어있는 text
(hyperlink, simply a link)

MarkUp: 콘텐츠 구조화를 위해 구분자를 넣어주는 것

아웃라인 잡기 - 제목 잡기

html 과 css에서 문장안의 단어 구분자는 카멜 표기법이 아닌 `-` 을 쓰도록 하자. 
문장과 문장간의 구분처럼 더 큰 단위의 구분자가 필요할때는 `_` 와 같은 것을 쓰자.

-------------------------------------------------------------------------------

Block Type Tag 블록 타입 태그

콘텐츠를 가장 말단에서 감싸는 태그

방을 만드는 태그이다.
제목 태그(h1,.....)
문장 태그(p)
목록 태그(ol, ul, menu > li, dl>dt,dd)
표(table)
폼(form)

div 태그(어디에도 포함되지 않는 블록)
	CSS를 하다가 스타일을 위해서 추가하는 태그는 div로 하자.
	(문서 아웃라인에 영향을 주지 않는다.)
	자매품으로 inline에는 span 태그가 있다.
	과거에는 섹션을 위한 태그는 존재하지 않아서 div 태그를 사용했다.
	=> 포함관계를 세어서 섹션에 대한 제목의 넘버를 직접 부여하는 작업이 필요했기 때문.
	=> 새로운 섹션을 위한 태그가 등장

섹션 태그 (section tag)
	section 의 조건: 제목 + 내용(콘텐츠)
	제목이 이끌고 있는 영역. 바디 태그도 포함한다.
	태그를 이용해 아웃라인을 잡는 새로운 방식
	섹션에는 header / main / footer 와 같은 영역이 존재한다.
	section의 부분(영역)을 만드는 태그로 div가 사용되었는데
	section의 필수 영역에 대해서는 시맨틱한 태그가 추가 되었다.
	-header
	-main
	-footer
	과거에는 이런 영역이 태그로 존재하지 않아서 div를 사용했다.
	지금은 그런 영역을 위한 특수한 이름의 태그가 존재하는 것이다.
	시맨틱(의미가 부여된) section: <body />, <section />, <article />, <aside />, <nav />
	- article > header,footer,main(X)
	- aside > header,footer,main(X)
	- nav > header(X),footer(X),main(X)
	- body > header,footer,main(O)

시맨틱 태그 (semantic tag)
	콘텐츠 영역을 구분해줄 수 있게 의미가 살아있는 태그. 
	sementic : 의미의, 의미론적인
	<header />, <main />, <footer />

(시맨틱 웹 : 컴퓨터가 사람을 대신하여 정보를 읽고 이해하고 가공하여 새로운 정보를 만들어 낼 수 있도록, 이해하기 쉬운 의미를 가진 차세대 지능형 웹)

-------------------------------------------------------------------------------

표 태그 (table 태그)

<table>
    	<caption></caption>
    	<thead>
    		<tr>
    			<td></td>
    			<td></td>
    			<td></td>
    			<td></td>
    		</tr>
    	</thead>
    	<tbody>
    		<tr>
    			<td></td>
    			<td></td>
    			<td></td>
    			<td></td>
    		</tr>
    	</tbody>
</table>

tr : table row
th : data head. 나중에 태그를 보고 열에서 특별한 데이터인지 판단할 수 있다.
<thead>, <tfoot>, <tbody> : 헤드나 바디 정보를 따로 추출해야할 필요가 있을 때 구분해주면 좋다.
tbody는 구분하지 않아도 자동으로 태그가 달린다. tbody는 여러개를 사용할 수 있다. thead와 tfoot은 하나만 존재할 수 있다.
테이블 태그 안에는 <div> 태그 쓰지 말 것.
colspan : Cell 열 병합 가능
rowspan : 행 병합
caption : 테이블에 대한 정보를 캡션으로 보여줄 수 있다.
col
colgroup

-------------------------------------------------------------------------------

폼 태그 (form)

<form action="signup"> <!--action 서버에서 찾을 프로그램-->
    <fieldset> <!--울타리-->
        <legend>회원 가입 정보</legend> <!--울타리의 이름-->

        <div>
            <label for="userId">아이디</label> <!--for 옵션으로 id를 설정해서 바라보는 태그 지정 가능-->
            <input name="id" id="userId"> <!--id를 키값으로 입력값을 전달함-->
            <output>유효한 아이디입니다.</output> <!--입력값에 대한 결과값에 해당하는 태그 span 도 가능-->
        </div>
        <div>
            <label>비밀번호</label>
            <input name="pwd"> <!--pwd를 키값으로 입력값을 전달함-->
            <output>유효한 비밀번호입니다.</output> <!--입력값에 대한 결과값에 해당하는 태그 span 도 가능-->
        </div>
    </fieldset>

    <fieldset> <!--라디오 버튼-->
        <legend>가장 좋아하는 취미</legend>
        <input type="radio" name="hobby1" value="1">
        <label>애니 시청</label>
        <input type="radio" name="hobby1" value="2">
        <label>드라마 시청</label>
        <input type="radio" name="hobby1" value="3">
        <label>축구 시청</label>
    </fieldset>

    <fieldset> <!--체크 박스-->
        <legend>좋아하는 취미</legend>
        <input type="checkbox" name="hobby2" value="1">
        <label>애니 시청</label>
        <input type="checkbox" name="hobby2" value="2">
        <label>드라마 시청</label>
        <input type="checkbox" name="hobby2" value="3">
        <label>축구 시청</label>
    </fieldset>

    <fieldset> <!--콤보 박스-->
        <legend>좋아하는 취미</legend>
        <select name="hobby3">
            <option>선택</option>
            <option value="1">애니 시청</option>
            <option value="2">드라마 시청</option>
            <option value="3">축구 시청</option>
        </select>
    </fieldset>

    <fieldset> <!--멀티콤보 박스-->
        <legend>좋아하는 취미</legend>
        <select multiple name="hobby3">
            <option>선택</option>
            <option value="1">애니 시청</option>
            <option value="2">드라마 시청</option>
            <option value="3">축구 시청</option>
        </select>
    </fieldset>

    <datalist>
        <option value="여행1">
        <option value="여행2">
        <option value="여행3">
        <option value="여행4">
    </datalist>

    <div>
        <label>나이</label>
        <input name="age" required type="number" min="10" max="100">
    </div>

    <input type="submit" value="회원가입">
    <!--value 는 버튼에 보이는 이름 / input type submit을 클릭하면 입력값을 서버에 전달가능.-->

    <button>회원가입</button>
    <button><img src="/path"></button>
    <!--submit과 기능은 같음. 하지만 스타일을 자유롭게 수정가능함. 이미지 버튼-->

    <input type="button" value="회원가입">
    <!--그냥 생긴 모양이 버튼일 뿐임.-->

    <!--html5에서 추가된 태그들. 브라우저별로 ui가 달라져서 잘 안씀 / 라이브러리를 사용하는것을 권장-->
    <label>가입일</label>
    <input type="date">
    <label>색상</label>
    <input type="color">
    <label>볼륨</label>
    <input type="range" min="0" max="100">
</form>

`input 태그`에서 id는 클라이언트에서 사용하기 위한 식별자이다. 
name 은 서버에서 사용하기 위한 식별자이다. 
서버로 전달되기 위한 입력필드에 해당하는 element만 name을 사용할 수 있다.
라디오버튼을 사용할때 그룹으로 묶기 위해서는 `name`을 같은걸로 지정하면 된다. 전달하려는 값은 `value`에 지정하면 된다.
같은 키값으로 서버에 전송하면 서버에서 키를 이름으로 같는 배열에 값을 담아준다.
필수 입력 필드를 위한 속성 `required`. type으로 입력값의 타입과 범위 설정이 가능하다.
`placeholder` 속성을 hint로 사용 가능하다.
`autofocus` 속성을 설정하면 클릭 없이 포커스 부여가 가능하다.
자동완성은 내가 한번이라도 서버에 전송했던 내용이 나온다.
name 속성에 부여된 값만 같으면 다른 사이트라도 상관없이 나타난다.
브라우저 자체에서 자동완성 기능을 끌수도 있고, `autocomplete 속성을 off`로 부여 하면 자동완성 입력이 해제된다.
`pattern` : 인풋 옵션으로 정규식 패턴을 추가해서 필터링이 가능하다.

-------------------------------------------------------------------------------

inline Tag 인라인 태그

컨텐츠를 설명하는 태그다. 방을 갖지 않는다. 콘텐츠를 설명하기 위한 태그만 남았다.
<span /> : 스타일을 위한 범용적인 태그
<u />, <i />, <b />, <br /> : 의미를 위한 태그로 바뀌었다.
<a />

-------------------------------------------------------------------------------

Regular Expression 정규식
mdn javascript 정규표현식 URL: https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_Expressions
문자열에서 바뀔 수 있는 부분과 고정된 부분을 나눈다. 그리고 바뀔 수 있는 부분을 기호로 대신한다.
대표적인 정규 표현식
[0123456789abcdef] → 이 자리에 들어올 수 있는 값 종류
[0-9] → 축약형
\d{4} → 정수가 4번 들어온다. 그룹화해서 범위 표현 가능
\d{3,4} → 정수가 3개 혹은 4개 입력

-------------------------------------------------------------------------------

Entity
mdn Entity URL: https://developer.mozilla.org/en-US/docs/Glossary/Entity
문서내에서 사용되면 문제가 발생하는 문자를 대신해서 쓸 수 있는 키워드. 
&로 시작해서 ;로 끝난다.

-------------------------------------------------------------------------------

Emmet Snippets
VS code 플러그인이다. 약어를 사용해서 빠르게 태그를 생성할 수 있다.

#page>div.logo+ul#navigation>li*5>a{Item $}
--> 생성
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>

50강 Visual Studio Code Emmet snippets URL: https://docs.emmet.io/
해당 사이트 접속 후 > 좌측 사이드바 Abbreviations > Syntax 에서 참고

-------------------------------------------------------------------------------

경로
상대 경로 : 현재 내가 존재하는 위치에서 경로를 찾아가는 방법.
      수정이 편하기 때문에 일반적으로 사용할 것이 권장된다.
절대 경로 : Root 위치부터 경로를 찾아가는 방법.
      페이지 구조 변경을 하면 모든 경로를 수정해야 하기 때문에 상대적으로 사용이 지양된다.

/
root 경로
./
현재 경로
../
이전 경로

```
