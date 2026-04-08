## 시작하며

오늘은 저번에 포스팅 한 상태 관리 라이브러리 **Redux** 처럼 데이터의 상태를 관리하는 라이브러리인 **Zustand**를 알아보겠습니다.
또한 전역 상태 관리를 **Zustand** 뿐만 아니라 **Redux, recoil, contextAPI** 등등 여러가지가 있는데 그 중에서 **Zustand**를 사용하는 이유를 알아보겠습니다.

# Zustand

**Zustand**는 데이터의 상태를 전역 **store**에서 관리할 수 있는 라이브러리 중 하나이다.

이렇게만 설명하면 저번에 포스팅한 Redux와 별반 다를게 없어 보이지만

> **Zustand**는 **Redux**와 달리
> store에 있는 변수를 어느 컴포넌트에서 사용할 것인지 정하는 **Provider**와
> 데이터를 어떻게 수정할지 정하는 **Action** 과
> 데이터를 실제로 수정하는 수정함수 **reducer**

위 세개를 설정하지 않고 store에서 데이터 선언과 수정함수 선언이 가능하다.

이 점에서 **Zustand**는 **Redux**와 다르게 빠른 프로토타입 개발이 가능해진다.

## 사용

### React에서 store를 사용해보자

**1. store 만들기**

```
// stores/useCounterStore.ts

import { create } from "zustand";



type CounterState = {

  count: number;

  increase: () => void;

};



export const useCounterStore = create<CounterState>((set) => ({

  count: 0,

  increase: () => set((state) => ({ count: state.count + 1 })),

}));
```

store에서 위와 같이 **create**를 통해 변수 및 수정함수를 hook을 직접 만들어 사용할 수 있다.

**2. 컴포넌트에서 데이터 불러오기**

```
import { useCounterStore } from "@/stores/useCounterStore";



function Counter() {

  const count = useCounterStore((state) => state.count);

  const increase = useCounterStore((state) => state.increase);



  return (

    <button onClick={increase}>

      count: {count}

    </button>

  );

}
```

이렇게 store를 import 해오고 store에서 create를 통해 생성한 함수(useCounterStore)를 hook처럼 사용할 수 있다.

여기서 **useCounterStore**의 매개변수로 있는 **state**는 useCounterStore안에 들어있는 모든 변수와 수정함수를 담고 있다.
그래서 **state.count, state.increase** 이렇게 꺼내서 사용하는 것 이다.

### 특징

위를 예시로 들어보면

```
const count = useCounterStore((state)=>state.count);
```

이처럼 여러 상태가 store에 있어도 원하는 상태만 렌더링 시킬 수 있기때문에
**불필요한 렌더링을 줄일 수 있다!**

또한 다른 상태가 바뀌어도 이 상태에는 영향이 없음

### Next.js에서 사용하기

Next.js에서도 Zustand는 hook처럼 그대로 사용한다.

```
import { useCounterStore } from "@/stores/useCounterStore";



function Counter() {

  const count = useCounterStore((state) => state.count);

  const increase = useCounterStore((state) => state.increase);



  return (

    <button onClick={increase}>

      count: {count}

    </button>

  );

}
```

그러나 store 파일을 제외하고 store에 있는 상태를 불러오는 즉,
hook을 사용하는 파일은 무조건 클라이언트 컴포넌트여야 하기에

```
'use client';
```

을 사용해주어야 한다.

### 이런 프로젝트에서 사용해야 한다

**1.빠른 MVP 및 프로토타입 개발 프로젝트**
초기 기획 과 개발 단계에서 따로 설정 필요없이 빠른 개발속도가 중요한 경우

**2.서비스형 프로젝트**
로그인 여부, 사용자 상태, UI상태 등등 전역으로 관리해야하는 데이터가 많은 경우
