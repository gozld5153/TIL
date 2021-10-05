# Effect Hook
> ## Effect Hook ?
함수 컴포넌트 내에서 `side effects`를 수행할 수 있게 해주는 react Hook의 내장함수.
 *  `side effects`란 함수내부의 작동이 함수외부에 영향을 미치는 것을 말한다.  
***
> ## useEffect
화면이 랜더링 될 때마다 effect라는 함수를 실행시킨다. 
```js
useEffect(() => {
   console.log("hi")
})
//랜더링이 일어날 때마다 "hi"가 찍힌다. 
```
특정값들이 리랜더링 시에 변경되지 않는다면 리액트로 하여금 `effect`를 건너뛰도록 할 수 있다. 

```js
const [count, setCount] = useState(0)
useEffect(() => {
   document.title = "hello"
}, [count])
//처음 랜더링이 된 후 실행되고 count 값이 변하지 않는한 실행되지 않는다. 

const [count, setCount] = useState(0)
useEffect(() => {
  setCount(count + 1)
}, [count])
//처음 랜더링 되면서 effect함수가 실행된다. count 값이 변하게 되고 다시 랜더링이 일어나게 된다. 무한반복

const [count, setCount] = useState(0)
useEffect(() => {
  setCount(count + 1)
}, [])
//두번째 인자에 빈배열을 넣을 경우 처음 랜더링이 될 때 한번만 실행된다.
```