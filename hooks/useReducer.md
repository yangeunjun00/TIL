오늘 배운 것

# useReducer

오늘 배운 useReducer hook은 변수의 상태를 관리하는 useState의 상위호환이라고 볼 수 있다.

useReducer는 크게 **reducer**, **dispatch**, **action**
이렇게 세개로 이루어져 있다.

이 세가지를 간단하게 설명하면 다음 과 같다.

### reducer

reducer는 변수의 상태 즉 state를 업데이트 해주는 역할을 맡는다.

### dispatch

dispatch는 state 업데이트를 위한 요구라고 볼 수 있다.

### action

action은 요구의 내용이라고 정의할 수 있겠다.

## 사용 법

```
const [money,dispatch] = useReducer(reducer,0);
```

선언은 기본적으로 이렇게 [] 안에 업데이트가 될 state 변수와 dispatch 함수
그리고 useReducer의 인자로는 state를 업데이트 해줄 reducer함수와 state의 기본값을 넣어준다.

### dispatch

```

dispatch({type:"wjrwktodwhs", 수행:"밥 먹기"});

```

dispatch 함수는 이런 식으로 이 업데이트는 어떤 type이고 어떤 수행을 할 건지를 인자에 객체 형태로 넣어준다.

### reducer

const reducer= (state,action)=>{
return state+action.수행
}

reducer 함수에는 인자로 앞서 useReducer를 선언할 때 써준 money 값을 업데이트 하기 위한 state 와 업데이트를 수행 할 action 함수(dispatch 라고 보면 될 듯)를 넣어준다.
