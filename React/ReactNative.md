오늘 배운 것

# reactNative

reactNative란?

react기반의 코드를 통해 iOS 와 Android 환경에서 앱을 만들 수 있는 크로스 플랫폼 프레임워크이다.

reactNative와 똑같이 iOS, Android에서 앱을 만들 수 있는 크로스 플랫폼인 **flutter** 라는 프레임워크가 있는데 둘은 무슨 차이가 있을까?

## 화면을 그리는 방식

reactNative의 경우 Bridge 모델을 사용해서 화면을 그린다.

JS 파일이 실행 되면 iOS/Android 에서 네이티브 위젯을 호출한다.

즉, 실제 운영체제의 UI 구성요소를 그대로 빌려 쓴다.

그러나 flutter의 경우 운영체제의 위젯을 빌리지 않고 **자체 렌더링 엔진**을 사용한다.

그래서 모든 기기에서 정확한 UI를 보여줄 수 있다.

## 언어

reactNative의 경우 JS를 사용하며 react와 정말 유사한 코드구조를 지닌다.

flutter에서는 Dart라는 언어를 사용한다.

## 장단점

reactNative는 **CodePush** 기능을 통해 앱 심사를 거치지 않고 JS 코드를 즉시 업데이트 할 수 있다.

flutter는 자체 렌더링 엔진을 통한 부드럽고 프레임 높은 애니메이션을 구현 할 수 있다.
