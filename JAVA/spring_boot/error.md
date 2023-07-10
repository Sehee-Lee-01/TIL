# Error 해결

### 문제1: 프로젝트를 생성하고 보니 계속 Gradle 버전이 맞지 않는다고 나왔다!!

- 다른 IDE를 설치하기가 번거롭기도 하고 관리하기가 불편하여 기존에 사용하던 Visual Studio Code로 Spring Boot 환경을 세팅하기로 했다. 이 과정에서 버전 문제가 있었다.

→ 원인: 알고보니 gradle 버전(7.6)과 jdk 버전(20)이 권장되지 않는 조합이었던 것이다! 

- 참고: [https://docs.gradle.org/current/userguide/compatibility.html](https://docs.gradle.org/current/userguide/compatibility.html)

→ 해결:  jdk 17 버전을 설치하여 문제를 해결할 수 있었다!

- LTS 버전 다운 받자,,, 버전은 하라는 대로 하자,,,

→ 해결2: gradle 버전을 바꾸는 방법도 있다.(근데 바꾸기가 어렵다,,,)

- 참고: [https://yearnlune.github.io/java/change-gradle-wrapper-version/#gradle-wrapperproperties](https://yearnlune.github.io/java/change-gradle-wrapper-version/#gradle-wrapperproperties)
- 그런데 vscode에서는 잘 안되는 것 같았다.
    - 나중에 보니 vscode 실행 jdk 버전은 17이지만 내가 테스트한 환경은 20버전이었다,,바보,,,

### 문제2: vscode 에서 프로젝트를 만들고 build.gradle에서 디펜던시를 추가하려고 하니 계속 오류가 발생했다.

→ 원인: 잘 모르겠다. 계속 버전 관련 문제가 발생하다보니 버전 문제인 것 일수도 있겠다는 개인적인 의견… 그리고 vscode 자체가 java에게 적합한 ide는 아니라는 글이 있었다.

→해결: 프로젝트를 생성할 때 나오는 초기 디펜던시 추가에서 필요한 것을 다 추가하였다. 그러니 build.gradle에도 추가가 되었고 정상적으로 작동이 되었다.

### 문제3: lombok 확장자를 설치하고 테스트를 진행했는데 아무 문제가 없는 세팅이라고 생각했지만 오류 발생.

→ 원인: vscode 롬복 관리에서 자동으로 설정이 되지 않는 부분이 있는 것 같다,,, 

- 참고: https://github.com/projectlombok/lombok/issues/1323
- 참고2: [https://github.com/redhat-developer/vscode-java/wiki/Lombok-support](https://github.com/redhat-developer/vscode-java/wiki/Lombok-support)

→ 해결: 바로 위 링크 사진처럼 ‘{}’ 표시를 누르고 extension version으로 바꾸어 주었다. reload 후 다시 실행해보니 다행히 실행이 된다. 바로 안될 수도 있다. 껐다가 켜보자.