
# 이정욱
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

