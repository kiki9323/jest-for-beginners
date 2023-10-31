# Jest

## Jest 설치

1. 설치

```terminal
npm install --save-dev jest // 개발용 설치
```

---

# API

**[ 예시 ]**

```js
test("Test Title", () => {
  expect(검증할 값).toBe(기대값);
});
```

1. `test` : 테스트 케이스를 정의한다. alias로 `it`을 쓰기도 한다.
2. `expect` : 검증할 값을 넣는다.
3. **Matcher** `toBe` : 기대할 값을 넣는다.

#### 검증할 값

`expect()`

- 주어진 값을 테스트하는데 사용. 검증할 값을 넣어줌.

## Matcher

- 테스트에서 기대값과 실제값을 비교하고 판단하는 함수

#### 기대값

- 예상된 값과 정확하게 일치하는지 테스트

```js
toBe();

// 정확한 값과 데이터 타입을 비교한다.
//
// 원시값 비교 - 숫자, 문자열, 불리언 비교할 때 사용
```

```js
toEqual();
toStrictEqual(); // 보다 엄격함 (strict equality)

// 객체의 경우 재귀적으로 객체를 테스트해야하므로
// 객체의 구조나 속성값이 일치해야 한다.
//
// 깊은 비교를 위해 toStrictEqual을 사용한다.
```

```js
toBeNull();
toBeUndefined();
toBeDefined();

test("null은 null이다.", () => {
  expect(null).toBeNull();
});
```

```js
toBeTruthy();
toBeFalsy();
```

```js
toBeGreaterThan(); // 크다
toBeGreaterThanOrEqual(); // 크거나 같다
toBeLessThan(); // 작다
toBeLessThanOrEqual(); // 작거나 같다
```

```js
toHaveBeenCalledWith(...expectedArgs);

// 올바른 인자들로 호출되었는지를 확인한다.
// = 함수 호출에 사용된 인자들이 예상된 것과 일치하는지 확인.
//
// @params ...expectedArgs - 기대하는 인자들의 배열이나 인자 목록
```

#### Mocking Function : 모의 함수

테스트에서 함수를 흉내내는 mock 함수를 만들 때 사용한다.

실제 함수처럼 동작하지 않지만, 호출 여부와 호출 매개변수, 반환값 등을 추적하고 테스트에서 사용할 수 있게 만들어준다.

**사용 이유**

- 테스트 격리 (isolation)
  : 특정 함수가 의존하는 다른 함수나 모듈을 격리하고 싶을 때 사용한다. 실제 함수를 대체하여 함수 간의 의존성을 없애고, 특정 함수의 동작을 제어한다.

- 호출 여부 확인
  : 함수가 특정 조건에서 호출되었는지 여부 확인, 및 몇 번 호출되었는지 추적한다.

- 반환 값 제어
  : 특정 입력에 대한 반환 값을 강제로 설정.
  이를 통해 반환 값이 다양한 상황에서 어떻게 도작해야 하는지를 테스트한다.

- 함수의 인자 추적
  : 함수가 어떤 인자들과 호출되었는지 추적한다.
  인자가 올바른지 확인하거나 특정 조건에서 어떤 인자로 호출되는지 검증한다.

- 비동기 함수에서의 사용
  : 비동기 함수의 콜백 함수를 mock 함수로 대체하여 테스트한다.

```js
jest.fn();
```
