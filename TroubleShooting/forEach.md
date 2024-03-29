# forEach

## 문제인식
`forEach`는 배열 인덱스 오름차순 순서대로 콜백함수를 실행시킨다. 
비동기처리의 경우 `forEach`는 콜백함수의 결과를 기다리지 않고 바로 다음 콜백함수를 호출한다. (aysnc / await 구문 적용 X)

그렇다면 동기적인 처리의 경우에도 콜백함수만 순차적으로 호출하고 콜백함수의 결과를 기다려 주지 않는 걸까?

## 실험
각각의 인덱스에서 피보나치 수열을 만드는 재귀함수를 호출한다. 만약 콜백함수의 결과를 기다리지 않는다면 먼저 완료된 콜백함수의 결과물이 출력될 것이다.

```js
const arr = [20, 5, 1]

arr.forEach(item => {
  const fibo = (num) => {
    if (num <= 1) return 1
    return fibo(num - 1) + fibo(num - 2)
  }

  console.log(fibo(item))
})

// 실행결과
// 10946
// 8
// 1
```

## 추론
실험 결과 동기처리의 경우에 콜백함수의 결과물을 기다리고 순차적으로 처리한 것을 알 수 있었다. 결과물을 통해 추론한 것은 `JS`가 작동하는 방식은 single thread로 하나의 스택을 가지고 있다. 동기처리의 경우 각각의 작업이 스택에 쌓이고 작업이 완료되고 스택에서 사라진 후에 다음 작업이 실행되기 때문에 `forEach`안에서 순차적으로 콜백함수가 작동한다.



