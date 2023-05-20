## React-Query

### Keys

react query를 사용하면서 가장 나를 헷갈리게 한 것이 이 `key`라는 개념이다. 아직까지도 정확한 개념 정의는 된 것 같지 않지만 어느 정도 파악한 것들을 정리해 보고자 한다.

### what is key?

> At its core, TanStack Query manages query caching for you based on query keys. Query keys have to be an Array at the top level, and can be as simple as an Array with a single string, or as complex as an array of many strings and nested objects. As long as the query key is serializable, and unique to the query's data, you can use it!

공식 문서에서 제공하는 key의 정의는 위와 같다. 이를 바탕으로 내가 이해한 key의 정의는,

1. 쿼리의 주요 기능인 data 캐싱에 핵심적인 역할을 한다.
2. key는 배열로 이루어져야 하고, 요소는 단순 string 이거나 배열, 객체가 올 수 있다.
3. 직렬화가 가능해야 하며 쿼리의 데이타에 고유해야 한다.

쿼리의 캐싱 데이타에 접근하기 위한 역할을 하는 것이 key이기 때문에 각 캐싱 데이타에 접근하기 위해서는 key 값이 고유해야 한다는 것으로 이해했다.  
 결국 key는 쿼리에서 캐시된 데이터의 식별자로 사용되는 것이다. 하지만 실제로 코드 상에서는 단순 식별자로서의 기능 뿐만 아니라 query function에서 매개변수로 할당되어 사용되기도 한다.

```js
const { data } = useQuery(["test", foo], () => bar(foo));
```

key 배열의 두번째 요소에 `foo`라는 변수가 들어갔고, 해당 변수의 값이 바뀌면 새로운 키가 생성되면서 bar()함수를 다시 실행하게 된다. 여기서 중요한 점은 쿼리에서 제공하는 `refetch` 메소드와 위 방식의 차이점이다. 위 방식은 새로운 키를 생성하여 새로운 데이타를 캐싱하는 방법이고, `refetch`의 경우 동일한 키를 사용하기 때문에 같은 결과를 캐싱한다.

처음에 단순히 `key`를 캐싱된 data에 접근하기 위한 유니크한 값으로만 생각했기 때문에 왜 `key`의 요소에 객체나 배열이 들어가는지 이해할 수가 없었다. 단순한 열쇠역할 뿐만 아니라 query function의 매개변수로도 활용되기 때문에 공식문서에서 정의한 `key`를 조금이나 이해할 수 있었다.

### 나만의 key 정의

useEffect 의존성 배열이 고유하다!
