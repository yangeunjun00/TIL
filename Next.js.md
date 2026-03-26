오늘 배운 것

# Next.js

<hr>

**Nextjs란?** 자바스크립트 프레임 워크의 한 종류로 현재 자주 쓰이는 자바스크립트 라이브러리인 React에서는 불편했던 기능들을 쉽게 사용할 수 있어서 많은 사용자가 이용한다.

## 왜 쓸까?

React에서는 라우팅을 하려면 react-router, react-router-dom을 사용해야 했지만, Next.js에서는 그냥 폴더 하나만 생성하면 자동으로 그 엔드포인트에 해당하는 페이지를 만들 수 있다

또한 이미지태그를 사용 할 때 이미지 로딩이 지연되는 **Lazy loading** 문제를 해결할 수 있다.

그리고 CSR(Client Side Rendering)만 되던 React 와 달리 SSR(Server Side Rendering)을 통해 보안 문제 및 페이지 로딩 지연 문제를 해결할 수 있다.

### 사용 법

터미널에

```
npm creat-next-app
```

입력 시 next 프로젝트 생성 됨

```
npm run dev
```

프로젝트 실행

프로젝트 생성 시 프로젝트 구조는 다음과 같다

![alt text](image.png)

여기서 layout.tex 는 자식 페이지들의 부모가 되는 페이지이다. 이 페이지 안에 넣는 코드는 자식 페이지에서도 보이게 된다.
그래서 계속 보여져야하는 탑 컴포넌트등을 넣는다.

### Dynamic routing

다이나믹 라우팅은 Next.js에서 제공하는 동적인 URL 생성 방식이다.

만약 http://..../home 이런 URL이 필요하다면

app폴더 안에서 home이라는 이름의 폴더를 생성하고 그 안에 page.tsx를 생성하면 그 home/page.jsx가 동적으로 /home 엔드포인트를 갖게되는 페이지가 된다.

### Linking

Linking은 기존 <a>태그를 사용해서 페이지를 이동하는 방법과 비슷하다 <Link> 컴포넌트를 이용해서 페이지를 이동하는 방식이다.
이 방법은 페이지를 로드할 때 필요한 자원을 가져오기 때문에 사용자 경험을 개선할 수 있다.
이를 **프리패칭** 이라고 한다.

```
import Link from "next/link"

function home(){
    return(
        <div>
            <Link href="/about"></Link>
            <a>어바웃 페이지로 이동!</a>
        </div>
    );
}

```

### client component

Next.js에서는 기본적으로 컴포넌트를 SSR으로 렌더링 한다.
그러나 'use client' 키워드를 통해 CSR을 하는 컴포넌트를 만들 수 있다.

```
'use client'

function home(){
    return(
        ...
    );
}
```

이러면 home 컴포넌트는 CSR로 렌더링 되는 컴포넌트가 된다.
