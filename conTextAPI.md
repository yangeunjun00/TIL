오늘 배운 것

# conTextAPI

conTextAPI를 알아보기 전 **Props drilling**에 대해 알아보자

## Props drilling

Props drilling은 최상위 컴포넌트에 있는 데이터를 여러개의 하위 컴포넌트로 보낼 때 최하위 컴포넌트에서만 그 데이터를 사용하려고 해도 그 전 그러니까 최상위 컴포넌트와 최하위 컴포넌트 사이에 있는 컴포넌트들은 데이터를 사용하지 않음에도 불고하고 불편하게 데이터를 처리 해줘야 하는 문제이다.

이 문제를 해결하기 위해 React는 conTextAPI를 지원한다.

conTextAPI를 쉽게 설명하면 원하는 데이터를 **전역공간**에 둔다고 생각하면 이해하기 쉽다.

전역공간에 둠으로써 원하는 위치에서 데이터를 쉽게 꺼내서 쓸 수 있다

## 사용 법

### Context 생성

`import {createContext} from 'react';`
`export const themeContext = createContext(null);`

이러면 이제 데이터들을 담을 바구니가 생긴다.

### 제공자(Provider)

`<MyContext.Provider vaulue={{isData,isHello}}>`
`</컴포넌트명>`
`</컴포넌트트명>`
`</MyContext.Provider>`

이러면 Provider로 감싼 컴포넌트들은 isData 와 isHello에 접근 가능하다

### 데이터 꺼내 쓰기

`import {useContext} from 'react';`

`const hi = useContext(myContext);`

이런 식으로 useContext hook을 import해서 인자로 Provider 객체를 넘겨주면 Provider객체의 value에 있는 데이터를 받아와서 사용할 수 있다
