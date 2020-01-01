# HTML 태그



## Heading 태그 

제목을 표현할 때 사는 태그. 제목의 중요도에 따라 `<h1>` ~ `<h6>`  까지 있다.

`<p>` 문단 단락 태그. 여백을 준다

`<br>` 개행 태그. 띄어쓰기를 하게 해준다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<h1>역사</h1>

<h2>개발</h2>

<p>
팀 버너스리 <br>
1980년, 유럽 입자 물리 연구소(CERN)의 계약자였었던 물리학자 팀 버너스리가 HTML의 원형인 인콰이어를 제안하였다. 인콰이어는 CERN의 연구원들이 문서를 이용하고 공유하기 위한 체계였다. 
1989년에 팀 버너스리는 인터넷 기반 하이퍼텍스트 체계를 제안하는 메모를 작성했다.[2] 버너스 리는 1990년 말에 HTML을 명시하고, 브라우저와 서버 소프트웨어를 작성했다. 
그 해에 버너스리와 CERN 데이터 시스템 엔지니어 로버트 카일리아우와 함께 CERN측에 자금 지원을 요청하였지만, 이 프로젝트는 CERN으로부터 정식으로 채택 받지 못했다.
 버너스리의 개인적인 기록[3] 에 1990년부터 "하이퍼텍스트가 사용되는 여러 분야의 일부"를 열거했고 백과사전을 그 목록의 첫 번째로 두었다.
</p>

<h2>최초 규격</h2>

<p> 
HTML 최초의 일반 공개 설명은 1991년 말에 버너스리가 처음으로 인터넷에서 문서를 "HTML 태그"(HTML tag)로 부르면서 시작되었다.[4][5]
</p>

<p>
그것은 머릿글자로 이루어진 20개의 요소를 기술하였고, 상대적으로 HTML의 단순한 디자인이었다. 하이퍼링크를 제외한 HTML 태그들은 CERN 자체의 SGML 기반 문서화 포맷인 SGML GUID에 강하게 영향을 받았다. 이 요소 중 13개는 HTML 4 버전에서도 여전히 존재한다.[6]
</p>

<p>
HTML은 동적인 웹 페이지의 웹 브라우저를 통한 문자와 이미지 양식이다. 문자 요소의 대부분은 1988년 ISO 기술 보고서 9537 SGML을 이용한 기법에서 찾을 수 있다. 하지만 SGML 개념의 일반적인 마크업은 단지 개별 효과 보다는 요소 기반이고 또한 구조와 처리의 분리(?)(HTML은 CSS와 함께 이 방향으로 점진적으로 이동해 왔다.)
</p>

<p>    
버너스리는 SGML 응용 프로그램이 되는 HTML을 고안해야 했고 그것은 공식적으로 IETF(국제 인터넷 표준화 기구)에 의하여 1993년 중반, HTML 규격에 대한 최초의 제안을 간행물로 정의했다. (버너스리와 덴 콘놀리에 의한 문법을 규정하는 SGML 문서 형식 정의(SGML DTD)가 포함된 "하이퍼텍스트 마크업 언어(HTML)" 인터넷 초안[7]) 이 초안은 6개월 후 만료된다. 하지만 NCSA 모자이크 브라우저의 인라인 이미지를 내장하는 사용자 정의 태그의 사례는 주목할 만 했고, 성공적인 프로토타입에 대한 표준을 기반한 IETF의 철학을. [8] 마찬가지로 데이브 라그렛의 경쟁 인터넷 초안인 "HTML+ (하이퍼텍스트 마크업 포맷)"은 1993년 말에 테이블과 기입양식 같은 요소들을 이미 구현하여 표준화 제안을 했다.[9]
</p>

