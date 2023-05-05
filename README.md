
# 이정욱
## 5_4일
* ### 리스트와 키의 개념
1. 리스트는 자바스크립트의 변수나 객체를 하나의 변수로 묶어 놓은 배열과 같다.
2. 키는 각 객체나 아이템을 구분할 수 있는 고유한 값을 의미
3. 리액트에서 배열과 키를 사용하는 반복되는 다수의 엘리멘트를 쉽게 렌더링 가능 -> map함수에 대한 내용
~~~jsx
const doubled = numbers.map((number)=>number *2)
// numbers 배열에 있는 각각의 요소를 map()를 이용해 하나씩 추출, 2를 곱한 후 doubled라는 배열에 다시 넣음
~~~
json 스타일로는 다음과 같이 배열 사용 가능
~~~jsx
  [
    {
        key:1,
        id : foo,
        pass :123,
    },
     {
        key:2,
        id : foo2,
        pass :1234,
    }
]
~~~
* 기본적인 리스트 컴포넌트
~~~jsx
funtion NumberList(props){
    const {number} = props;

    const listItems = number.map((number)=>
    <li>{number}</li>
    );

    return (
        <ul>{listItems}</ul>
    );
}

const numbers =[1,2,3,4,5];

ReactDom.render(
    <ul>document.getEmentById('root')</ul>
);
~~~
위와 같은 코드를 실행하면 "리스트 아이템에 무조건 키가 있어야 한다"는 경고 문고가 나옴<br>

이유? -> 각각의 아이템에 key props가 없기 때문

* ### 리스트의 키란?
 1. 리스트에서 키는 "리스트에서 아이템을 구분하기 위한 고유한 문자열"이다.
 2. 리액트에서 키의 값은 같은 리스트에 있는 엘리먼트 사이에서만 고유한 값이면 된다.
* ### 제어 컴포넌트
HTML 폼에서는 자체적으로 state를 관리 하지만
제어 컴포넌트에서는 모든 데이터를 state에서 관리한다.<br>

HTML 폼을 리액트의 제어 컴포넌트로 만들어보겠다.
~~~jsx
function NameForm(props) {
    const [value, setVaule] = useState('');

    const handleChange = (event) => {
        setValue(event.target.value);
    }

    const handleSubmit = (event) => {
        alert('입력한 이름: ' + value);
        event.preventDefault();
    }

    return(
        <form onSubmit={handleSumbit}>
            <label>
            이름:
            <input type="text" value={value} onChange={handleChange}>
            </label>
            <button type="submit"/>제출</button>
        </form>
    );//value={value} 리액트 컴포넌트의 state에서 값을 넣어줌
    //onChange={handleChange} handleChange함수에서 setVaule() 함수를 사용해서 새롭게 변경된 값을 value라는 이름의 state에 저장
}
~~~
### select태그
HTML과 마찬가지로 사용되며 리액트에서는 이벤트 핸들러를 사용때 onChange를 사용하여 함수를 불러와 이벤트 발생시 시작되는 조건을 실행 할 수 있다.
~~~jsx
        <select value={gender} onChange={test}>
          <option value="남자">남자</option> 
          <option value="여자">여자</option>
        </select>
        // onChange={test} 폼 요소의 값이 변경될 때 실행되는 함수를 지정
~~~  
### Input Null Value
value prop에 정해진 값을 넣으면 코드를 수정하지 않는 한 입력값을 바꿀 수 없지만, 자유롭게 입력할 수 있게 만들고 싶으면 null을 넣어주면 된다.
~~~jsx
//예제
setTimeout(funtion() {
    ReactDOM.render(<input value={null}>, rootNode);
}, 1000);
~~~      

