### 시작하며

오늘은 상태관리 라이브러리인 **Redux**에 대해 알아보겠습니다.

# Redux

> **Redux**란?
> **props drilling** 문제를 해결하기 위해 생겨난 데이터 상태관리 라이브러리 중 하나이다.

여기서 **props drilling**이란

데이터를 사용하지 않음에도 props로 데이터를 넘겨주어야하는 행위를 말한다.

<hr>

거두절미하고 **작동 과정**부터 바로 알아보도록 하자.

작동 과정은 다음과 같다.

- **Provider**로 App컴포넌트 묶기
- store폴더 따로 만들고 파일 생성해서 **createSlice**로 데이터 추가
- **configureStore**로 데이터 export
- 데이터 쓰이는 컴포넌트에서 **useSelector**로 데이터 사용

간단하게 설명하면 이런 식이다.

코드를 통해 알아보자.

<hr>

먼저 **Redux** 설치를 위한 명령어를 입력해야한다.

```
npm install @reduxjs/toolkit react-redux
```

이렇게 redux toolkit라는 라이브러리를 다운로드 해서 기존의 Redux 문법에서 더 개선된 문법을 사용할 수 있게된다.

## Redux setting

```
import { configureStore } from '@reduxjs/toolkit'

export default configureStore({
	reducer: {}
})
```

src폴더 안에 store라는 폴더를 따로 만들어서 그 안에 파일을 또 생성한 후에
위 코드를 작성하여 데이터를 전역으로 관리한다.

```
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import { Provider } from "react-redux";
import store from "./store";
import "./index.css";
import App from "./App.jsx";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </StrictMode>,
);
```

그런다음 react-redux에서 **Provider**를 import 받아와서
App 컴포넌트를 위 코드 처럼 **<Provider store={import 해온 스토어 명}>**로 묶으면 App 컴포넌트 뿐만 아니라 하위 컴포넌트들에서 store에 있는 데이터를 사용할 수 있게된다.

```
import { configureStore,createSlice } from '@reduxjs/toolkit'

let data = createSlice({
	name: 이름변수,
	initialName: 초기값
})

export default configureStore({
	reducer: {
	data:data.reducer
}
})
```

이렇게 createSlice로 데이터를 설정하고 configureStore에 export할 데이터를 넣어주면 된다.

이때 createSlice에 initialName이 초기값을 무조건 넣어줘야한다.

```
import { useSelector } from "react-redux";

function 어떤컴포넌트() {
	let state = useSelector((state) => { return state })

  ...

  return 생략
}
```

이렇게 useSelector에 콜백 함수로 state를 반환받아와서 원하는 컴포넌트에서 데이터를 사용할 수 있다.

```
  import { configureStore, createSlice } from '@reduxjs/toolkit'

let data = createSlice({
    name: 이름변수,
    initialState: 'hello',
    reducers : {
    	changeName(state) {
        	return '변경하기 ' + state
        }
    }
});

export let { changeName } = 변수.actions

export default configureStore({
	reducer: {
    	변수2: 변수.reducer
    },
});
```

이렇게 createSlice안의 reducers속성을 이용해서 데이터를 수정하는 함수 또한 store에 저장할 수 있다.

```

  import { useSelector, useDispatch } from "react-redux";
import { changeName } from "../store";

function 어떤컴포넌트() {
    let state = useSelector((state) => { return state })
    let dispatch = useDispatch();

    ...

    return (
    	<div>
            <button onClick={ () => { dispatch(changeName()) }}>
            버튼
            </button>
        </div>
    );
}
```

이제 데이터를 사용하려는 컴포넌트에서 useDispatch()를 활용해서
store에 설정한 함수를 호출해줄 수 있다.
