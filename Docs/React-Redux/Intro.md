[TOC]



# Redux Introduction

The whole global state of the app is stored in an object tree inside a single store. 

The only way to change the state tree is to create an action, an object describing what happened, and dispatch it to the store.

**Note**: Redux state should contain only plain JS objects, arrays and primitives. The root state value is usually an object.

```js
function counterReducer(state = { value: 0 }, action) {
  switch (action.type) {
    case 'counter/incremented':
      return { value: state.value + 1 }
    case 'counter/decremented':
      return { value: state.value - 1 }
    default:
      return state
  }
}
// Create a Redux store holding the state of the app APIs is { subscribe, dispatch, getState}
let store = createStore(counterReducer)

// You can use subscribe() to update the UI in response to state changes.
// Normally you'd use a view binding library (e.g. React Redux) rather than subscribe() directly.
// There may be additional use cases where it's helpful to subscribe as well.

// The only way to mutate the internal state is to dispatch an action.
// The actions can be serialized, logged or stored and later replayed.
store.dispatch({ type: 'counter/incremented' })
// {value: 1}
```

## Core Concepts

State is a JS plain Object, (model except setters)

To change the state, you need to dispatch an action. An action is a plain JS object

Reducer: function takes state and action as arguments, and return the next state of the app.

Redux is more useful when:

- You have large amounts of application state that are needed in many places in the app
- The app state is updated frequently over time
- The logic to update that state may be complex
- The app has a medium or large-sized codebase, and might be worked on by many people

JavaScript objects and arrays are all mutable by default. If I create an object, I can change the contents of its fields. If I create an array, I can change the contents as well:

```js
const obj = { a: 1, b: 2 }
// still the same object outside, but the contents have changed
obj.b = 3

const arr = ['a', 'b']
// In the same way, we can change the contents of this array
arr.push('c')
arr[1] = 'd'
```

**In order to update values immutably, your code must make \*copies\* of existing objects/arrays, and then modify the copies**.

```js
const obj2 = {
  // copy obj
  ...obj,
  // overwrite a
  a: {
    // copy obj.a
    ...obj.a,
    // overwrite c
    c: 42
  }
}

const arr = ['a', 'b']
// Create a new copy of arr, with "c" appended to the end
const arr2 = arr.concat('c')

// or, we can make a copy of the original array:
const arr3 = arr.slice()
// and mutate the copy:
arr3.push('c')
```

An **action** is a plain JavaScript object that has a `type` field.  The `type` field should be a string that gives this action a descriptive name, like `"todos/todoAdded"`. We usually write that type string like `"domain/eventName"`, where the first part is the feature or category that this action belongs to, and the second part is the specific thing that happened.

An action object can have other fields with additional information about what happened. By convention, we put that information in a field called `payload`.

An **action creator** is a function that creates and returns an action object. We typically use these so we don't have to write the action object by hand every time

```js
const addTodo = text => {
  return {
    type: 'todos/todoAdded',
    payload: text
  }
}
```



A **reducer** is a function that receives the current `state` and an `action` object, decides how to update the state if necessary, and returns the new state: `(state, action) => newState`. **You can think of a reducer as an event listener which handles events based on the received action (event) type.**

Reducers must *always* follow some specific rules:

- They should only calculate the new state value based on the `state` and `action` arguments
- They are not allowed to modify the existing `state`. Instead, they must make *immutable updates*, by copying the existing `state` and making changes to the copied values.
- They must not do any asynchronous logic, calculate random values, or cause other "side effects"



```js
const initialState = { value: 0 }

function counterReducer(state = initialState, action) {
  // Check to see if the reducer cares about this action
  if (action.type === 'counter/increment') {
    // If so, make a copy of `state`
    return {
      ...state,
      // and update the copy with the new value
      value: state.value + 1
    }
  }
  // otherwise return the existing state unchanged
  return state
}
```

The current Redux application state lives in an object called the **store** .

The store is created by passing in a reducer, and has a method called `getState` that returns the current state value:

```js
import { configureStore } from '@reduxjs/toolkit'

const store = configureStore({ reducer: counterReducer })

console.log(store.getState())
// {value: 0}
```

The Redux store has a method called `dispatch`. **The only way to update the state is to call `store.dispatch()` and pass in an action object**. The store will run its reducer function and save the new state value inside, and we can call `getState()` to retrieve the updated value



**Selectors** are functions that know how to extract specific pieces of information from a store state value. As an application grows bigger, this can help avoid repeating logic as different parts of the app need to read the same data:



**A "slice" is a collection of Redux reducer logic and actions for a single feature in your app**, typically defined together in a single file. The name comes from splitting up the root Redux state object into multiple "slices" of state.



**Writing Async logic with Thunks**:

So far, all the logic in our application has been synchronous. Actions are dispatched, the store runs the reducers and calculates the new state, and the dispatch function finishes. But, the JavaScript language has many ways to write code that is asynchronous, and our apps normally have async logic for things like fetching data from an API. We need a place to put that async logic in our Redux apps.

A **thunk** is a specific kind of Redux function that can contain asynchronous logic. Thunks are written using two functions:

- An inside thunk function, which gets `dispatch` and `getState` as arguments
- The outside creator function, which creates and returns the thunk function





# React-Redux Introduction





# Redux ToolKit Introduction

It wraps around the Redux core, and contains packages and functions that are essential for building Redux app.

