## CSS 기초
#
## CSS (Cascading Style Sheets)
웹 페이지를 꾸미는 역할. 웹 페이지의 스타일링을 담당.
HTML과 같은 마크업 언어가 어떻게 표현되어야 하는지를 지정하기 위해 사용됨.

- 콘텐츠의 배치와 위치 (레이아웃 디자인)
- 텍스트를 강조하거나 밑줄을 치는 등, 최소한의 타이포그래피 (Typography)

CSS를 통해 정보 전달력을 끌어올리고, 컨텐츠의 가독성을 향상시킬 수 있음.

**CSS는 결국 효율적으로 사용자 인터페이스(User Interface, UI)를 구성함으로써 더 나은 사용자 경험(User experience, UX)을 제공하기 위해 사용한다.**
#
![CSS의 문법 구성](https://github.com/Luxahn/TIL/blob/main/img/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-04-27%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.47.03.png)

### 질문
- **위 CSS 예제에서 등장하는 속성은 어떤 것들이 있나요?**

*색상, 글자 크기*
<br><br>

- **텍스트의 가운데 정렬을 하기 위한 속성은 무엇인가요?**
```css
{
text-align: center;
}   
```
<br>

- **글자 색을 바꾸기 위한 속성은 무엇인가요?**

*color*
<br><br>

- **배경 색을 바꾸기 위한 속성은 무엇인가요?**

*background-color*

*✓ background-image -> 배경 이미지
background-repeat -> 배경 이미지 반복 여부
   background-position -> 배경 이미지 위치*
<br><br>

- **background 속성과 background-color 속성은 어떻게 다른가요?**

*backgroud와 background-color 모두 배경 색상을 지정할 수 있지만.
background-color는 색깔만 지정할 수 있는 반면에, 
background는 color 이외의 다른 background 옵션들을 지정해 사용할 수 있다.*

*결론적으로 background 속성은 다양한 background의 속성을 부여할 수 있는 축약 속성이다.
다만 명시성 측면에서 각각의 옵션명을 적어주는 편이 좀 더 코드를 이해하기 쉽다.*
<br><br>

- **em의 의미는 무엇인가요?**   
*상위 요소의 크기에 따라 그 크기의 몇 배인지 정하는 단위.*
<br> ex) 
```css
    font-size: 1.5em;
```
: 글자 크기를 상위 요소 크기의 1.5배로 하겠다는 뜻.

**✓ em과 rem의 차이점**

*em의 경우, 해당 단위가 사용되고 있는 요소의 font-size 속성 값이 기준이 된다.
(Ex. <html>의 font-size 속성 값이 16px이어도 <div> 요소의 font-size 속성 값이 30px이라면 <div>의 font-size 속성 값을 따라간다.)*

*반면, rem의 경우 최상위 요소의 font-size 속성 값이 기준이 된다.
(HTML에서 최상위 요소는 <html>이다. 따라서 rem의 경우, html 요소의 font-size 속성 값이 기준이 된다.
(Ex. <html> font-size 속성 값이 16px이면 <div> 요소의  font-size 속성 값이 30px이라 하여도 <html>의 font-size 속성 값 16px을 따라간다.*

*✓-em은 각 요소 사이에 다른 요소들이 층층이 껴있는 경우 값을 계산하기 어렵기 떄문에*

*되도록 -rem을 우선적으로 쓰기를 권유한다.*

#
## CSS 파일 추가 ##
CSS 파일을 HTML 파일에 연결할 때에는,

(HTML 문서의)
link 태그 안에서 href 속성을 통해 파일을 연결한다.

예시)

```css
<link rel="stylesheet" href="index.css" />
```
*link 태그는 HTML 파일과 다른 파일을 연결하는 목적으로 사용된다.
link 태그의 rel은 연결하고자 하는 파일의 역할이나 특징을 나타낸다.*

*CSS는 Style sheet이므로 **rel** 속성에 **stylesheet**를 추가한다.*

*href 속성에는 파일의 위치를 추가해야 한다.
(파일이 한 폴더 내에 있을 경우 파일 이름만 입력해도 된다.
단, 다른 폴더에 파일이 존재하는 경우, 절대 경로 또는 상대 경로를 입력해 원하는 파일을 찾아 연결할 수 있다.)*

✓ CSS를 별도의 파일로 구분하여 HTML에 적용하는 걸 "외부 스타일 시트"라고 한다.

CSS를 별도의 파일로 분리하지 않고, HTML 태그에 직접 CSS 속성을 추가할 수도 있지만, 이러한 방법은 관심사 분리 측면에서 권장되지 않는다.
<br><br>

* 관심사 분리: 
<br>예를 들어 <br>HTML은 웹페이지의 구조와 내용만 담당하고, CSS는 디자인만 담당하도록 하여 HTML과 CSS의 역할을 분리하는 것.

<br>하지만 가끔은 파일로 굳이 구분하지 않아도 될 만큼 CSS 코드가 많지 않은 경우도 있다.
이 경우, HTML요소에 직접 CSS 스타일을 적용할 수 있는 방법은 2가지가 있다.

- 같은 줄에서 스타일을 적용하는 “인라인 스타일”

- CSS 파일 내에 작성하는 내용을 별도의 파일로 구분하지 않고 style 태그 내에 작성하는 “내부 스타일 시트”

[예시. “인라인 스타일”; HTML 요소에 직접 추가하는 방법]
```css
<nav style="background: #eee; color: blue">...</nav>
```
#
## Selector(선택자) ##
HTML 문서에는 여러 요소(element)가 존재한다.
그 중 특정 요소에만 스타일을 적용하고 싶을 땐

- id
- class

를 사용한다.

✓ **id**는 문서 내에 단 하나의 요소에만 적용할 수 있는 **유일한** 이름

[예시. HTML]
```HTML
<ul id="apple">
    <li class="pc">Mac</li>
     <li class="pc">MacBook</li>

     <li class="phone">iphone 13</li>
     <li class="phone">iphone 13pro</li>
     
</ul>
```

[예시. CSS]
```css
#apple {
    font-size: 20px;
}

.pc{
    color: red;
}
.phone{
    color: blue;
}
```

|id|class|
|--------|---------|
|#으로 선택|.으로 선택|
|한 문서에 단 하나의 요소에만 적용|동일한 값을 갖는 요소 많음
|특정 요소에 이름을 붙이는 데 사용|스타일의 분류에 사용|
#
<br>

- 색상
<br>**color**

- 글꼴
<br>**font-famliy**

- 글자 크기
<br>**font-size**
<br><br>
*알아야 할 몇가지 단위*

- 절대 단위: px, pt 등
- 상대 단위: %, em, rem, ch, vw, vh 등
<br><br>

*기타 스타일링*

- 굵기: font-weight
- 밑줄, 가로줄: text-decoration
- 자간: letter-spacing
- 행간: line-height

#
<br>

## CSS 박스 모델 ##
![CSS 박스 모델](https://github.com/Luxahn/TIL/blob/main/img/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-05-02%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.46.36.png)

각각의 값은 top, right, bottom, left로 시계방향.

[예시]
```css
p {
  margin: 10px 20px 30px 40px;
}
```

- 높이: height
- 너비: width

<br>

**여백과 테두리 두께를 포함한 박스 계산법**

box-sizing 속성을 추가하고,
border-box라는 값을 추가

```css
* {
  box-sizing: border-box;
}
```