# 리덕스
- 리덕스는 자바스크립트 어플리케이션의 위한 예측 가능한 스테이트 컨테이너입니다.
- 리덕스는 어플리케이션 박스 안에 `데이터`가 포함되어 있다. 
- 리덕스는 그 자체를 `스테이트 컨테이너`라고 묘사한다. 

# 리액트
- 리액트는 `뷰`가 포함되어 있다.
- 유저가 실제로 상호 작용하게 만든다. 

# 컴포넌트 레벨 스테이트와 리덕스 스테이트
## 컴포넌트 레벨 스테이트
- 컨테이너 만의 스테이트 

r 리덕스 레벨 스테이트
- 어플리케이션 레벨 스테이드. 즉, 어플리 케이션 전체 

# 리듀서
- 리듀서는 어플리케이션 스테이트를 반환하는 함수이다. 
- 리듀서는 스테이트의 값을 만든다. 
```js
// Application State - Generated by reducers
{
  books:[{title: 'Harry Potter'},{title:'Javascript'}],
  activeBook:{title:'Javascript:The Good Parts'}
}
```

# 리덕스와 리액트
- 리덕스는 어플리케이션 스테이트를 구조화 하는데 도움을 주고
- 리액트는 이것들을 디스플레이 하는 뷰를 제공한다. 

# Action, Action Creator, Reducer
- Action creattor is function to return some action.
- Action is a object flowing to all reducer.
- Reducer make value for specific state.

# Action
- Action is a object made two value 'type' and 'payload'
- type is named as uppercase with '_'.
- payload hvae many information.

# 
