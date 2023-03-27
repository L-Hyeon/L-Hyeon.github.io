---
layout: post
title: 리액트의 기본
categories: React
tags: [React]
---

### Understanding the basics of React

React는 사용자 인터페이스를 구축하기 위해 널리 사용되는 자바스크립트 프레임워크이다. 이 글에서는 componets, props 및 state를 포함한 React의 기본 사항에 대해 설명합니다

##### Components

React 응용 프로그램의 핵심 구성 요소는 component입니다. component는 응용 프로그램 전체에서 재사용할 수 있는 독립적인 코드 블록입니다. component는 버튼이나 텍스트 입력과 같이 단순할 수도 있고, 전체 양식이나 사용자 인터페이스와 같이 더 복잡할 수도 있습니다.

component는 자바스크립트로 작성되며 클래스 또는 함수로 작성될 수 있습니다. 다음은 간단한 component의 예입니다:

```javascript
function HelloWorld() {
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  );
}
```

이 component는 내부에 "Hello, World!"라는 요소가 있는 <div> 요소를 렌더링합니다.

##### Props

props은 "속성"의 줄임말로, component 간에 데이터를 전달하는 데 사용됩니다. 구성요소의 동작 또는 모양을 사용자 지정하는 데 props을 사용할 수 있습니다. 예를 들어, 단추 구성요소가 있는 경우 도구를 사용하여 단추의 텍스트나 단추 색상을 사용자 정의할 수 있습니다.

다음은 props을 사용할 수 있는 component의 예입니다:

```javascript
function Button(props) {
  return <button style={{ backgroundColor: props.color }}>{props.text}</button>;
}

<Button color="blue" text="Click me!" />;
```

이 component는 파란색 배경과 "Click me!"라는 텍스트가 있는 버튼 요소를 렌더링합니다.

##### State

상태는 component 내의 데이터를 관리하는 데 사용됩니다. 상태를 사용하면 사용자 상호 작용 또는 API의 데이터에 따라 변경할 수 있는 동적 사용자 인터페이스를 만들 수 있습니다. component의 상태가 변경되면 React는 새 상태를 반영하도록 사용자 인터페이스를 자동으로 업데이트합니다.

다음은 상태를 포함하는 component의 예입니다:

```javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me!
        </button>
      </div>
    );
  }
}
```

이 component는 현재 카운트를 표시하는 <p> 요소와 클릭하면 카운트를 업데이트하는 버튼으로 <div> 요소를 렌더링합니다.

##### Conclusion

결론적으로 component, props 및 state는 React 응용 프로그램의 구성 요소입니다. component는 재사용 가능한 코드 블록이며, component 간에 데이터를 전달하는 데 props이 사용되며, 상태는 component 내의 데이터를 관리하는 데 사용됩니다. 이러한 기본 개념을 이해함으로써, 독자적인 리액트 애플리케이션을 구축할 수 있습니다.