</body>
</html>
```



## 텍스트 표현 태그

- `<b>`

  글자를 굵게 표현한다.

- `<i>`

  글자의 이탤릭체를 표현한다

- `<u>`

  글자에 밑 줄을 표현한다.

- `<s>`

  글자에 중간 선을 그어준다.



## 앵커 태그

링크 생성 태그. 많이 / 자주 사용된다.

```html
<a href="http://www.naver.com/" target="_blank">네이버</a>
```

앵커 태그는 `href` 속성을 반드시 가지고 있다. href 값은 실제로 이동 할 url 을 가지고 있다.

내부 링크로 이동시에는 `href="#id"` 를 사용할 수도 있다.

##### target 속성

target 은 링크된 리소스를 어디에 표시할지 나타내는 속성이다.

- _self 

  현재 화면에 표시

- _blank

  새 탭으로 표시



## 의미 없는 요소들

순전히 무언가를 담기 위해 사용되는 태그들. `style` 을 주거나, 서버에서 보내는 데이터를 담기 위해 사용된다. HTML 은 문서를 웹에 나타내기 위해 만들었기 때문에, 생겼다. 

대표적 의미없는 요소

- division

`<div>` 태그. 블록 레벨 요소.
블록레벨은 라인 하나를 다 채워서 표시된다.

- span

`<span>` 태그. 인라인 요소
라인위에 표시된다. 블록 레벨에 주로 들어간다.
이전에 배웠던 `p` 가 블록, `b,s,i` 같은 태그들은 인라인 요소이다. 

```html
    <div>
        <span>Lorem</span> ipsum dolor sit.
    </div>
```

## 리스트 요소 

리스트를 표현하는 태그. 일련 항목으로 사용할 태그들. 네이버 실시간 검색어와 같은데 사용된다.

- ul

순서가 없는 리스트들. 나열된 항목이 순서와 상관 없을 때 사용된다. 

```html
    <div class="ul-list">
        <ul>
            <li>콩나물</li>
            <li>김치</li>
            <li>국간장</li>
        </ul>
    </div>
```

- ol

순서가 있는 리스트 들. 요리 하는 방법이면 순서가 필요하기 때문에 `ol` 태그를 써야한다. 앞에 숫자가 붙는다.

- dl 

용어와 그에대한 정의를 나타내는 리스트. 설명을 기술한다 하여 description list 라 한다.
용어와 설명이 세트를 이루고, 하나 이상의 항목으로 구조가 나타난다. 

`dl` 안에 제목 `dt` 와 내용 `dd` 가 한 쌍을 이룬다. 용어 하나에 여러개 정의가 들어갈 수도 있다.

example
```html
    <div class="lists">
        <h1>월드컵 조 편성</h1>
        <ol>
            <!-- ol 태그의 자식은 li ol 이 선언되면 li 만 올 수 있다. -->
            <li>
                <!-- li 에는 여러개가 올 수 있다.-->
                A조
                <ul>
                    <li>러시아</li>
                    <li>우루과이</li>
                    <li>이집트</li>
                    <li>사우디아라비아</li>
                </ul>
            </li>
            <li>
                B조
                <ul>
                    <li>이란</li>
                    <li>스페인</li> 
                    <li>포르투칼</li>
                    <li>모로코</li>
                </ul>
            </li>
        </ol>    
    </div>
```

## 이미지 태그 

문서에 이미지를 삽입하는 태그 

- 문서에 이미지 삽입
- src : 경로를 저장한다
  상대경로와 절대경로가 있다.
  상대경로 - ./ 를 사용한다. 생략가능 ../ 의 경우 상위 폴더 이동.
  절대경로 - 실제 이미지가 위치한 곳의 전체 경로. 로컬이면 `c://` 부터 
- alt : 이미지의 대체 텍스트를 입력한다.
  반드시 필요한 속성. 시각 장애인의 경우 컨텐츠 확인을 할 수 없어, 스크린 리더 보조기가 대체 테스트 속성을 통해 사용할 수 있다.
- width / height : 이미지에 가로 / 세로 크기를 지정한다. 
  이미지가 고정적이지 않기 때문에지정, 만약 이미지가 고정적이면, 성능적인 측면에서 좋다. 

##### example

```html
 <div class="image-test">
        <img src="https://enrilemoine.com/wp-content/uploads/2018/08/Jalapen%CC%83o-and-Serano-Pepper-Pizza-SAVOIR-FAIREby-enrilemoine-4-768x1109.jpg" alt="pizza">
    </div>
```
이미지가 크니까, width, height 를 지정해보자. 