## 4_27일
>* ### 이벤트 처리하기
>   react에서 클릭 이벤트를 처리하는 예제코드는 다음과 같다
>~~~ jsx
>   <button onClick={activate}>
>       Activate
>   </button>
>~~~
>   리액트에서 이벤트 이름은 onClick(Camel case)로 사용함<br>
>   위의 이벤트 헨들러에서 ativate를 실행 할려며녀 activate의 컴포넌트를 만들어 실행해야 한다. activate컴포넌트는 화살표 함수로 만들 수 있고 다음과 같은 예제를 볼 수 있다.
>~~~jsx
>function test(props){
> const [isToggleon, setToggleon] = useState(true);
> const ativiate = () => {
> setToggleon((isToggleon)=>!isToggleon);    
>}
>return(
>   <button onClick={activate}>
>       Activate
>   </button>    
>)}
>~~~
>* ### 조건부 렌더링
>   조건부 랜더링이란 조건에 따른 렌더링이 달라지는 것을 의미한다.<br>
if문, 삼항연산자, 논리 연산자등을 이용하여 다양하게 사용가능.
>  if문을 이용한 코드로 예제를 만들어 공부해 보겠다.
>~~~jsx
>function test() {
>  const istrue = true;
>
>  if (istrue) {
>    return <div>참입니다.</div>;
>  }
>
>  return <div>거짓입니다.</div>;
>}
>~~~
>* ### 컴포넌트 렌더링 막기
>   조건부 렌더링을 이용하여 결과값에 null을 리턴하면 리액트 내에서 렌더링 되지 않는다. 다음과 같은 예제코드를 통해 이해할 수 있다.
>~~~jsx
> fuction ShowWarning(props){
>   if(!props.warning){
>   return null;    
>}  
>   return(
>  <div>경고</div>    
>);  
>}
>~~~
>  위에서 ShowWarning라고 작성한 컴포넌트는 props.warning의 값이 false이면 null를 리턴한다. 조건부 렌더링에서 삼항연산자를 이용하여 컴포넌트를 만들고 이를 이용하여 컴포넌트 렌더링도 막는 코드를 작성해 보겠다.
>~~~jsx
>function test(props){
>    const [warningBanner,setwarningBanner] = useState(false);
>
>   const handleToggleClick = ()=>{
>      setwarningBanner(preShowWarning => !preShowWarning);
>    }
>
>    return(
>        <div>
>            <ShowWarning warning={warningBanner}/>
>            <button onClick={handleToggleClick}>
>                {warningBanner ? '감추기':'보이기'}
>            <button>
>        </div>
>    );
>}
>~~~
## 4_13일
> * ### Hook이란?
>    리액트 state의생명주기 기능에 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만든 기능. 훅의 이름은 모두 'use'를 앞에 붙임
> * ### useState 설명 및 사용법
>   가장 대표적이고 많이 사용되는 훅은 'useState'이다. 사용법은 아래와 같다.
>     ~~~jsx
>     const [변수명,set함수명] = useState(초깃값);
>     ~~~
>      초깃값을 넣어주면 useState를 호출할 때 리턴 값으로 배열이 나옴
> * ### useEffect 설명 및 사용법
>   이 함수는 '사이드 이펙트'를 수행하기 위해 사용
>   ~~~jsx
>   useEffect(이팩트 함수, 의존성 배열);
>   ~~~
>   의존성 배열은 이펙트가 의존하고 있는 배열로, **배열안에 있는 변수중에 하나라도 값이 변경되었을 때 이펙트 함수**가 실행됨<br><br>
>   의존성 배열을 생락하는 경우 업데이트 될 때마다 호출
>   ~~~jsx
>   useEffect(()=>{
>   // 컴포넌트가 마운드 된 이후 
>   // 의존성 배열에 있는변수들 중 하나라도 값이 변경되었을 때 실행됨
>   // 의존성 배열에 빈배열([])을 넣으면 마운트와 언마운트시에 단 한번 씩만 실행됨
>   // 의존성 배열 생략 시 컴포넌트 업데이트 시마다 실행
>   ...
>   return ()=> {
>   // 컴포넌트가 마운트 해제되기 전에 실행
>   }
>   },[의존성 변수1,의전성 변수2, ...]);
>   ~~~
> * ### useMemo
>   이전 계산값을 갖고 있음으로 연산량이 많은 작업의 반복을 피하기 위해 사용<br><br>
>   **랜더링이 일어나는 동안 실행돼서는 안될 작업을 넣으면 안됨**
>   ~~~jsx
>   const meoizedValue = useMemo(
>   () => {
>   // 연산량이 높은 작업을 수행하여 결과를 반환    
>   return computeXpensiveValue(의존성변수1, 의존성변수2);
>   },
>   [의존성변수1, 의존성변수2]
>   );
>* ### useCallback
>   useMemo와 비슷한 역할을 함. 차이점은 **값이 아닌 함수를 반환**
>* ### useRef
>   레퍼런스를 사용하기 위한 훅
>   레퍼런스 객체에는 .current라는 속성이 있음. 현재 레퍼런스(참조) 하고있는 엘리먼트 의미
>   ~~~jsx
>   const refContainer = useRef(초깃값);
>   ~~~
>* ### Hook의 규칙
>   1. 훅은 무조건 최상의 레벨에서만 호출 가능
>   2. 반복문이나 조건문, 중첩된 함수들 안에서 훅을 호출 불가
>   3. 컴포넌트가 렌더링 될 때 마다 매번 같은 순서로 호출되어야 함

