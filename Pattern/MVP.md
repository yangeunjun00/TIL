### 시작하며

오늘은 웹 개발을 해보면 한번 쯤 접해보게 되는 디자인 패턴 **MVC**와 MVC에서 파생된 **MVP**에 대해 알아보겠습니다.

<hr>

## 디자인 패턴이란?

> 소프트웨어 설계에서 생기는 문제들을 일반적으로 재사용 가능한 **해결책**이다.

디자인 패턴은 코드를 구조화 시켜 개발효율성 과 유지보수성을 높혀준다.

앞으로 설명할 **MVP**가 바로 이 디자인 패턴 중 하나이다.

# MVP

**M**odel, **V**iew, **P**resenter 로 이루어져 있다.

여기서 Model 과 View는 MVC에서와 같은 역할을 한다.

## 1. 구조

그러나 **Presenter**는 MVC의 Controller와 사뭇 **다른** 역할을 지닌다.

Controller는 사용자의 action을 받아들이고 Model을 업데이트 시켰다면
**Presenter**는 View에서 온 요청을 통해 Model을 가공하여 View에 다시 전달을 하는 View와 Model의 중간 매체라고 할 수 있다.

## 2. 동작 과정

> - 사용자의 action을 View에서 받아들임

- View에서 Presenter에게 요청
- Presenter에서 Model에게 요청
- Model에서 Presenter에게 요청에 맞는 응답 반환
- Presenter에서 View로 응답 전달
- View에서 받은 데이터 UI로 렌더링

## 3. 특징

Presenter는 View 와 Model의 인스턴스를 가지고 있어 둘을 연결해주는 역할을 한다.

MVC에서 있던 View 와 Model의 높은 의존성 문제를 해결한 디자인 패턴이다.

Presenter 와 View가 1:1로 대응한다.

그러나 프로젝트의 규모가 커질수록 View 와 Presenter 사이의 의존성이 높아지게 된다.(View 와 Presenter 사이에서 데이터를 주고 받기 때문)
