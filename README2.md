**2) 현재 선택한 항목의 value 값 만큼 세부 내용을 출력하는 컴포넌트 출력**
* Detail.js
    * props 로 전달된 count 값 만큼 반복하며 별 문자를 출력하는 Details 컴포넌트를 생성한다.

* Card.css
    ```css
    .card .details {
    word-wrap: break-word;
    font-size: 0.8em;
    }
    ```
    * Card CSS Class의 하위 속성으로 details CSS Class 를 선언한다.
Word-wrap 속성을 지정해 글자가 div범위를 벗어나 깨지지 않고 줄바꿈 되도록 설정하고 글씨 크기를 적절히 조정한다.

* Card.js
    ```js
    let details = this.props.isCurrent ? <Details count={r.v}></Details> : '';
    ```
    * Card 컴포넌트에서 Details 컴포넌트를 import 한다.
Render() 에서 Details 컴포넌트를 배정할 details 변수를 선언해 this.props.isCurrent(현재 클릭여부) 에 따라 Details 컴포넌트를 사용할지, 현재 클릭이 된 것이 아니라면 빈 값을 출력할지 설정한다.
이 Details 컴포넌트의 count props 에는 r.v(랜덤값) 을 넘겨준다.
그리고 만들어진 details 변수를 { details } 를 통해 출력한다.
이렇게 되면, 현재 클릭된 (props.isCurrent === true) 인 경우에만 details 컴포넌트를 사용하게 된다.

**<2 결과>**

![image](https://user-images.githubusercontent.com/38427658/53088324-b9a69700-354c-11e9-8f59-1ae662937bc4.png)