## 4_6일
>* ### 컴포넌트 추출<br>
>   컴포넌트 추출을 왜 하는 것 일까? -> 재사용을 높히기 위해 사용
    자주 쓰이는 컴포넌트를 작은 단위로 생성을 하면 필요할 때 가져와 사용이 가능하기떄문에 효율성이 좋아진다.
>* ### State<br>   
>   state는 '리액트 컴포넌트의 상태'를 의미 
<br> state를 정의할 때 랜더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야한다.
> * ### state의 가장 최신 값 사용
>   setState를 사용하여 여러 업테이트 사항에 충돌없이 사용 가능하게 처리
> * state 사용예제 
>~~~jsx
>incrementCount() {
>  this.setState((state) => {
>    // 중요: 값을 업데이트할 때 `this.state` >대신 `state` 값을 읽어옵니다.
>    return {count: state.count + 1}
>  });
>}
>
>handleSomething() {
>  // `this.state.count`가 0에서 시작한다고 >해봅시다.
>  this.incrementCount();
>  this.incrementCount();
>  this.incrementCount();
>
>  // 지금 `this.state.count` 값을 읽어 보면 >이 값은 여전히 0일 것입니다.
>  // 하지만 React가 컴포넌트를 리렌더링하게 >되면 이 값은 3이 됩니다.
>}
>~~~
> * ### 리액트 컴포넌트의 생명주기<br>
> 1. 마운트 (Mounting)
> * constructor() : 컴포넌트 생성 및 초기화
> * static getDerivedStateFromProps() : props로부터 상태 업데이트
> * render() : UI 렌더링
> * componentDidMount() : 컴포넌트가 마운트된 후 실행되는 메소드
> 2. 업데이트 (Updating)
> * static getDerivedStateFromProps() : props로부터 상태 업데이트
> * shouldComponentUpdate() : 컴포넌트 업데이트를 결정하는 메소드
> * render() : UI 렌더링
> * getSnapshotBeforeUpdate() : 변경 전 DOM 상태 저장
> * componentDidUpdate() : 컴포넌트 업데이트 후 실행되는 메소드
> 3. 언마운트 (Unmounting)
> * componentWillUnmount() : 컴포넌트가 마운트 해제되기 전 실행되는 메소드
> 4. 오류 처리 (Error Handling)
> * static getDerivedStateFromError() : 자식 컴포넌트에서 오류 발생 시 상태 업데이트
> * componentDidCatch() : 자식 컴포넌트에서 오류 발생 시 오류 처리








