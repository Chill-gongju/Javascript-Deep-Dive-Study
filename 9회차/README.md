# 46장 제너레이터와 async/await

- 제너레이터 함수란 무엇이며 일반 함수와의 차이점은 무엇인가요?
    - 종훈리: 제너레이터 함수란 코드를 일시 중지했다가 다시 실행할 수 있는 함수를 말합니다.
    - 일반 함수랑 다른 점은 1: 함수 호출자에게 함수 실행 제어권을 양도할 수 있다. 2: 함수 호출자와 함수의 상태를 주고받을 수 있다. 3: 함수를 호출하면 제너레이터 객체를 반환한다.
- 제너레이터 함수는 어떤 키워드로 선언하나요?
    - 이소: `function*`
- 제너레이터 객체의 next, return, throw 메서드는 각각 어떤 역할을 하나요?
    - 채온:
        - next: yield 지점까지 실행하고 일시 중지
        - return: 호출 시 제너레이터 종료, 종료 값 전달
        - throw: 현재 yield 지점에서 예외 발생
- 제너레이터를 비동기 처리에 사용하는 방식은 무엇이고, 그 한계는 무엇인가요?
    - 히범: 제너레이터를 프로미스와 함께 사용하면 된다.
    표준 내장 API가 아니다! 가독성 매우매우매우 떨어진다! 병렬처리가 어렵다! 디버깅도 어렵다! 에러 핸들링 어렵다! 일맥상통하는 내용! 끄읏!
- async/await은 어떤 방식으로 동작하며, 제너레이터와 비교했을 때 장점은 무엇인가요?
    - 종훈리:  async/await은 제너레이터랑 비슷하게 비동기 처리를 동기처럼 구현하는 방식, 동작 방식은 프로미스를 기반으로 동작해서 프로미스가 settled 상태가 될 때까지 기다린 후 await을 하면  처리 결과가 반환하는 방식으로 동작합니다. / 제너레이터는 가독성이 안좋고, 병렬처리 어렵고 등등 문제가 있는데 async/await은 훨씬 더 간단하게 비동기를 처리할 수 있습니다.
- async/await에서의 에러 처리는 어떻게 하나요?
    - 이소: try{ }…catch { }문  / catch문을 사용하지 않으면, async 함수가 발생한 에러를 reject하는 프로미스를 반환합니다

---

# 47장 에러 처리

- try...catch...finally 문은 각각 어떤 역할을 하나요?
    - 채온:
        - try: 에러가 발생할 가능성이 있는 코드
        - catch: 에러가 발생했을 때 실행할 코드, 생략하지 않음
        - finally: 에러 발생 여부와 상관 없이 항상 실행되는 코드, 생략 가능
- Error 객체를 사용하는 이유는 무엇인가요?
    - 히범: 에러에 대한 구조화된 정보를 전달할 수 있다! / 정확한 예외 추적 및 디버깅이 가능하다! / 일관된 에러 처리 흐름을 구성할 수 있다. / 사용자 정의 에러 클래스를 생성 할 수 있다.
- throw 문은 언제 사용하고 어떤 효과를 내나요?
    - 종훈리:  throw은 에러를 던지는 역할을 합니다. try…catch문이 있으면 catch문에서 에러를 던진다던지 예외 처리를 할 때 사용합니다.

---

# 48장 모듈

- 자바스크립트에서 모듈이란 무엇이며 왜 필요한가요?
    - 이소: 모듈: 재사용 가능한 코드들이다! 독립적인 스코프를 갖게 하기 위해..? 그니깐 전역 변수가 중복되는 걸 방지해줍니다? !재사용성 유지보수성!~~~
- ES6 이전에는 자바스크립트에서 모듈을 어떻게 관리했나요?
    - 채온: 파일 스코프 없이 전역으로 공유되도록 관리를 해서 변수가 중복되는 문제 발생
- export와 import의 기본 문법을 설명해주세요.
    - 히범: export → named, default  → 전자는 한 파일에서 여러개 export 가능하다! 후자는 한 파일에 한개만 가능하다!
    import → 네임드 디폴트 → 전자는 임폴트할 모듈의 이름을 중괄호로 싸서 호출? 해야함. 벗 후자는 그런거 필요없음!
    전체 import! import * as 별칭 from “블라블라” 할 수도 있음!
- script 태그에서 모듈을 로딩하기 위해 필요한 설정은 무엇인가요?
    - 종훈리:  script 태그에 type=”module” 어트리뷰트를 추가하면 된다.
        
        ```jsx
        <script type = "module" src = "app.js"></script>
        ```
        

---

# 49장 **Babel과 Webpack을 이용한 ES6+/ES.NEXT 개발 환경 구축**

- Babel은 무엇이며 어떤 역할을 하나요?
    - 이소: 최신 사양의 코드를 옛날 브라우저에서도 동작 가능하게 ES5의 코드로 바꿔줍니다!
- Webpack은 무엇이며 어떤 역할을 하나요?
    - 채온: 여러 자바스크립트 모듈, 이미지, css 등을 하나의 번들 파일로 묶어줍니다. 모듈 로더 없이 브라우저에서 실행 가능
- Webpack을 사용했을 때 코드 번들링이 프론트엔드 성능에 미치는 긍정적 영향은 무엇인가요?
    - 히범: 웹팩! 모듈 번들러죠! 의존 모듈이 하나의 파일로 번들링되무ㅡ로 별도의 로더가 필요없음!!!
    - 여러 개의 JS 파일을 하나로 번들링하므로 HTML 파일에서 script 태그로 여러개의 JS 파일을 로드해야하는 번거로움도 사라지죠! 이래서 씁니다! 끄읕!@@

<br/>
<br/>



끝!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

굿 👍👍👍

ㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎ

😇

🤗

🏊🏻‍♂️

![](https://media1.giphy.com/media/v1.Y2lkPTc5NDFmZGM2M2loamR0dTc0Z3d1bTh2NnhuZXpjMGk5NHhiZ2t3YmVmaGZpYnNkYSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/APHFMUIaTnLIA/giphy.gif)

![](https://media1.giphy.com/media/v1.Y2lkPTc5NDFmZGM2MnR5enE2b2ZhMDJoZGVvb3J4MXBnMzgzZ2RyZTByMHkzazllOG4zNSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/11sBLVxNs7v6WA/giphy.gif)

![](https://media2.giphy.com/media/v1.Y2lkPTc5NDFmZGM2N3M1YXU1NWdueWY2cDN3ZG9wYmJnNjZjbmlhaWY5czl4NG9iNW1oNiZlcD12MV9naWZzX3NlYXJjaCZjdD1n/QBC5foQmcOkdq/giphy.gif)

