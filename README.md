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
