---
layout: post
title: 리액트 Hook
categories: React
tags: [React]
---

### React Hook

React hooks are a feature introduced in React 16.8 that allow functional components to use state and other features that were previously only available to class components. In this article, we'll cover the basics of React hooks and show you how to use them in your own projects.

React Hook은 기능 컴포넌트가 이전에는 클래스 컴포넌트에서만 사용할 수 있었던 상태 및 기타 기능을 사용할 수 있도록 하는 반응 16.8에 도입된 기능입니다. 이 기사에서는 React Hook의 기본 사항을 다루고 프로젝트에서 사용하는 방법을 보여줄 것입니다.

##### useState

The useState hook is used to add state to a functional component. State is used to manage data within a component, and it allows you to create dynamic user interfaces that can change based on user interaction or data from an API.

useState Hook는 기능 컴포넌트에 상태를 추가하는 데 사용됩니다. 상태는 컴포넌트 내의 데이터를 관리하는 데 사용되며, 이를 통해 사용자 상호 작용 또는 API의 데이터를 기반으로 변경할 수 있는 동적 사용자 인터페이스를 만들 수 있습니다.

```javascript
import React, { useState, useEffect } from "react";

function UserList() {
	const [users, setUsers] = useState([]);

	useEffect(() => {
		fetch("https://jsonplaceholder.typicode.com/users")
			.then((response) => response.json())
			.then((data) => setUsers(data));
	}, []);

	return (
		<ul>
			{users.map((user) => (
				<li key={user.id}>{user.name}</li>
			))}
		</ul>
	);
}
```

This component will render a <div> element with a <p> element that displays the current count and a button that, when clicked, will update the count.

이 컴포넌트는 현재 카운트를 표시하는 <p> 요소와 클릭하면 카운트를 업데이트하는 버튼으로 <div> 요소를 렌더링합니다.

##### useEffect

The useEffect hook is used to perform side effects in a functional component. Side effects can include things like fetching data from an API or updating the document title based on the state of the component.

useEffect Hook는 기능 컴포넌트에서 부작용을 수행하는 데 사용됩니다. 부작용으로는 API에서 데이터를 가져오거나 컴포넌트의 상태에 따라 문서 제목을 업데이트하는 것이 포함될 수 있습니다.

```javascript
import React, { useState, useEffect } from "react";

function UserList() {
	const [users, setUsers] = useState([]);

	useEffect(() => {
		fetch("https://jsonplaceholder.typicode.com/users")
			.then((response) => response.json())
			.then((data) => setUsers(data));
	}, []);

	return (
		<ul>
			{users.map((user) => (
				<li key={user.id}>{user.name}</li>
			))}
		</ul>
	);
}
```

This component will fetch data from the JSONPlaceholder API and store it in the users state variable. The useEffect hook is used to perform the fetch when the component is first mounted.

이 컴포넌트는 JSONPlaceholder API에서 데이터를 가져와 사용자 상태 변수에 저장합니다. useEffect Hook는 컴포넌트를 처음 마운트할 때 가져오기를 수행하는 데 사용됩니다.

##### useContext

The useContext hook is used to consume a context in a functional component. Context allows you to share data between components without having to pass props down through every level of the component tree.

useContext Hook는 기능 컴포넌트의 컨텍스트를 사용하는 데 사용됩니다. 컨텍스트를 사용하면 컴포넌트 트리의 모든 수준에서 컴포넌트를 전달하지 않고도 컴포넌트 간에 데이터를 공유할 수 있습니다.

```javascript
import React, { useContext } from "react";
import MyContext from "./MyContext";

function MyComponent() {
	const myData = useContext(MyContext);

	return (
		<div>
			<p>{myData}</p>
		</div>
	);
}
```

This component will consume the MyContext context and render the data provided by the context.

이 컴포넌트는 MyContext 컨텍스트를 사용하고 컨텍스트에서 제공하는 데이터를 렌더링합니다.

##### Conclusion

In conclusion, React hooks are a powerful feature that allow functional components to use state and other features that were previously only available to class components. The useState hook is used to add state to a functional component, the useEffect hook is used to perform side effects, and the useContext hook is used to consume a context in a functional component. By understanding these basic hooks, you'll be well on your way to building your own React applications.

결론적으로, 리액트 Hook는 기능적 컴포넌트가 이전에는 클래스 컴포넌트에서만 사용할 수 있었던 상태 및 기타 기능을 사용할 수 있는 강력한 기능입니다. useState Hook는 기능 컴포넌트에 상태를 추가하는 데 사용되고, useEffect Hook는 부작용을 수행하는 데 사용되며, useContext Hook는 기능 컴포넌트의 컨텍스트를 사용하는 데 사용됩니다. 이러한 기본적인 Hook를 이해하면 자신만의 React 응용 프로그램을 구축할 수 있습니다.