## 3_30일
> * props란?<br>
Read-Only, 수정이 불가하고 읽기 전용이다. 즉 값을 변경 할 수 없다는 것을 의미한다. 리액트 문서에는 '모든 리액트 컴포넌트는 그들의 Props에 관해서 pure 함수와 같은 역할을 해야한다'고 명시되어 있다.
> * Component 생성 및 Props의 사용법
>```jsx
> const App = () ={
> const example = [
>     {
>      id: "id1",
>      title: "title1",
>    },
>    { id: "id2", 
>      title: "title2", 
>    },
>];
>}
>```
> App.js에서 위와 같은 방법으로 배열을 만든 다음 const명의 이름을 example로 정하였다.
>그 후 같은 폴더 내 Example.js라는 파일 생성 후 다음과 같이 코딩을 해준다.
>~~~jsx
>const example = (props) => {
>  return(
> <div 
>id = {props.items[0].id} 
>title = {props.items[0].title}>
></div>
> <div 
>id = {props.items[1].id} 
>title = {props.items[1].title}>
></div>
>  )
>}
>~~~
> 위와 같이 작성을 하게되면 앞에 만들었던 example이라는 배열 안의 items 인덱스 0번의 값은 id와 title, 그 다음 div에서 인덱스 값 1번의 id와 title의 값이 호출이된다. 앞의 App.js로 돌아와서 
>~~~jsx
> import Example from "./Exaple"
> ...   return (
>    <div>
>      <h2>props를 이용하여 값 호출</h2>
>      <div items={example}></div>
>    </div>
>  );
>}
>~~~
>Example에서 지정한 items란 변수를 이용하여 App.js에 선언하고 위에 만든 example 배열로 {}를 사용하여 지정하면 example내 id와 title의 값을 사용 할 수 있다. 이와 같이 컴포넌트를 만든 후 props를 통해 값을 불러올 수 있다.
## 3_23일
> * JSX란? <br>
자바스크립트의 확장 문법이며 JavaScript와 XML/HTML를 합친 형태임<br>  
 > * JSX의 역활 <br> JSX를 사용하면 코드를 좀 더 직관적이고 길이를 짧게 줄일 수 있다 . JSX 코드를 자바스크립트 코드로 변환하는 역활을 하는 것은 리액트에서 creatElement() 라는 함수가 있지만 이것 을 사용하게 되면
 > ~~~ 
 >React.createElement(
 > type,
 > [props],
 > [...children]
 >)
 >~~~
 > 위와 같이 작성이 되고 
 >~~~
 ><h1 id="greeting">Hello, world!</h1>
 >~~~
 >다음과 같은 예제를 작성할 때 JSX를 쓰게되면 
 >~~~
 >const element = <h1 id="greeting">Hello, world!</h1> //JSX
 >~~~
 >~~~
 >React.createElement("h1", { id: "greeting" }, "Hello, world!") //JSX 사용x
 >~~~
 > 다음과 같이 이용이 된다. JSX를 사용하는 것이 코드의 생산성과 가독성이 올라가기 떄문에 React를 공부할 때 JSX를 자주 사용하는 코딩 습관을 기르는게 중요하다.

## 3_16일
>DOM의 상태를 메모리에 저장하고, 변경 전과 변경 후의 상태를 비교한 뒤
최소한의 내용만 반영 하는 기능 → 성능 향상

>가상 DOM은 DOM의 상태를 메모리 위에 계속 올려두고,
DOM에 변경이 있을 경우 해당 변경을 반영함

> creat-react-app [폴더이름] ->리액트 폴더 생성
새로운 폴더를 만드는 것이기 때문에 따로 폴더를 만들고 안에 만들 필요없다. (*파일을 중복해서 만듦을 방지*)

>cd  [폴더이름] /  npm start를 터미널창에 입력하면 리액트 어플리케이션 시작

## 3_9일 React 수업
1. git을 이용하여 github에 자신이 작성한코드를 올림
2. commit을 할 시 stage에 올린 후 동사 원형(명령문)으로 수정된 내용 작성 후 저장
=======
1. git을 이용하여 github에 자신이 작성한 코드를 올림
2. commit을 할 시 stage에 올린 후 동사 원형(명령문)으로 수정된 내용 작성 후 저장
3. test
=======
3_9일 React 수업
===============
1. git을 이용하여 github에 자신이 작성한 코드를 올림
2. commit을 할 시 stage에 올린 후 동사 원형(명령문)으로 수정된 내용 작성 후 저장
3. test

