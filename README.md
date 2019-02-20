# reactjs_Card

### 2. Card 1 프로젝트에 기능을 추가해보았습니다. 특정 카드를 클릭했을 때 해당 카드에 출력된 value 만큼 별이 출력되고, 별을 클릭했을 때 별의 현재 값을 출력하고 별의 색을 변경하도록 이벤트 처리 기능을 추가하였습니다.
![default](https://user-images.githubusercontent.com/38427658/53087581-d641cf80-354a-11e9-9560-ee81577a89c1.png)

**1) 클릭된 카드 선택하기**
* Card.css
    ```css
    .card {
        cursor: pointer;
    }

    .current {
        background-color: yellow;
    }
    ```
    * Card CSS Class에 cursor (마우스 커서속성) 값을 pointer(손가락) 으로 변경하는 설정을 추가한다.
또한, 선택된 Card에 지정할 current CSS Class 도 추가한다. Current CSS Class는 배경색을 노랑색으로 지정한다.
* Card.js
    ```js
    return <div className={['card', this.props.isCurrent ? 'current' : ''].join(' ')} key={r.id} 
    onClick={this.props.onClick.bind(this, this.props.value.id)}>

    ```
    * Card 컴포넌트를 수정한다. Card 컴포넌트의 Div 에 className 속성에 기존에 있던 card CSS Class 외에 추가로 조건에 따라 current 속성을 배정하기 위해 배열로 변경하였다. This.props.isCurrent 속성은 App 컴포넌트에서 Card 컴포넌트로 true/false 값을 전달해 주는데, 현재 클릭한 Card 일 경우 true 가 전달된다. This.props.isCurrent 값이 true 일 경우, current값이 지정되며 false일 경우 빈값이 지정된다. 이 배열을 join(‘ ‘) 함수를 통해 string 으로 변환해 className에 배정하게 된다.
* App.js
    ```js
        // 클릭시 처리
    handleClick(id) {
        this.setState({ currentId: id });
    }

    render() {

        let list = this.state.list.map(r => {
            return <Card key={r.id} isCurrent={this.state.currentId === r.id} value={r} onClick={this.handleClick.bind(this,r.id)} />;
        })
    }
    ```
    * App 컴포넌트에서는 현재 클릭한 Card의 id 값을 저장할 currentId 값을 state에 추가한다.
Render() 에서 Card 컴포넌트를 사용할 때, onClick 이벤트에 this.handleClick()을 바인딩하게되며, this.handleClick() 메서드에서는 전달받은 r.id 갑을 setState를 호출해 state 의 currentId 에 저장해 놓는다.
Renter() 에서 Card 컴포넌트를 사용할 때 isCurrent props를 추가로 지정해 주는데, 이 값은 state의 currentId 값과 현재 r 값 (state.list 순회값)의 id값과 동일할 경우 true, 다를경우 false를 반환하는데, 이 값은 현재 클릭된 Card 컴포넌트 여부이다. 이 값에 따라 Card 컴포넌트 내부에서 current CSS Class의 배정이 변경된다.


