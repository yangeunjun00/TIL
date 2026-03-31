오늘 배운 것

# Axios

node.js 와 브라우저를 위한 Promise 기반 HTTP 클라이언트이다.

## 특징

- JSON 데이터 자동 변환
- 브라우저를 위한 XMLhttpRequest 생성
- node.js를 위해 http 요청 생성
- Promise API 지원

## 설치

npm 사용시

```
npm install axios
```

## 왜 쓸까

브라우저에서 기본적으로 지원하는 fetch()함수로 간결한 데이터 처리는 가능하다.
그러나 axios는 fetch()를 사용했을 때 생겼던 불편함을 해결할 수 있다.
예를 들면 JSON 형식 자동 변환말이다.
뿐만 아니라 문법 자체도 axios가 훨씬 간결하다.

## 사용

axios에 해당 config을 전송하면 요청이 가능하다.

```
// axios(config)

axios({
    method: "post",
    url: "urlurlulr",
    data:{
        firstName: "a",
        lastName: "b
    }
});
```

```
const interface = axios.create({
    baseurl: "/api",

});


interface({
    url: "/hihi",
    method: 'get'
});
```

이런 식으로 axios 인스턴스에 config 객체를 호출할 수 있다.
이는 위에서 설명한 axios(config)와 같은 동작을 한다.

이 방식으로 인증 오류에서 재시도 로직을 깔끔하게 구현할 수 있다.
