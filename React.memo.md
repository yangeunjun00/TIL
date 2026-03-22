오늘 배운 것

# React.memo

오늘 배운 React.memo는 앞서 배웠던 useMemo, useCallback 과 같이 메모이제이션을 해서 불필요한 렌더링을 방지하는 기술이다.

### 작동 과정

부모 컴포넌트에서 자식 컴포넌트로 props 데이터를 보낼 때 props 데이터가 변하지 않고 그대로라면(이걸 prop check 라고 함)
prop check를 통해 렌더링을 하지 않게 한다.

### 사용 법

```
import {memo} from 'react';

// 자식 컴포넌트(Child.jsx)


function Child(){
    ...
    ...
    ...
}
export default memo(Child);
```

이렇게 export 로 컴포넌트를 보낼 때 memo() 안에 인자로 컴포넌트를 넣어서 prop check를 할 수 있게 하면 된다.
