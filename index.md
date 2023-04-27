This is a modified version of the [Pokedex exercise](https://t3-tools.notion.site/Pokedex-Problem-90f9dcfff10d4418a6fad44581b1ecff) by [Theo](https://twitter.com/t3dotgg) using [JSONPlaceholder](https://jsonplaceholder.typicode.com/) todos. Much credit to OpenAI's GPT4 for writing most of this:

# TodoList Exercise

**Intended candidate: Junior to mid-level frontend engineer**

## Part 1: Create a `<TodoRow>` component

Provided a Todo JavaScript object structured as such:

```js
const sampleTodo = {
  userId: 1,
  id: 3,
  title: "fugiat veniam minus",
  completed: false,
};
```

...create a reusable <TodoRow /> component (or the equivalent in your framework) that takes in sampleTodo as a property and renders a row with the userId, id, title, and completion status.

## Part 2: Create a `<TodoTable>` component

Provided a Todo JavaScript array structured as such:

```js
const todoArray = [
{
  userId: 1,
  id: 1,
  title: "Lorem ipsum dolor sit amet",
  completed: true
}, {
  userId: 2,
  id: 2,
  title: "Consectetur adipiscing elit",
  completed: false
}, ...]
```

...create a <TodoListTable /> component that takes in the array and renders all the todos in that array.

## Part 3: Create a `<FilterableTodoListTable>`

Provided a <TodoCompletionFilter /> component with the following props:

```tsx
type TodoCompletionFilterProps = {
  selectedCompletionStatus: boolean | undefined;
  selectCompletionStatus: (status: boolean | undefined) => void;
};
```

...create a <FilterableTodoListTable /> component that renders both the <TodoCompletionFilter /> component and <TodoListTable /> component. Make sure you only display todos with the selected completion status!

## Part 4: Fetching todos from JSONPlaceholder

In this part, you'll fetch the todos from `https://jsonplaceholder.typicode.com/todos` and display them using the components you created in the previous parts.

1. In your application, create a function called `fetchTodos` that fetches todos from the JSONPlaceholder API. This function should return a Promise that resolves with an array of todos.

```js
function fetchTodos() {
  return fetch("https://jsonplaceholder.typicode.com/todos").then((response) =>
    response.json()
  );
}
```

2. In your `<FilterableTodoListTable />` component, add a state variable to store the fetched todos. When the component mounts, call the `fetchTodos` function and update the state with the fetched todos.

If you're using React, this can be achieved using the `useState` and `useEffect` hooks:

```jsx
import React, { useState, useEffect } from "react";

function FilterableTodoListTable() {
  const [todos, setTodos] = useState([]);

  useEffect(() => {
    fetchTodos().then((fetchedTodos) => {
      setTodos(fetchedTodos);
    });
  }, []);

  // Render your TodoCompletionFilter and TodoListTable components here
}
```

3. Pass the fetched todos to the `<TodoListTable />` component and ensure that the todos are displayed correctly.

4. Test the filtering functionality using the `<TodoCompletionFilter />` component to ensure that it still works with the fetched todos.

With these additional instructions, the candidate should be able to fetch the todos from JSONPlaceholder and display them using the previously created components.
