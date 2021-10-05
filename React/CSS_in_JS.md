# CSS in JS
> ## Styled Component
* **Automatic critical CSS**    
Styled Component는 화면에 어떤 컴포넌틑가 렌더링 되었는지 추적해서 해당하는 컴포넌트에 대한 스타일을 자동으로 삽입합니다. 따라서 코드를 적절히 분배해 놓으면 사용자가 어플리케이션을 사용할 때 최소한의 코드만으로 화면이 띄워지도록 할 수 있습니다.

* **No Class name bugs**    
Styled Component 는 스스로 유니크한 `className` 을 생성합니다. 이는 `className` 의 중복이나 오타로 인한 버그를 줄여줍니다.

* **Easier deletion of CSS**    
기존에는 더 이상 사용하지 않거나 삭제한 컴포넌트에 해당하는 스타일 속성을 제거하기위해 CSS 파일 안의 `className`을 이리저리 찾아야 했습니다. 하지만 Styled Component 는 모든 스타일 속성이 특정 컴포넌트와 연결되어 있기 때문에 만약 컴포넌트를 더 이상 사용하지 않아 삭제할 경우 이에 대한 스타일 속성도 함께 삭제됩니다.

* **Simple dynamic styling**    
 `className`을 일일이 수동으로 관리할 필요 없이 React 의 props 나 전역 속성을 기반으로 컴포넌트에 스타일 속성을 부여하기 때문에 간단하고 직관적입니다.

 * **Painless maintenance**    
 컴포넌트에 스타일을 상속하는 속성을 찾아 다른 CSS 파일들을 검색하지 않아도 되기 때문에 코드의 크기가 커지더라도 유지보수가 어렵지 않습니다.

 * **Automatic vendor prefixing**    
 개별 컴포넌트마다 기존의 CSS 를 이용하여 스타일 속성을 정의하면 될 뿐입니다. 이외의 것들은 Styled Component 가 알아서 처리해 줍니다

 > ### Installation
 ```js
$ npm install --save styled-components
 ```

 Styled Component 에서는 package.json에 다음 코드를 추가하도록 권장하고 있습니다. 아래의 코드를 추가하면 여러 버전의 Styled Component가 설치되어 발생하는 문제를 줄여줍니다.
```js
{
  "resolutions": {
    "styled-components": "^5"
  }
}
```
실제 사용 예
```js
//컴포넌트를 생성하고 styled 뒤에 html tag를 붙여준 후 백틱 사이에 기존 CSS속성을 삽입한다. 
const Button = styled.button`
   padding: 0, auto;
   marigin: 1em;
`;
```

같은 스타일 속성을 지닌 여러개의 컴포넌트들 중 몇 개의 컴포넌트에 약간의 변화를 주고 싶은 경우

```js
//styled ()안에 컴포넌트 명을 입력한다.
const Tomato = styled(Button)`
   color: tomato;
`;
```

### [styled-components](https://styled-components.com/)