```html
<img src="https://enrilemoine.com/wp-content/uploads/2018/08/Jalapen%CC%83o-and-Serano-Pepper-Pizza-SAVOIR-FAIREby-enrilemoine-4-768x1109.jpg" alt="pizza" width="400">
```
width 만 줄였는데, 세로도 알아서 조절이 되었다. 

height 도 적용해보기
```html
<img src="https://enrilemoine.com/wp-content/uploads/2018/08/Jalapen%CC%83o-and-Serano-Pepper-Pizza-SAVOIR-FAIREby-enrilemoine-4-768x1109.jpg" alt="pizza" width="400" height="400">
```
또 줄어들었다. 하나를 설정 안해 두면, 해당 사진 비율대로 줄어 든다. 두가지 비율을 안맞으면 이미지가 왜곡 될 수 있다.

##### 이미지 확장자 포맷

- jpg
  전통적으로 웹에서 많이 사용하는 포맷. 압축률 높고, 사진 일반적인 글에 다 사용. 아쉽게 투명 X
- gif
  색이 제한적. 용량이 작음. 애니메이션 / 투명이미지 지원 
- png
  반투명 / 투명 지원. 가장 핫한 포맷이나 용량이 살짝 크다. 하지만 인기템 


## 테이블 태그

데이터 표를 나타나는 태그. 어떤 복잡한 데이터를 표시할 때 사용. 

행 / 열 = row / col 로 표시된다. 

- td, th
  한칸. 테이블 셀

- tr
  한행. 테이블 로우

- table
  전체 테이블

조금 복잡하다. 그래서 구조를 나타낼 수 있는 태그들을 제공한다

- caption

테이블 제목. 테이블 가장 위에 선언 되어야 한다

- thead / th

테이블 제목 행 그룹화. th 쓰면 굵게 표시된다.


- tfoot

바닥 행. 위 표처럼 내용 합계 쓸 때 사용한다

- tbody

본문 태그. 

tfoot 은 th / tbody 안에 써져도, 가장 마지막에 출력된다.

```html
  <table>
    <caption>Monthly saving</caption>
    <thead>
      <tr>
        <th>Month</th>
        <th>Saving</th>
      </tr>
    </thead>
    <tfoot>
      <tr>
        <td>Sum</td>
        <td>180</td>
      </tr>
    </tfoot>
    <tbody>
      <tr>
        <td>January</td>
        <td>$100</td>
      </tr>
      <tr>
        <td>Febuary</td>
        <td>$80</td>
      </tr>
    </tbody>
  </table>
```

- colspan

셀을 가로 방향으로 병합

- rowspan

셀을 세로 방향으로 병합


## Form 관련 요소

텍스트를 직접 입력 / 선택 / 클릭 실행하는 액션을 취해 서버에 전달할 때 사용하는 태그. 
서버에 데이터를 전달하는 요소들

```html
<input type="...">
```

text, password, radio, checkbox, file, 등이 있다

- text

아이디 / 이름 / 주소 / 전화번호 등 단순한 텍스트 입력 

`placeholder` 라는 속성을 사용해 미리 화면에 노출할 수 있다. 


- password

```html
  패스워드 : <input type="password">
```
암호와 같이 공개할 수 없는 내용. 값이 화면에 나오지 않는다. 

- radio

```html
  남자: <input type="radio" name="gender" id="m">
  여자: <input type="radio" name="gender" id="fm">
```
라디오 버튼을 만들 때, 버튼은 중복 선택이 불가능하다. 하나의 항목만 선택할 수 있다. 
이름을 동일하게 넣으면 그룹화가 된다. 
- checkbox

```html
  영화감상 <input type="checkbox" name="hobby" id="movie">
  독서 <input type="checkbox" name="hobby" id="book">
  소리지르기 <input type="checkbox" name="hobby" id="shouting">
```
체크 박스 만들 때 사용한다. 중복 선택이 가능하다. `checked` 속성을 해주면 기본값으로 체크된다.
name 을 사용해서 공통된 그룹임을 알려줄 수 있다.

