https://www.w3schools.com/css/css_selectors.asp

**Table of Contents**

- [스타일파일불러오기](#스타일파일불러오기)
- [selectors](#selectors) : 스타일을지정하려는 html element를 선택할때 사용합니다.
  - [기본선택자](#기본선택자) : tagname, id, class이름을 기반으로 element를 선택합니다.
  - [가상클래스선택자](#가상클래스선택자) : element의 상태를 기반으로 element를 선택합니다.
  - [가상element선택자](#가상element선택자) : element의 일부분을 선택하고 스타일을 지정할때 사용합니다.
  - [가상속성선택자](#가상속성선택자) : 속성또는 속성값을 기반으로 요소를 선택합니다.

# 상속과 우선순위

- 상속 : 각엘리먼트들은 상위 엘리먼트의 속성값을 물려받습니다.
  - 상속하는속성과 상속하지않는 속성
  - ttps://www.w3.org/TR/CSS21/propidx.html
- CSS적용의 우선순위
  - style attribute> id selector > class selector > tag selector
- !important -> 무조건적인 우선순위를 부여할수있다.
- ` li{color:red !important;}`

# 스타일파일불러오기

```html
<link rel="stylesheet" href="./style.css>
```

# selectors

more information - click below

- http://flukeout.github.io/
- https://www.w3schools.com/css/css_pseudo_classes.asp

## 기본선택자

| selector          | description                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------- |
| **기본선택자**    |
| \*                | universial selector 모든태그선택                                                                        |
| tagname           | 특정태그를 모두선택                                                                                     |
| .classname        | 특정 클래스이름을가진 태그 모두선택                                                                     |
| tagname.classname | 특정클래스이름을가진 특정태그를 모두선택                                                                |
| #idname           | 특정id값을 가진 태그선택                                                                                |
| **선택자 조합**   |
| A, B              | 모든 A태그와 모든B태그를 선택                                                                           |
| A B               | 후손들 선택 - A의 하위에있는 모든 B태그선택                                                             |
| A>B               | 자식들선택 - A의 한단계 아래위계에 위치한 모든B태그선택                                                 |
| A+B               | 바로다음형제선택 - 만약A태그바로다음위치에(형제위계)B태그가 있다면 선택, 바로다음위치에 없다면 선택안함 |
| A~B               | 형제선택자 - A태그다음에 위치하는 모든 형제위계의 B태그를 선택)                                         |

## 가상클래스선택자

https://www.w3schools.com/css/css_pseudo_classes.asp

- 클래스 선택자는 아니지만, **엘리먼트의 상태에따라서** 마치 클래스선택자처럼 **여러 엘리먼트를 선택**할수 있다는 의미에서 가상클래스선택자라고 한다.
- 예시) div태그의 상태가 hover되면, div태그하위에있는 p태그를 선택하라.

```CSS
div:hover p {
display: block;
}
```

### 자식선택

- `A:first-child` → A의 상태가 첫번째 (자식) 태그인 A태그를 선택한다.
  - :first-child → 다른태그의 내부에 있는 모든 첫번째( 자식)태그를 선택한다
  - p:first-child → P태그의 상태가 첫번째 (자식)태그인 P태그를 선택한다.
  - div p:first-child → div태그의 모든하위의 P태그중에 p태그의 상태가 첫번째 (자식) 태그인 P태그를 선택한다.
- `A:only-child` → A의 상태가 다른 태그의 유일한 자식일때 A태그를 선택한다. - A B, A C:only-child → A태그 하위의 B, C가 유일한 자식태그일때 그 B,C태그를 선택 -` A:last-child` → A태그의 상태가 마지막 (자식) 태그일때 그 A태그를 선택한다. - A:LAST-CHILD → 마지막 자식태그인 모든 A태그를 선택 - ul li:last-child → ul태그로 감싸진 태그중에 제일 마지막에 위치하는 li태그선택

### 몇번째 자식

- `A:nth-child(1)` → 다른 태그안에서 몇번째 (자식) A태그를 선택한다.
  - div p:nth-child(2) → 모든div태그안에있는 2번째 p태그를 선택한다
- `A:nth-last-child(1)` → 다른태그안에서 뒤에서 몇번째 (자식) A태그를 선택한다.
  - :nth-last-child(2) → 다른 태그안에서 뒤에서 2번째 태그를 모두 선택한다.

### 같은 Type의 element 중에서..

- `A:first-of-type` → 순차적으로 찾다가 처음으로 발견하는 a태그를 선택. - span:first-of-type → selects the first span in any element. -` A:nth-of-type(2 or odd or even)` → A태그를 찾다가 몇번째(2번째, 홀수, 짝수)로 나타나는 A태그를 선택. - div:nth-of-type(2)→ selects the second instance of a div. - .example:nth-of-type(odd) →selects all odd instances of a the example class.
- `a:nth-of-type(An+B)` → 함수를 따라가며 나타나는 순서대로 선택되는 a태그를 선택
  - span:nth-of-type(6n+2) → selects every 6th instance of a span, starting from (and including) the second instance.
- `a:only-of-type` → a태그가 오직 유일하게 존재할때 그 a태그를 선택해라.Selects the only element of its type within another element.
  - p span:only-of-type→ selects a span within any p if it is the only span in there.
    p태그안에 span태그가 오직 유일하게존재할때 그 span태그를 선택해라.
- `a:last-of-type ` → 모든 태그속에서 제일 마지막 a태그를 선택하라.
  - div:last-of-type →selects the last div in every element. (모든태그속에서 제일마지막div태그를 선택)
  - p span:last-of-type → selects the last span in every p.

### 기타

- `a:empty` → 안에 아무것도 없는 a태그를 선택해라
- `:not(X)` → X가아닌 태그를 선택

  You can use this to select all elements that do not match selector "X".

  - :not(#fancy) selects all elements that do not have id="fancy". ID값이FANCY가 아닌 모든태그선택
  - div:not(:first-child) selects every div that is not a first child. 다른태그의 첫번째 자식이아닌 모든DIV태그선택
  - :not(.big, .medium) selects all elements that do not have class="big" or class="medium".(클래스네임이 빅, 미디움이 아닌 모든 엘리먼트를 선택)

### 링크관련

- `a:link` -> unvisited 상태의 a링크를 선택
- `a:visited` -> 방문한적이 있는상태의 a링크를 선택
- `a:hover` -> 해당링크위에 마우스가 올라오면 해당 a링크를 선택
- `a:active` -> 해당링크가 active된 상태인 a링크를 선택

### 기타

- `:focus` -> 해당태그가 active되거나 클릭되었을때 해당요소를 선택

## 가상element선택자

https://www.w3schools.com/css/css_pseudo_elements.asp

- `::first-line` -> text의 첫번째줄을 선택합니다.
- `::first-letter` ->text의 첫번째 letter를 선택합니다.

- `::before` -> 선택된elememt의 content앞에 일부내용을 삽입할때 사용합니다.
- `::after` -> 선택된elememt의 content뒤에 일부내용을 삽입할때 사용합니다.

```css
p::before {
  content: url(smiley.gif);
}
h1::after {
  content: "Click Below";
}
```

- `::marker` -> list items의 markers를 선택합니다.

- `::selection` -> 사용자가 마우스로 드래그해서 선택한 부분을 선택합니다. 사용자의 선택영역의 글자색, 배경, 커서, outline등의 css효과를 줄수있습니다.

## 가상속성선택자

- `[ATTRIBUTE]` - 해당속성을 가진 태그를 모두선택

- `element[attribute]` -해당속성을 사용하는 특정태그들을 모두선택
- `element[attribute="xxxx"]` -속성의 값이 XXX인 특정태그를 모두선택

- `[attribute~="xxx"]` - 속성의 값이xxx라는 단어를 포함하는 태그
- `[attribute^="red"]` - 속성의 값이 첫글자가 red로 시작하는 태그선택
- `[attribute$="flower"]` - 속성값이 flower로 끝나는경우 (flowers는 선택안된다)
- `[attribute*="flow"]` - 속성의 값이 flow라는 문자를 포함하는 element선택 ->이경우(flowers, flower모두 선택된다)
