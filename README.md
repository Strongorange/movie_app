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

2-2,3 Map
웹사이트에 동적 데이터를 추가하는 방법
그냥 텍스트를 쓰면 텍스트 {} 안에 쓰면 JS
Object 가 있다면 .map 을 사용해서 사용가능
return 하고 () 으로 HTML 여러줄을 사용가능
map 에 있는 각각 item 은 key 가 필요

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

4-0 Axios
fetch 보다 나은 방법이 존재 axios 를 사용
axios ==>> fetch 위에 있는 작은 레이어

YTS API 사용
https://yts.mx/api
=> https://yts.mx/api/v2/list_movies.json 에서 MOVIES 리스트 배열을 얻을 수 있음
YTS 는 불법 토렌트 그룹이여서 URL 이 계속 변하는데 NOMAD CODER 의 PROXY 를 사용해서 해결
https://yts-proxy.now.sh/list_movies.json
getMovies async 함수를 만들고 axios 에서 얻어온 데이터를 movies 로 저장

컴포넌트를 불러온 후 render 가 실행되고 DidMount 를 실행해서 데이터를 가져옴

4-1 Rendering Movies
ES6 를 사용해서 movies 를 가져오고 movies 를 state 에 넣을것 => setState
Movie.js 를 만드는데 state 가 필요없어 class 컴포넌트로 만들필요 없음 => function 컴포넌트로 하고 propTypes 사용
App 에서 ?sort_by=rating 사용해서 점수순으로 정렬
render 안에서 state 에 안에있는 movies 를 추가로 선언해두고 movies 에 map 을 사용함 => map 은 반드시 return 이 존재해야!

4-2
홈페이지에 타이틀 요약 년도 포스터가 나오게 만듬
style={{}} 처럼 {{}} 으로 css 사용가능함 근데 별로임!
CSS 파일을 만들어서 가능

4-3 Add Genres
Movie 에 장르 arrayOf(PropTypes.string) 을 추가해줌!

JSX 는 HTML 처럼 보이지만 어쨌든 JS 임 JS 에서 CLASS 는 CLASS APP EXTENDS..... 같은게 CLASS
HTML 의 CLASS 를 지정해줄때는 CLASSNAME 을 사용
Movie.js 컴포넌트에 장르를 추가
map 에 있는 각가 item 은 key 가 필요
map 은 현재의 item 과 item number 를 반환함 해당값을 key 로 보내서 에러 해결

4-5 Cutting the summary
.slice 를 이용해서 설명을 좀 잘라줌

5-0 gh-pages
gh-pages 모듈로 gh-pages 에 업로드, npm i gh-pages
package.json 을 설정
homepage 를 반드시 넣어줘야함!!!
npm run build 를 하면 압축된 build 폴더가 생김
"deploy": "gh-pages -d build" 스크립트를 추가함 // -d 는 directory 의 약자 => build 폴더를 올린다는 뜻
"predeploy": "npm run build" 를 추가하면 npm run deploy 를 하면 predeploy 를 먼저 하고 deploy 함 똑띠

6-0 네비게이션 만들기
react-router-dom 설치
component 폴더에 Movie 들을 routes 폴더에 about 과 home js 를 만듬
react-router-dom 중에서 HashRouter , Route 를 임포트
Route 에는 2가지 props 가 들어감

1. 렌더링할 스크린

2. 뭘할지 정해줌
   <Route path="/about" component={About} /> 내가 /about 으로 가면 About 컴포넌트를 보여줘
   그런데
   <Route path="/about" component={About} />
   <Route path="/home" component={Home} />
   처럼 2개가 있다면 "/" 에서 두 컴포넌트가 동시에 표현되서 화면이 이상해짐

    <Route path="/home">
        <h1>Home</h1>
      </Route>
      <Route path="/home/intro">
        <h1>intro</h1>
      </Route>
    에서 /home/intro 에서는 둘 다 표시됨 => 겹치는 url 을 모두 표시

   요걸 방자하기 위해서 exact={true} 를 해주면 오직 정확히 매치하는 url 에 해당되는 컴포넌트만 불러옴

6-2
Navigation 컴포넌트를 만들고 실행하보면 링크를 누르면 새로고침을 시켜버려 컴포넌트를 죽이고 다시 시작하고 /about 로 이동하지 않음
a, href 대신에 Link 와 to 를 사용
Link 는 Router 안에서만 작동함

HashRouter 이외에도 Brower Router 가 존재하는데 gh-pages 에서 설정하기가 복잡해서 해쉬 라우터 사용

6-3
라우터의 라우트 들은 props 를 가짐 console 로 확인시 history, location, match, static~~ props 를 가지고 이것들을 사용가능
영화를 클릭시 정보를 about 페이지로 보내서 사용가능
https://reactrouter.com/web/api/Link/to-object
to 를 단순 주소가 아닌 객체로도 보낼 수 있음

<Link
  to={{
    pathname: "/courses",
    search: "?sort=name",
    hash: "#the-hash",
    state: { fromDashboard: true }
  }}
/>

네비게이션이 라우트로 정보를 보내고 라우트는 props 인자로 받음
state 에서 fromNavigation:true 로 보낸것이 About 라우트 props.location.state 에서 그대로 확인 가능
Detail 라우트를 만들고 Movie.js 에 Link 를 생성해 클릭하면 /movie-detial 로 이동하고 state에 모든 props 를 같이 보냄
props.location.state 에 모든 정보들이 있고 이것을 사용가능!

6-4
영화를 클릭하지 않고 /movie-detail 을 쳐서 들어가면 state 가 undefined 라고 콘솔에 출력
Detail 을 class 컴포넌트로 바꾸고 componentDidMount() 에서 location.state 를 콘솔하면 정상이나 위와 같은 증상
해서 location.state 가 undefined 면 홈으로 리다이렉트 시킴
props 의 history.push("/") 으로 가능!

render() 가 실행되고 componentDidMount() 가 실행되기때문에 render() 에서 location 이 없는 경우에 오류발생

location, history 같은 props 를 사용가능한 것은 Route component 이기 때문!
<Navigation />
<Route path="/" exact={true} component={Home} />
<Route path="/about" exact={true} component={About} />
<Route path="/movie-detail" exact={true} component={Detail} />

Navigation 은 Route 가 아니라 history, location 같은 props 가 없음

clonetube 에서 한 것 같이 /movie/:id 로 넣고 pathname 에서 id 를 넣어주면 변수로도 가능
