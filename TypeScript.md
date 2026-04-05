오늘 배운 것

# TypeScript

TypeScript란 JavaScript에서 변수에 정적타입을 추가하는 문법이 있는 프로그래밍 언어이다.

### 왜 쓸까

JavaScript는 컴파일이 되지 않는 프로그램이다.
그래서 프로그램이 실행 하고 에러가 났을 때 비로소 잘못 된 것을 알 수 있다.

그러나 TypeScript를 사용할 시 런타임 전에 ts파일이 js파일로 변환되는 과정에서 컴파일을 해서 어떤 에러가 났는지 알 수 있다.
또한 타입의 존재로 인해 IDE에서 자동완성, 리팩토링 시 안정성(어디가 에러인지 알 수 있음) 등등 여러 장점이 있다.

### 사용 방법

npm 사용 시

터미널에
`npm i -D typescript `

위 명령어를 입력하게 될 시
TypeScript 개발 의존성 설치를 하게 된다.

설치가 되었다면 `node_modules` 폴더와 생기게 되고 `package.json` 안의 `devDependencies` 에 본인이 설치한 TypeScript의 버전을 보여준다.

그런다음

`npx tsc --init`

위 명령어를 입력 시 `tsconfig.js` 파일이 생성된다.
이 파일은 TypsScript가 프로젝트를 어떻게 컴파일 할 지 설정하는 파일이다.

이 파일 안에는 컴파일 대상, 모듈 방식, 타입 검사 수준 등 TypeScript의 핵심설정이 들어간다.

`npm tsc`

위 명령어 입력 시 .ts파일을 .js파일로 변환한 새 .js 파일을 생성한다.

### 타입 지정

```
const hi: string = "안녕하세요";
```

이렇게 변수 옆에 콜론 과 함께 타입을 지정해줄 수 있다.

### interface

```
interface obj{
    id: number,
    name: string,
    email?: string, // ?를 붙히면 있어도 되고 없어도 되게 된다.
};



const people: obj = {id: 1, name: "김철수"};  // email이 없어도 에러가 나지 않음


```

### type

interface와 동일한 동작을 하나 문법이 조금 다르다.

```
type obj={
    id: number,
    name: string,
}
```

### 제네릭

```
function hi<T>(value: string): T[]{
    return [value];
}


hi<string>("안녕");
```

### 타입 상속

```
interface menu{
    name:string,
    price:number,
};


interface Bestmenu extends menu{

};
```

이러면 Bestmenu 타입에서 menu에 있는 타입들을 사용할 수 있다.

```
type menu={
    name:string,
    price:number
}

type Bestmenu = menu &{

}
```

type의 경우 이렇게 하면 된다.
