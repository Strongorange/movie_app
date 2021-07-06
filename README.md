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

3-1
state 의 값을 직접 바꾸게되면 오류가나고 작동하지 않음 대신에 setState 를 사용하면 가능함
state 에 있는 값을 업데이트하고 render 를 실행하는데 오직 바뀐 부분만 부분적으로 똑똑하게 업데이트

안녕하세요. 궁금한 점이 잇어서 댓글 남깁니다.
this.setState( current => ({count: current.count -1 })); 에서 왜
this.setState( current => {count: current.count -1 }); 로 작성하면 오류가 날까요?

{count: current.count -1}를 감싸고 있는 () 소괄호의 역할이 무엇인가요?
return을 다음과 같이 써주어도 마찬가지로 오류가 납니다.
this.setState( current => {return count: current.count +1});

()를 쓴다면 () => {} 에서 (current) => 이렇게로 사용해주거나, 아니면 return에서 JSX 문법을 사용할때 여러 line일 경우를 대비해 ()를 사용해주는 것 {return (count: current.count +1)}으로 알고 있었는데... 왜 => 다음에 ()를 사용해주어야 하는 걸까요?

번외로
this.setState( current => {return current.count += 1});
얘는 왜 => () 를 사용해주지 않아도 작동하는 걸까요?

==>>>>

안녕하세요 implicit return과 관련하여 궁금하실 분들을 위해 알고있는 내에서 설명을 덧 붙여봅니다.

화살표 함수를 통해 함수를 나타낸 경우
() => {} 형식을 띄게 되는데요,
뒤의 {} 부분이 return 할 대상으로 표현되는 경우가 많습니다.
만일 return 시에 객체를 반환할 경우(위와같이)
js는 이게 return 을 나타내기위한 {} 인지, 아니면 객체를 나타내기 위한 {} 인지 잘 모르기 때문에 둘을 구분하기 위해
객체를 반환하는 경우 ({}) 를 사용하는 것으로 알고 있고, 번외의 질문에서는 {} 안에 return 키워드가 사용되었으니 ()가 없어도 잘 실행이 되겠지요 :)

3-2 Component Life Cycle
https://reactjs.org/docs/react-component.html

Mounting => 컴포넌트가 태어나는 것
constructor 가 실행되고 render 가 실행되고 componentDidMount 가 실행됨

Updating
render 가 실행되고 componentDidUpdate 가 실행

Unmounting => 페이지를 바꿔서 컴포넌트가 죽을때
componentWillUnmount 를 실행

3-3
Life Cyle 을 이해하고 사용
componentDidMount 는 컴포넌트가 mount 되자마자 호출 됨 => 타이머를 사용해서 6초후에 완료라고 표시
=> 실전에서는 API 에 FETCH 를 보내고 데이터를 가져오면 데이터를 보여줌
