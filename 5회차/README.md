
### 콜백 함수 내부의 this 문제란?

일반 함수에서 콜백을 쓸 때 this가 바뀌는 문제!

```jsx
const counter = {
  count: 0,
  increase() {
    setTimeout(function () {
      console.log(this.count); // ❌ undefined (또는 window.count)
    }, 1000);
  },
};

counter.increase();
```

### 해결 방법

1. this를 변수에 저장
2. bind로 명시적 바인딩
3. 화살표 함수 사용

```jsx
const counter = {
  count: 0,
  increase() {
    setTimeout(() => {
      console.log(this.count); // ✅ 0
    }, 1000);
  },
};
```

---

# ⭐️ Quiz

### 26장 ES6 함수의 추가 기능

- ES6 이전 사양에서의 함수의 특징은?
    - 종훈리: 사용 목적에 따라 구분이 없어서 호출 방식에 제약이 없다 → 생성자 함수로 생성하지 않아도 생성이 되기 때문에 실수 유발 가능, 성능에도 좋지 않다
- ES6 사양에서의 메서드의 특징은?
    - 이소: 인스턴스를 생성할 수 없는  non-constructor? → prototype 프로퍼티 x, 프로토타입 생성 x
- 화살표 함수와 일반 함수의 차이점은?
    - 히범
        1. non-constructor
        2. 중복 매개변수 선언 못함.
        3. 함수 자체 this argument super [new.target](http://new.target) 바인딩을 갖지 않음.
- rest 파라미터란 무엇이며 어떤 장점을 가지나요?
    - 채온: 함수에 전달된 인수들의 목록을 배열로 전달, `…변수명` / 가독성, 효율성 좋음
- 함수 호출 시 매개변수의 개수만큼 인수를 전달하는 것이 원칙이지만 그렇지 않은 경우에도 에러가 발생하지 않는 이유는 무엇인가요?
    - 종훈리: 자바스크립트 엔진이 체크하지 않기 때문입니다. 인수 전달되지 않은 매개변수는 undefined

### 27장 배열

- 자바스크립트의 배열과 일반적인 배열의 차이점은?
    - 이소: 자바스크립트 - 메모리 크기가 다 다를 수 있고, 연속적이지 않을 수 있어서 희소 배열입니다. 그리고 배열의 요소는 모든 타입을 가질 수 있습니다 / 일반 배열 - 동일한 크기의 메모리와 연속적으로 이어져 있습니다
- 희소 배열이 뭐에요?
    - 히범: 배열의 요소가 연속적으로 있지 않고 중간 중간 비어있는 이상한 배열을 희소 배열이라 하고 중요한건 그렇기 때문에 언제나 length로 반환받는 값이 실제 배열에 들어있는 요소의 갯수보다 큼! 그러면 개발자가 실수 하기 딱! 좋겠지? 그러므로 희소배열은 사용을 지양하자!
- `Array.from()` 과 `Array.of()`의 차이점은?
    - 채온: `Array.from()` 유사 배열 객체, 이터러블 객체를 배열로 변환 / `Array.of()` 전달된 인자를 배열 요소로 가지는 배열을 생성한다
- `Array.isArray({ length: 3 })`는 true를 반환한다. (OX)
    - 종훈리: 배열이면 true, 아니면 false이기 때문에 false를 반환할 듯 합니다.
- 배열의 `length`는 실제 요소 개수를 의미하나요?
    - 이소: 아니오 / 희소 배열일 경우, 실제 요소 개수보다 클 수 있기 때문에
- 배열 메서드 중 원본을 변경하는 것과 변경하지 않는 것을 구분해온나.
    - 히범
        - 원본 변경 : pop push shift unshift splice fill sort reverse…
        - 복사본 반환 : concat join map filter…slice flat 이정도?
- `map`과 `forEach`의 차이점은?
    - 채온: `map` 배열 요소를 변환하여 새로운 배열을 반환 / `forEach` 단순 순회만 해서 반환값이 없음, 콜백 함수 실행
- `reduce()` 메서드의 동작 원리를 설명해주세요.
    - 종훈리: 콜백 함수의 반환값을 다음 순회 시 콜백 함수의 첫 번째 인수로 전달하면서 콜백 함수를 호출하여 하나의 결과값을 만들어 반환합니다.
- `splice(2, 1, 10)`의 의미는?
    - 이소: [1, 2, 3, 4] → [1, 2, 10, 4]
- `filter()` 메서드는 무엇을 반환하는가?
    - 히범: 콜백함수의 리턴값이 true인 요소로만 이루어진 새로운 배열을 만들어서 반환해줌!
- `every()`는 배열이 빈 경우 항상 `false`를 반환한다. (OX)
    - 채온: X, true 반환, 빈 배열에서는 모든 요소가 조건을 만족한다고 간주

### 28장 Number

- `Number.isNaN`과 `isNaN`의 차이는?
    - 종훈리: `Number.isNaN` 메서드, `isNaN` 전역 함수, `isNaN` 빌트인 전역 함수는 전달받은 인수를 숫자로 암묵적 타입 변환을 해서 검사를 수행하지만, `Number.isNaN` 은 메서드니까 타입 변환하지 않는다.
- `Number.isFinite("10")` 의 결과는?
    - 이소: 타입 변환을 하지 않아서 false (유한수이면 true)
- `Number.isNaN(NaN)` 은 true를 반환한다 (OX)
    - 히범: O! (isNaN은 이거 NaN임? 물어보는거임!)

### 29장 Math

- `Math.floor()`, `Math.ceil()`, `Math.round()` 차이?
    - 채온: `Math.floor()` 소수점 이하 내림 / `Math.ceil()` 소수점 이하 올림 / `Math.round()` 소수점 이하 반올림
- `Math.max()`에 배열을 전달하려면?
    - 종훈리: const arr = [1, 2, 3] → Function.prototype.apply 메서드 또는 스프레드 문법을 사용해야 한다. Math.max(…arr); // …

### 30장 Date

- `new Date()`와 `Date.now()` 차이는?
    - 이소: 날짜 객체 생성, 생성자 함수, 현재 시간을 나타냅니다 / 시간을 나타냅니다……
- `getMonth()` 메서드의 반환값은 1월일 때 몇인가?
    - 히범: 0! 너무 쉽다!
- 날짜 포맷을 변환하려면 어떤 메서드를 사용할 수 있을까요?
    - 채온: `toLacaleDateString`, `toISOString`, `toDateString`

끝~

너무 좋다
