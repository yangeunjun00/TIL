오늘 배운 것

# useRef hook

useRef는 React에서 자체적으로 제공하는 hook 중 하나이다.

거두절미 하고 useRef가 무엇인지 소개해보도록 하겠다.

useState를 사용한 변수는 렌더링이 되면 초기화가 된다.

근데 이 useRef를 사용한 변수는 렌더링이 되어도 값이 초기화 되지 않고 유지된다.

이 유지 된 값은 컴포넌트가 언마운트 되기 전 까지는 계속 유지된다.

useRef를 어떻게 사용하는지 알아보도록 하자

### 선언

```
const ref = useRef(0);
```

이렇게 일반 변수처럼 선언하고 useRef의 인자로 들어가는 값은 해당 변수의 기본값이 된다.

그리고 이 변수의 형태는 **객체(object)**라서 이렇게 저장된다.

```
{ref: 0}
```

```
ref.current = ref.current+1;
console.log(ref.current);
```

사용 할 때는 `변수명.current` 이렇게 하면 객체 형태가 아닌 일반적인 변수처럼 사용할 수 있다.

### DOM 요소 접근

```
const inputRef = useRef();

useEffect(()=>{
    inputRef.current.focus();
},[]);

<input ref={inputRef}></input>
```

이렇게 하면 컴포넌트가 마운트 되었을 때 inputRef 변수가 DOM 요소에 접근 해 인풋이 자동으로 포커스 되도록 한다.

이 useRef hook은 값이 저장은 되야하지만 렌더링 되면 안되는 경우에 사용하면 된다.

뭔가 더 설명해야 하는데 뭘 해야 할 지 모르겠다.
