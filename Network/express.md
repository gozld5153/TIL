# Express
> ### express.json
* express version 4.6 이상부터 `body-parser`기능 내장 
```js
const express = require('express')
const app = express()

app.use(express.json())
//request로 오는 paylaod에 내용을 파싱한 후 request.body에 할당한다 
```

* 위와 같이 했는데도 parsing이 제대로 이루어지지 않아 오류가 나는 경우가 있다. 

```js
const express = require('express')
const app = express()

app.use(express.json({strict: false}))
//express.json의 옵션으로 strict가 있다. 기본값으 true이고 false로 바꿔주게 되면 모든 타입을 parsing해 준다
```
***
> ### 모듈 corse
`express`모듈은 `cors`에 응답하기 위해서 모든 요청의 헤더에 `access-control-allow-origin`을 작성할 필요가 없다.    
`cors`모듈을 사용하면 손쉽게 `cors`를 적용할 수 있다.
```js
npm install cors
```
```js
const express = require('express')
const app = express()
const cors = require('cors')

app.use(cors())
```