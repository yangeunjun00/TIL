### 시작하며

> 오늘은 웹 개발을 해보면 한번 쯤 접해보게 되는 디자인 패턴 **MVC**와 MVC에서 파생된 **MVVM**을 알아보겠습니다.

<hr>

## 디자인 패턴이란?

> 소프트웨어 설계에서 생기는 문제들을 일반적으로 재사용 가능한 **해결책**이다.

디자인 패턴은 코드를 구조화 시켜 개발효율성 과 유지보수성을 높혀준다.

앞으로 설명할 **MVVM**가 바로 이 디자인 패턴 중 하나이다.

# MVVM

**M**odel, **V**iew, **V**iew**M**odel의 약자이다.

이 패턴에서도 Model 과 View는 다른패턴과 동일한 역할을 수행한다.

## 1. 구조

> - **Model** (애플리케이션에서 실제로 사용되는 데이터 및 데이터 처리하는 부분)

- **View** (사용자에게 보여지는 실제 UI)
- **ViewModel** (View에게 데이터를 보내주기 위한 Model이자 View를 위해 데이터를 가공하는 부분)

## 2. 동작과정

> - 사용자의 action을 View에서 받아들임

- View에서 **Command 패턴**으로 ViewModel에게 action 전달
- ViewModel에서 action에 맞는 데이터를 Model에게 요청
- Model에서 ViewModel에게 데이터 응답
- ViewModel에서 데이터 가공 및 저장
- View에서 ViewModel과 **Data Binding**을 통해 화면 제작

여기서 말하는 **Command 패턴**은 리소스 요청을 **객체형태로 캡슐화**하여 사용자의 요청을 나중에도 처리할 수 있도록 메서드 이름, 매개변수 등을 저장, 로깅, 취소등을 통해 관리하는 패턴이다.

또 **Data Binding** 같은 작업을 하지만 수행하는 역할이 다른 두 개의 작업을 묶어 동기화 하는 기술이다.

## 3. 특징

MVVM 패턴은 Command 패턴과 Data Binding을 통해 이루어져있다.
그로 인해 View 와 ViewModel 사이 의존성을 없앨 수 있다.
View 와 ViewModel은 n:1의 관계이다.
