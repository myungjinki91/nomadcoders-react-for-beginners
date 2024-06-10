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