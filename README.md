# 1.0 INTRODUCTION

## 1.1 무료 강의

2015년에는 React생태계가 매우 작았습니다. 그 때는 Angular, Backbone, MeteorJS, EmberJS가 더 인기가 많았습니다.

2021년 현재 React는 최고입니다.

## 1.2 Why React

개발자에게 중요한 것은 시간입니다. 기술은 생겨나고 사라집니다. 어떤 기술이 배우는데 1년 걸리지만 2년 뒤에 사라진다면 효율이 좋지 않습니다. ReactJS는 여전히 좋고 최고의 선택입니다.

[trends.builtwith.com](http://trends.builtwith.com)

기술을 선택할 때 고려해야할 요소는 아래와 같습니다.

1. 누가 사용하는지, 규모가 큰지, 그들에게 얼마나 중요한지입니다.
2. ReactJS는 페이스북이 개발합니다.
3. 커뮤니티 규모입니다. 생태계 크기입니다.

## 1.3 Requirements

JavaScript 알고 강의 들으셔야 합니다.

# 2. THE BASICS OF REACT

## 2.0 Introduction

기술이 왜 생겼는지 이해하고 시작해야 합니다. JavaScript와 ReactJS를 비교해볼겁니다. ReactJS를 팔아보겠습니다. ReactJS는 UI를 Interactive하게 만듭니다. 매우 쉽게 말이죠!

```jsx
button = document.getElementById("btn")
button = document.querySelector(".btn")
button.addEventListener("onclick", () => console.log("hi"))
```

ReactJS를 만든 사람들은 버튼을 만들고 이벤트를 등록하는 과정을 줄였습니다. ReactJS는 오직 Interactive를 위한 것입니다.

## 2.1 Before React

ReactJS를 사용하기 위해서는 아래 Script를 불러와야 합니다.

```html
<!DOCTYPE html>
<html>

<body>
    <script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
</body>

</html>
```
## 2.2 Our First React Element

우선 ReactJS로 어렵게 Counter를 만들어 봅시다. 우선 어렵게 사용하면서 ReactJS의 본질을 이해해봅시다.

react-dom은 모든 React element을 HTML안에 넣을 수 있게 해주는 라이브러리입니다.

VanillaJS는 HTML을 만들고, 선택한 뒤, 함수를 만들고, 이벤트를 등록합니다. 반면 ReactJS는 JavaScript에서 시작해서 HTML이 만들어집니다.

## 2.3 Events in React

ReactJS 팀은 Interactive한 웹페이지는 모두 event를 감지하는 일이라는 것을 알았습니다.

ReactJS에서 on + event는 addEventListener로 알아서 적용해줍니다.

## 2.4 Recap

```jsx
React.createElement()
ReactDOM.render(root, container)
```

## 2.5 JSX

ReactJS에서 제시하는 새로운 문법입니다. 다만 JSX를 ReactJS로 변환하려면 Babel이 필요합니다.

```jsx
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
  <script type="text/babel">
    const root = document.getElementById("root");
    const Title = (
      <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
        Hello I'm a title
      </h3>
    );
    const Button = (
      <button
        style={{ backgroundColor: "tomato" }}
        onClick={() => console.log("im clicked")}
      >
        Click me
      </button>
    );

    const container = React.createElement("div", null, [Title, Button]);
    ReactDOM.render(container, root);
  </script>
</html>

```

## 2.6 JSX part Two

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="root"></div>
  </body>
  <script type="text/babel">
    const root = document.getElementById("root");
    const Title = () => (
      <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
        Hello I'm a title
      </h3>
    );
    const Button = () => (
      <button
        style={{ backgroundColor: "tomato" }}
        onClick={() => console.log("im clicked")}
      >
        Click me
      </button>
    );

    const container = (
      <div>
        <Title />
        <Button />
      </div>
    );
    ReactDOM.render(container, root);
  </script>
</html>

```

주의해야 할 점은 React Element는 Uppercase로 작성해야 합니다. lowercase로 작성하면 Bable이 HTML element라고 이해합니다.

```jsx
<button /> /* HTML */
<Button /> /* JSX */
```

# 3. STATE

## 3.0 Understanding State

VanillaJS와 다르게, ReactJS는 필요한 것만 Rerendering합니다.

## 3.1 setState part One

전에 봤듯이 처음에 Rendering하고 Rerendering하는 작업이 반복됩니다. 

Rendering부분과 Data를 다루는 부분을 분리합니다.

```jsx
const data = React.useState();
```

useState()는 Element가 2개인 Array를 Return합니다.

```jsx
console.log(data) // [undefined, ƒ]
```

JavaScript 문법인 destructurize을 이용하면 더 세련되게 초기값을 가져올 수 있습니다.

```jsx
const root = document.getElementById("root");

function App() {
  const [counter, modifier] = React.useState(0);
  return (
    <div>
      <h3>Total clicks: {counter}</h3>
      <button>Click me</button>
    </div>
  );
}
ReactDOM.render(<App />, root);
```

## 3.2 setState part Two

modifier를 어떻게 사용하는지 봅시다.

```jsx
const root = document.getElementById("root");

function App() {
  let [counter, modifier] = React.useState(0);
  const onClick = () => {
    counter = counter + 1;
  };
  return (
    <div>
      <h3>Total clicks: {counter}</h3>
      <button onClick={onClick}>Click me</button>
    </div>
  );
}
ReactDOM.render(<App />, root);
```

```jsx
const onClick = () => {
  counter = counter + 1;
};

const onClick = () => {
  modifier(counter + 1);
};
```

## 3.3 Recap

HTML Element 생성 → JavaScript로 Element 선택 → addEventListener()로 등록 → Rerendering의 과정을 ReactJS는 더 간편하게 만들어줍니다.

## 3.4 State Function

modifier로 state를 수정할 때는 두 가지 경우가 있을겁니다.

1. 특정 값으로 수정
2. 이전 값을 기준으로 수정

이전 값을 수정할 때 아래와 같이 하는 것이 더 안전하다고 합니다.

```jsx
const onClick = () => {
  // setCounter(counter + 1);
  setCounter((current) => current + 1);
};
```

## 3.5 Inputs and State

```jsx
function App() {
  return (
    <div>
      <h1>Super Converter</h1>
      <label for="minutes">Minutes</label>
      <input id="minutes" placeholder="Minutes" type="number" />
      <label for="hours">Hours</label>
      <input id="hours" placeholder="Hours" type="number" />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

위 코드에서 문제점은, HTML의 label element는 for attributes가 있지만, JavaScript는 for를 keyword로 사용하고 있기 때문에 문제가 발생할 여지가 충분히 있습니다. import하는 package를 development로 변경하면 Browser console에서 Error를 확인할 수 있습니다.

```html
<script src="https://unpkg.com/react@17.0.2/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.development.js"></script>
```

JSX에서는 살짝 다르게 사용해야 합니다.

- for - htmlFor
- class - className

onChange attribute는 변화가 일어날 때 이벤트 입니다.

```jsx
function App() {
  const [minutes, setMinutes] = React.useState();
  const onChange = (event) => {
    setMinutes(event.target.value);
  };
  return (
    <div>
      <h1 className="hi">Super Converter</h1>
      <label htmlFor="minutes">Minutes</label>
      <input
        value={minutes}
        id="minutes"
        placeholder="Minutes"
        type="number"
        onChange={onChange}
      />
      <h4>You want to convert {minutes}</h4>
      <label htmlFor="hours">Hours</label>
      <input id="hours" placeholder="Hours" type="number" />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

## 3.6 State Practice part One

minutes에 입력할 때마다 hours에 표시되도록 바꾸어봅시다. 그리고 Reset도 만들어봅시다.

## 3.7 State Practice part Two

- flip
- disabled
- ternary operator

```jsx
function App() {
  const [amount, setAmount] = React.useState(0);
  const [flipped, setFlipped] = React.useState(false);
  const onChange = () => {
    setAmount(event.target.value);
  };
  const reset = () => {
    setAmount(0);
  };
  const onFlip = () => {
    setFlipped((current) => !current);
    reset();
  };
  return (
    <div>
      <h1 className="hi">Super Converter</h1>
      <div>
        <label htmlFor="minutes">Minutes</label>
        <input
          value={flipped ? amount * 60 : amount}
          id="minutes"
          placeholder="Minutes"
          type="number"
          onChange={onChange}
          disabled={flipped}
        />
      </div>
      <div>
        <label htmlFor="hours">Hours</label>
        <input
          value={flipped ? amount : Math.round(amount / 60)}
          id="hours"
          placeholder="Hours"
          type="number"
          onChange={onChange}
          disabled={!flipped}
        />
      </div>
      <button onClick={reset}>Reset</button>
      <button onClick={onFlip}>Flip</button>
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

## 3.8 Recap

## 3.9 Final Practice and Recap

- Add KM to Miles
- <hr />

# 4. PROPS

## 4.0 Props (15:24)

프로그램이 커지면 자연스럽게 React Component는 계층을 가지게 됩니다. Parents Component의 데이터를 Child Component에 보내는 방법은 props를 사용하는 것입니다.

회사에서 제품을 만들 땐 버튼 모양이 모두 같습니다. 따라서 Component를 재사용 해야 합니다. 그러나 아직 React Component를 재사용하는 법을 배우지 않았으니, 아는 대로 만들어봅시다.

```jsx
function SaveBtn() {
  return (
    <button
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
      }}
    >
      Save Changes
    </button>
  );
}
function ConfirmBtn() {
  return (
    <button
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
      }}
    >
      Confirm
    </button>
  );
}
function App() {
  return (
    <div>
      <SaveBtn />
      <ConfirmBtn />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

위 코드는 중복이면서 못생기지 않았나요?

props는 OOP의 Class에서 Constructor parameter와 비슷합니다. 이게 무슨말이냐? OOP에서는 Class를 정의하고 Instance를 생성할 때, Argument를 전달하기도 합니다.

```jsx
function Btn(props) {
  return (
    <button
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
      }}
    >
      {props.banana}
    </button>
  );
}
function App() {
  return (
    <div>
      <Btn banana="Save Changes" />
      <Btn banana="Confirm" />
    </div>
  );
}
```

JavaScript Destructuring을 주로 이용하고 props는 사용하지 않습니다.

```
function Btn({ banana, big }) {
  return (
    <button
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
        fontSize: big ? 18 : 16,
      }}
    >
      {banana}
    </button>
  );
}
function App() {
  return (
    <div>
      <Btn banana="Save Changes" big={true} />
      <Btn banana="Confirm" big={false} />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

## 4.1 Memo (12:33)

State가 변하면 Component가 Rerendering됩니다. 그런데 단점은 State를 Props로 전달할 때, 전달받는 Component 모두 Rerendering되는게 문제입니다. 

```jsx
function Btn({ text, onClick }) {
  console.log(`${text} rendered`);
  return (
    <button
      onClick={onClick}
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
      }}
    >
      {text}
    </button>
  );
}
function App() {
  const [value, setValue] = React.useState("Save Changes");
  const changeValue = () => setValue("Revert Changes");
  return (
    <div>
      <Btn text={value} onClick={changeValue} />
      <Btn text="Confirm" />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

Props가 바뀐 Component만 Rerendering을 하고 싶다면, React.memo()를 사용하면 됩니다. memorize의 줄임말입니다.

```jsx
function Btn({ text, onClick }) {
  console.log(`${text} rendered`);
  return (
    <button
      onClick={onClick}
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
      }}
    >
      {text}
    </button>
  );
}
const MemorizedBtn = React.memo(Btn);
function App() {
  const [value, setValue] = React.useState("Save Changes");
  const changeValue = () => setValue("Revert Changes");
  return (
    <div>
      <MemorizedBtn text={value} onClick={changeValue} />
      <MemorizedBtn text="Confirm" />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

꼭 사용할 필요는 없지만, Component가 1000개라면 사용할 법 합니다. 그리고 React의 동작 과정을 더 이해할 수 있는 기능입니다.

## 4.2 Prop Types (08:14)

팀원이 Props를 잘못 전달하면 어떻게 하죠? 이를 위해 React팀에서 prop-types란 것을 만들었습니다. 

```jsx
function Btn({ text, fontSize = 12 }) {
  console.log(`${text} rendered`);
  return (
    <button
      style={{
        backgroundColor: "tomato",
        color: "white",
        padding: "10px 20px",
        border: 0,
        borderRadius: 10,
        fontSize,
      }}
    >
      {text}
    </button>
  );
}
Btn.propTypes = {
  text: PropTypes.string.isRequired,
  fontSize: PropTypes.number,
};
function App() {
  const [value, setValue] = React.useState("Save Changes");
  const changeValue = () => setValue("Revert Changes");
  return (
    <div>
      <Btn text={value} fontSize={18} />
      <Btn text="Confirm" />
    </div>
  );
}
const root = document.getElementById("root");
ReactDOM.render(<App />, root);
```

```jsx
Btn.propTypes = {
  text: PropTypes.string.isRequired,
  fontSize: PropTypes.number,
};
```

더 자세한 내용은 아래 링크를 참고하시면 됩니다.

https://legacy.reactjs.org/docs/typechecking-with-proptypes.html

# 5. CREATE REACT APP

## 5.0 Introduction

ReactJS팀은 React App을 빠르게 만들기 위한 패키지도 개발했습니다. Create React App이란 패키지는 CRA라고도 불리는데, https://www.github.com/facebook/create-react-app에서 확인할 수 있고 아래 명령으로 시작할 수 있습니다.

```bash
npx create-react-app react-for-beginners
cd react-for-beginners
npm start
```

CRA의 장점 중 하나는, 수정이 실시간으로 반영된다는 것입니다.

## 5.1 Tour of CRA

CRA의 장점 2: 개발하면서 발생하는 Warning도 알려줍니다. CRA Server는 저장할 때마다 App을 새로 Compile하기 때문입니다.

CRA로 장점 3: 작업하면 VSCode와 궁합이 좋다는 것입니다.

CRA의 장점 4: 분할하고 정복하기 쉽습니다. CSS를 적용할 때, 한 파일을 index.js에 import하면 전역적으로 적용되지만 그렇게 되면 CSS 파일이 엄청나게 커져버릴 수 있다는 단점이 있습니다. 그래서 Component마다 CSS를 적용하는 것이 선호됩니다. 그렇게 되면 CSS는 HTML의 style Attribute로 적용됩니다.

CRA의 장점 5: CRA는 CSS Modules를 지원합니다. 위 분할 정복에 이어서 아래처럼 CSS를 적용할 수 있습니다.

```css
.btn {
    color: white;
    background-color: tomato;
}
```

```jsx
import PropTypes from "prop-types";
import styles from "./Button.module.css";

function Button({ text }) {
  return <button className={styles.btn}>{text}</button>;
}

Button.propTypes = {
  text: PropTypes.string.isRequired,
};

export default Button;

```

주의할 점은 파일 이름이 abc.module.css와 같이 .module.css이여야 합니다.

# 6 EFFECTS

## 6.0 Introduction

button을 클릭할 때마다 해당 component는 계속 rerendering합니다. 만약… 첫 rendering때만 실행하고 싶은 코드가 있다면? 만약 API호출을 rerendering할 때마다 한다면? 오우 끔찍합니다.

```jsx
import { useState } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const onClick = () => setValue((prev) => prev + 1);
  console.log("call an api");
  return (
    <div>
      <h1>{counter}</h1>
      <button onClick={onClick}>Click me</button>
    </div>
  );
}

export default App;

```

## 6.1 useEffect

`useEffect()`의 존재로 인해서 첫 렌더링때만 실행할 수 있는 코드를 작성할 수 있게 되었습니다.

`console.log()`가 2번 출력되는 이유는 개발모드여서 그렇습니다. production일 경우 두 번 안나옵니다.

```jsx
import { useState, useEffect } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const onClick = () => setValue((prev) => prev + 1);
  console.log("i run all the time");
  const iRunOnlyOnce = () => {
    console.log("i run only once");
  };
  useEffect(iRunOnlyOnce, []);
  return (
    <div>
      <h1>{counter}</h1>
      <button onClick={onClick}>Click me</button>
    </div>
  );
}

export default App;

```

## 6.2 Deps

아래처럼 조건문을 추가할 수도 있습니다.

```jsx
const [counter, setValue] = useState(0);
const [keyword, setKeyword] = useState("");

useEffect(() => {
  if (keyword !== "" && keyword.length > 5) {
    console.log("SEARCH FOR", keyword);
  }
}, [keyword]);
```

혹은, counter, keyword 둘 중 아무거나 변화해도 실행되게 할 수도 있습니다.

```jsx
useEffect(() => {
  console.log("I run only once");
}, []);
useEffect(() => {
  console.log("I run when 'keyword' changes.");
}, [keyword]);
useEffect(() => {
  console.log("I run when 'counter' changes.");
}, [counter]);
useEffect(() => {
  console.log("I run when keyword & counter changes.");
}, [counter, keyword]);
```

## 6.3 Recap

useState(): 리액트의 존재 이유, 상태가 변할 때마다 컴포넌트를 다시 실행한다.

useEffect(): 그런데, 모든 상태가 아닌 특정 상태가 변할 때 특정 동작을 하도록 만들 수 있다.

## 6.4 Cleanup

useEffect의 첫번째 인자인 함수, 그 함수의 return을 지정하면 component가 삭제될 때 그 함수가 실행됩니다.

```jsx
import { useState, useEffect } from "react";

function Hello() {
  useEffect(() => {
    console.log("created :)");
    return () => {
      console.log("detroyed :(");
    };
  }, []);
  return <h1>Hello</h1>;
}

function App() {
  const [showing, setShowing] = useState(true);
  const onClick = () => setShowing((prev) => !prev);
  return (
    <div>
      {showing ? <Hello /> : null}
      <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
    </div>
  );
}

export default App;

```

아래와 같이 코드를 분리할 수 도 있습니다. 그런데 잘 사용하진 않습니다.

```jsx
import { useState, useEffect } from "react";

function Hello() {
  function byFn() {
    console.log("bye :(");
  }
  function hiFn() {
    console.log("created :)");
    return byFn;
  }
  useEffect(hiFn, []);
  return <h1>Hello</h1>;
}

function App() {
  const [showing, setShowing] = useState(true);
  const onClick = () => setShowing((prev) => !prev);
  return (
    <div>
      {showing ? <Hello /> : null}
      <button onClick={onClick}>{showing ? "Hide" : "Show"}</button>
    </div>
  );
}

export default App;

```

경험에 비춰보면 clean-up은 많이 사용하지 않습니다.

### sugar님의 정리

정리(clean-up)를 이용하는 Effects

위에서 정리(clean-up)가 필요하지 않은 side effect를 보았지만, 정리(clean-up)가 필요한 effect도 있습니다. 외부 데이터에 구독(subscription)을 설정해야 하는 경우를 생각해보겠습니다. 이런 경우에 메모리 누수가 발생하지 않도록 정리(clean-up)하는 것은 매우 중요합니다.

effect에서 함수를 반환하는 이유는 무엇일까요?

이는 effect를 위한 추가적인 정리(clean-up) 메커니즘입니다. 모든 effect는 정리를 위한 함수를 반환할 수 있습니다.

React가 effect를 정리(clean-up)하는 시점은 정확히 언제일까요?

React는 컴포넌트가 마운트 해제되는 때에 정리(clean-up)를 실행합니다. 하지만 위의 예시에서 보았듯이 effect는 한번이 아니라 렌더링이 실행되는 때마다 실행됩니다. React가 다음 차례의 effect를 실행하기 전에 이전의 렌더링에서 파생된 effect 또한 정리하는 이유가 바로 이 때문입니다.

https://ko.reactjs.org/docs/hooks-effect.html#effects-with-cleanup

# 7 PRACTICE MOVIE APP

## 7.0 To Do List part One

프론트엔드 프로젝트의 가장 기초적인 To-do list

`<form>`, `<input>`, `<button>`은 적응이 안된다.

주의할 점은 `event.preventDefault()`

```jsx
import { useState } from "react";

function App() {
  const [toDo, setToDo] = useState("");
  const [toDos, setToDos] = useState([]); // [toDo1, toDo2, toDo3, ...
  const onChange = (event) => {
    setToDo(event.target.value);
  };
  const onSubmit = (event) => {
    event.preventDefault();
    if (toDo === "") {
      return;
    }
    setToDos((currentArray) => [...currentArray, toDo]);
    setToDo("");
  };
  return (
    <div>
      <h1>My To Dos ({toDos.length})</h1>
      <form onSubmit={onSubmit}>
        <input
          onChange={onChange}
          value={toDo}
          type="text"
          placeholder="Write your to do..."
        />
        <button>Add</button>
      </form>
    </div>
  );
}

export default App;

```

## 7.1 To Do List part Two

react는 li의 key를 인식합니다.

array.map은 item, index를 사용할 수 있습니다.

```jsx
    <div>
      <h1>My To Dos ({toDos.length})</h1>
      <form onSubmit={onSubmit}>
        <input
          onChange={onChange}
          value={toDo}
          type="text"
          placeholder="Write your to do..."
        />
        <button>Add</button>
      </form>
      <hr />
      <ul>
        {toDos.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
```

## 7.2 Coin Tracker

https://api.coinpaprika.com/v1/tickers

오랜만에 사용해보는 fetch()와 then()

component의 3항 연산자

select, option

```jsx
import { useEffect, useState } from "react";

function App() {
  const [loading, setLoading] = useState(true);
  const [coins, setCoins] = useState([]);
  useEffect(() => {
    fetch("https://api.coinpaprika.com/v1/tickers")
      .then((response) => response.json())
      .then((json) => {
        setCoins(json);
        setLoading(false);
      });
  }, []);
  return (
    <div>
      <h1>The Coins! {loading ? "" : coins.length}</h1>
      {loading ? (
        <strong>Loading...</strong>
      ) : (
        <select>
          {coins.map((coin) => {
            return (
              <option key={coin.id}>
                {coin.name} ({coin.symbol}): ${coin.quotes.USD.price} USD
              </option>
            );
          })}
        </select>
      )}
    </div>
  );
}

export default App;

```

## 7.3 Movie App part One

https://yts.mx/api

https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year

```jsx
import { useEffect, useState } from "react";

function App() {
  const [loading, setLoading] = useState(true);
  const [movies, setMovies] = useState([]);
  useEffect(() => {
    fetch(
      "https://yts.mx/api/v2/list_movies.json?minimum_rating=8.5&sort_by=year"
    )
      .then((response) => response.json())
      .then((json) => {
        setMovies(json.data.movies);
        setLoading(false);
      });
  }, []);
  return (
    <div>
      {loading ? (
        <h1>Loading...</h1>
      ) : (
        movies.map((movie) => (
          <div key={movie.id}>
            <img src={movie.medium_cover_image} alt={movie.title} />
            <h2>{movie.title}</h2>
            <p>{movie.summary}</p>
          </div>
        ))
      )}
    </div>
  );
}

export default App;

```

then대신 async, await을 사용할 수도 있습니다. 이게 요즘 문법입니다.

```jsx
import { useEffect, useState } from "react";

function App() {
  const [loading, setLoading] = useState(true);
  const [movies, setMovies] = useState([]);
  const getMovies = async () => {
    const response = await fetch(
      "https://yts.mx/api/v2/list_movies.json?minimum_rating=8.8&sort_by=year"
    );
    const json = await response.json();
    setMovies(json.data.movies);
    setLoading(false);
  };
  useEffect(() => {
    getMovies();
  }, []);
  return (
    <div>
      {loading ? (
        <h1>Loading...</h1>
      ) : (
        movies.map((movie) => (
          <div key={movie.id}>
            <img src={movie.medium_cover_image} />
            <h2>{movie.title}</h2>
            <p>{movie.summary}</p>
            <ul>
              {movie.genres.map((g) => (
                <li key={g}>{g}</li>
              ))}
            </ul>
          </div>
        ))
      )}
    </div>
  );
}

export default App;
```

## 7.4 Movie App part Two

파일이 커지니 분리를 해봅시다.

```jsx
import { useEffect, useState } from "react";
import Movie from "./Movie";

function App() {
  const [loading, setLoading] = useState(true);
  const [movies, setMovies] = useState([]);
  const getMovies = async () => {
    const response = await fetch(
      "https://yts.mx/api/v2/list_movies.json?minimum_rating=8.8&sort_by=year"
    );
    const json = await response.json();
    setMovies(json.data.movies);
    setLoading(false);
  };
  useEffect(() => {
    getMovies();
  }, []);
  return (
    <div>
      {loading ? (
        <h1>Loading...</h1>
      ) : (
        movies.map((movie) => (
          <Movie
            key={movie.id}
            coverImg={movie.medium_cover_image}
            title={movie.title}
            summary={movie.summary}
            genres={movie.genres}
          />
        ))
      )}
    </div>
  );
}

export default App;

```

```jsx
function Movie({ coverImg, title, summary, genres }) {
  return (
    <div>
      <img src={coverImg} alt={title} />
      <h2>{title}</h2>
      <p>{summary}</p>
      <ul>
        {genres.map((g) => (
          <li key={g}>{g}</li>
        ))}
      </ul>
    </div>
  );
}

export default Movie;

```

주의할 점은 ReactJS에서 map을 사용해 component를 생성할 때, key가 꼭 필요합니다.

React router dom을 사용할겁니다. 강의가 2022년에 만들어져서 버전을 지정해줘야 합니다.

```bash
npm i react-router-dom@5.3.0
```

router는 URL을 보고 있는 component입니다.

## 7.5 React Router

```jsx
import { BrowserRouter as Router, Switch, Route } from "react-router-dom";
import Home from "./routes/Home";

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </Router>
  );
}

export default App;

```

- BrowserRouter: [http://localhost:3000/movie](http://localhost:3000/movie/#/)/
- HashRouter: http://localhost:3000/movie/#/

<Switch> Component가 필요한 이유는, URL마다 1개의 Component만 Rendering하고 싶기 때문입니다.

그리고 영화 상세페이지로 가고 싶다면 <a>를 사용해야 한다고 생각했을겁니다. 그렇게 되면 페이지를 Reloading합니다.

그렇게 하지 않고 싶으면 <Link>를 사용하면 됩니다.

```jsx
import propTypes from "prop-types";
import { Link } from "react-router-dom";

function Movie({ coverImg, title, summary, genres }) {
  return (
    <div>
      <img src={coverImg} alt={title} />
      <h2>
        <Link to="/movie">{title}</Link>
      </h2>
      <p>{summary}</p>
      <ul>
        {genres.map((g) => (
          <li key={g}>{g}</li>
        ))}
      </ul>
    </div>
  );
}

Movie.propTypes = {
  coverImg: propTypes.string.isRequired,
  title: propTypes.string.isRequired,
  summary: propTypes.string.isRequired,
  genres: propTypes.arrayOf(propTypes.string).isRequired,
};

export default Movie;

```

## 7.6 Parameters

그러기 위해서는 `<Route path="/movie/:id">`를 사용합시다. `:`가 중요합니다.

```jsx
import { BrowserRouter as Router, Switch, Route } from "react-router-dom";
import Home from "./routes/Home";
import Detail from "./routes/Detail";

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/movie/:id">
          <Detail />
        </Route>
        <Route path="/">
          <Home />
        </Route>
        f
      </Switch>
    </Router>
  );
}

export default App;

```

https://yts.mx/api/v2/movie_details.json?movie_id= 사용

순서: <Link> → <Route path=”:id”> → useParams()

문제: 영화 제목을 클릭하면, URL만 변경되고 Detail Component가 렌더링되지 않음.

버전: react-router-dom, 6.23.1

- App.js

```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "./routes/Home";
import Detail from "./routes/Detail";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/movie/:id" element={<Detail />} />
        <Route path="/" element={<Home />} />
      </Routes>
    </Router>
  );
}

export default App;

```

```jsx
import { useEffect } from "react";
import { useParams } from "react-router-dom";

function Detail() {
  const { id } = useParams();
  const getMovie = async () => {
    const response = await fetch(
      `https://yts.mx/api/v2/movie_details.json?movie_id=${id}`
    );
    const json = await response.json();
    console.log(json);
  };
  useEffect(() => {
    getMovie();
  });
  return <h1>Detail</h1>;
}

export default Detail;

```

## 7.7 Publishing

gh-pages 라이브러리로 한 번에 GitHub에 배포할 수 있습니다. 주의할 점은, package.json에 “homepage”를 설정해 주어야 합니다.

그리고 “scripts”에 “deploy”와 “predeploy”도 설정해 줍시다.

```bash
npm i gh-pages
```

```bash
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
  "deploy": "gh-pages -d build",
  "predeploy": "npm run build"
},
"homepage": "https://myungjinki91.github.io/nomadcoders-react-for-beginners/"
```

npm run deploy를 하면 predeploy가 먼저 실행되고 그 다음 deploy를 실행합니다. 그런데 배포를 하면 흰화면만 나올 경우가 있습니다.

basename을 아래와 같이 수정해 주면 해결됩니다.

```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "./routes/Home";
import Detail from "./routes/Detail";

function App() {
  return (
    <Router basename={process.env.PUBLIC_URL}>
      <Routes>
        <Route path="/movie/:id" element={<Detail />} />
        <Route path="/" element={<Home />} />
      </Routes>
    </Router>
  );
}

export default App;

```