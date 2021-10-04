# Redux
> ### Redux?
`Redux`는 `state`관리를 도와주는 라이브러리이다.    
```
View -> Action -> Reducer(s) -> Stroe -> View
```
`View`는 `state`의 관리 컨테이너이다. 이곳에서 event 호출이 발생하면 `Dispatch` 메소드에 `Action` 객체를 인자로 받아서 `Reducer`를 호출하게 된다. `Reducer`에 의해 새로운 `state`가 생성되고 이 값이 `Store`에 저장된다.
***
> ### Action
`action`은 `type`과 `payload`를 가지고 있는 자바스크립트 객체이다. `type`은 **action type**이라고 부르기도 한다. `type`은 문자열이고, `payload`는 어떤 타입이든지 올 수 있다. 
```js
{
   type: 'string',
   payload: [{string: "hi"}, {arr: ["h", "i"]}]
}
```
`action`의 실행은 **dispatching**이라고 부른다. `store`의 상태를 변경하기 위해 `action`을 `dispatch`한다.
***
> ### Reducer
`reducer`는 단방향 데이터 흐름 과정중의 한 부분이다. `dispatch`된 `action` 객체는 `reducer`를 통과하게 된다.     
`reducer`는 순수함수이다. 그러므로 input값이 동일하면 항상 같은 output을 반환한다. `reducer`함수는 `state`와 `action` 두 가지를 인자를 갖는다. 여기서 `state`는 `store`에 저장되어 있는 전역 `state` 즉 변경되기 전의 `state`다. 이전의 `state`와 `dispatch`된 `action`객체를 가지고 새로운 `state`를 만든다.
```
(preState, action) => newState
```
`reducer`는 순수함수이기 때문에 데이터의 immutable이 지켜져야 한다. 이전의 `state`가 바뀌는 것이 아니라 새로운 `state`를 return해야 한다. 
```js
function(state, action){
   state.push(action.payload)
   return state
}
```
위와 같은 함수는 redux에서 허용되지 않는다. push 메소드는 새로운 `state`를 반환하는 대신 이전 `state`를 변경하기 때문이다.    
아래의 함수는 새로운 `state`를 반환하기 때문에 허용된다. 
```js
function reducer(state, action){
   return state.concat(action.payload)
} 
```
`action`객체의 `type`은 `action`이 `reducer`함수에 전달된 후 `reducer`함수에 의해 `action`의 `type`이 평가된다. 결국 `type`에 따라 다른 `state`값을 생성하게 된다.
```js
function reducer(state, action){
   switch(action.type){
      case 'string' : {
         //do something and return new State
      }
      case 'number' : {
         //do something and return new State
      }
      default: return state
   }
}
```
***
> ### Store
`store`는 단 하나만의 글로벌 객체를 지닌다. `import`를 통해 사용할 수 있다. 
```js
import { createStore } from 'redux';
```
`creatStore`함수는 `reducer`함수를 필수 인자로 사용한다.
```js
const store = createStore(reducer);
```
`createStore`는 두번째 인자를 옵션으로 받는다. 두번째 인자는 초기 `state`값이다. 
```js
const store = createStore(reducer, []);
```
```js
//action을 dispatch 하는 방법
stroe.dispatch({
   type: 'TODO_ADD',
   todo: {id: '0', name: 'learn redux', completed: false},
})

//store에서 글로벌 state를 가져오는 방법
store.getState()
```
***
> ### 예시코드
``` js
const { createStore } = require('redux');
const CHANGE_NAME = 'CHANGE_NAME';
const ADD_POST = 'ADD_POST';
//state
const initState = {
  name: '백지욱',
  posts: [],
};
//action
const changeName = (data) => {
  return {
    //action 객체
    type: CHANGE_NAME,
    payload: data,
  };
};
const addPost = (post) => {
  return {
    type: ADD_POST,
    payload: post,
  };
};
//reducer
const reducer = (prevState, action) => {
  switch (action.type) {
    case CHANGE_NAME:
      return {
        ...prevState,
        name: action.payload,
      };
    case ADD_POST:
      return {
        ...prevState,
        posts: [...prevState.posts, action.payload],
      };
    default:
      return prevState;
  }
};
//store
const store = createStore(reducer, initState);

console.log(store.getState());
store.dispatch(changeName('이창우'));
console.log(store.getState());
store.dispatch(addPost('2'));
store.dispatch(addPost('2'));
console.log(store.getState());
```