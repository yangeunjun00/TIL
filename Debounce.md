오늘 배운 것

# Debounce

Debounce는 이벤트가 짧은시간에 여러번 반복될 때 마지막 이벤트가 발동된 후 몇초 뒤에 함수를 호출하는 기법이다.

## 이게 왜 필요할까?

만약 엄청나게 많은 작업을 하는 이벤트(실제 서버에서 데이터를 가져오는 함수)가 있다고 하자 이 이벤트를 여러번 연속으로 반복하면 불필요한 네트워크 요청이 발생하여 막대한 서버 비용을 지불해야 한다.

이 문제를 예방하기 위해 Debounce를 쓰는거다.

### 사용 법

```
useEffect(()=>{
    const timer = setTimeout(()=>{
        console.log("업데데이트!")
        setInput(input)
    },1000)
    return clearTimer(timer)
},[input])
```

위 코드는 input의 값이 바뀔 때마다 useEffect가 실행되어 setTimeout이 돌아가다가 다시 input의 값이 변하면 clearTimer를 통해 전에 있던 setTimeout을 지우고 새로 setTimeout을 시작하다가 마지막으로 input의 값을 변화시켜주면 1초 뒤에 setInput으로 input을 업데이트 해주고 업데데이트! 가 콘솔에 출력된다.
