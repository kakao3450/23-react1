
# 이정욱
## 3_30일
> * props란?<br>
Read-Only, 수정이 불가하고 읽기 전용이다. 즉 값을 변경 할 수 없다는 것을 의미한다. 리액트 문서에는 '모든 리액트 컴포넌트는 그들의 Props에 관해서 pure 함수와 같은 역할을 해야한다'고 명시되어 있다.
> * Component 생성 및 Props의 사용법
>~~~
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
>~~~
> App.js에서 위와 같은 방법으로 배열을 만든 다음 const명의 이름을 example로 정하였다.
>그 후 같은 폴더 내 Example.js라는 파일 생성 후 다음과 같이 코딩을 해준다.
>~~~
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
>~~~
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

