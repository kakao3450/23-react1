
# 이정욱
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

