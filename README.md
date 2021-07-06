# Movie App

React JS 시작

2-0
React 는 component 단위로 동작함 컴포넌트는 대문자로 시작
컴포넌트 => HTML 을 반환하는 함수
자바스크립트와 HTML 이 결합된 JSX 라는 개념으로 동작
리액트 앱은 한개의 컴포넌트만 렌더링가능 => 모든 것은 App 에 들어가야함

Potato.js 를 만들고 default 로 export 후 App.js 에서 임포트 후 App 안에서 <Potato /> 형식으로 사용가능

2-1
App.js 에 Food 컴포넌트를 만들고 App() 에서 불러옴
컴포넌트를 사용할때 정보를 보낼 수 있는데 해당 값들은 prop(property) 라는 인자로 컴포넌트 function 에 전달
<Food fav="kimchi"> 라는 예시로 컴포넌트에 값을 전달하고
{fav} 를 인자부분에 사용해서 props 안의 fav 를 꺼내고 함수내에서 {fav} 로 사용가능

2-2,3
웹사이트에 동적 데이터를 추가하는 방법
그냥 텍스트를 쓰면 텍스트 {} 안에 쓰면 JS
Object 가 있다면 .map 을 사용해서 사용가능
return 하고 () 으로 HTML 여러줄을 사용가능

2-4 PropTypes 를 이용해서 PropType을 확인 가능
Food 컴포넌트에 Food.propTypes = {} 을 이용해서 Food 컴포넌트의 인자들의 자료형을 지정해주면 다른 자료형이 들어왔을시 확인 가능
이름은 반드시 .propTypes 로 해야 리액트가 확인

3-0 State
2 장에서 App 은 function 컴포넌트
클래스 컴포넌트를 만들어 봄
class App extends React.Component {}
클래스 컴포넌트는 return 하지 않고 render 함!!!!!!!! => render() {} 안에 return 은 가능함
State 는 object 이고 컴포넌트의 데이터를 넣을 공간이고 이 데이터는 변하는 데이터 => 변하는 데이터를 담는게 사용 이유
컴포넌트 안에서 사용하려면 {this.state.이름} 식으로 사용
state 의 데이터를 변화시키기 위해 더하기, 뺴기 함수를 생성하고 onClick 을 사용해서 함수를 불러옴
onClick={this.함수}
