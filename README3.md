**3) 별 클릭 시, 별의 현재 값을 출력하도록 변경**
* Datail.js
    ```js
    render() {
        let r = []
        for (let i = 0; i < this.props.count; i++) {
            r.push(<span key={i} onClick={this.handleClick.bind(this, i)}>☆</span>);
        }
    }
    handleClick(i) {
            alert(i);
        }
    }
    ```
    * Render() 의 출력값을 저장하는 임시 저장변수 r의 배열로 변경한후, props.count 만큼 반복하면서 배열에 span 객체를 추가하도록 변경한다. Span 객체의 key 값은 현재 index(i) 로 지정하며, onClick 이벤트를 추가해 클릭시 이벤트를 처리한다. onClick시 this.handleClick() 메서드를 바인딩하며, 인자로 index(i)를 전달한다. This.handleClick() 메서드는 넘겨받은 I 값을 alert() 로 표시한다.

**<3 결과>**

![image](https://user-images.githubusercontent.com/38427658/53088521-55380780-354d-11e9-93bb-4b5c7385571f.png)

**4) 클릭한 별만큼 검은색 별로 변경**
* Datails.js
```js
constructor(props) {
        super(props);

        this.state = {
            currentIndex: -1,
        };
    }

handleClick(i) {
        this.setState({ currentIndex: i });
}
```
* 현재 클릭한 인덱스를 저장할 state.currentIndex를 추가한다.
handleClick() 메서드는 넘겨받은 index(i) 값을 state.currentIndex 에 저장한다.
Render() 에서 바로 별을 출력하던 부분에서, 현재 출력하는 index(i) 값보다 state.currentIndex(현재클릭한 인덱스) 가 크거나 같은경우 검은 별을, 그렇지 않으면 흰 별을 출력한다.

**<4 결과>**

![image](https://user-images.githubusercontent.com/38427658/53088627-a21bde00-354d-11e9-87e5-cba389107537.png)
