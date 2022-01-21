# 변수 할당으로 의도를 표현하라

## TIP 1 const로 변하지 않는 값을 표현하라

- 기본적으로 `const`를 사용한 변수선언을 하라!
- 그 이유는 다음과 같다

### 예시

첫 번째 코드

```js
const taxRate = 0.1;
const total = 100 + 100 * taxRate;

// 생략...

return total;
```

두 번째 코드

```js
var taxRate = 0.1;
var total = 100 + 100 * taxRate;

// 생략...

return total;
```

- 첫 번째 코드에서는 total은 상수이며 재할당할 수 없다는것을 알 수 있음
- 두 번째 코드에서는 total을 `예측할 수 없음` (저자의 말로는 믿을 ㅅ ㅜ없는 값)

- `const`에 할당한 값은 `불변값`이 아닐 수 도 있다! (객체,배열같은 경우)

```js
const discountable = [];
for (let i = 0; i < car.length; i++) {
  if (cart[i].discountAvailable) {
    discountable.push(cart[i]);

    // discountable은 const로 선언됬음에도 불구하고 push메서드로 값을 변경할 수 있다
  }
}
```

- 위와 같이 const로 선언된 변수는 최대한 조작을 피하도록 해야한다

# 정리

1. 자바스크립트에서는 var,let,const로 변수를 선언할 수 있지만 cosnt를 기본으로 하자!
2. 상수 선언이라는 것은 개발자로 하여금 그 변수에 대한 이해를 높여준다(예측할 수 있게 한다)
3. const로 선언된 변수라도 불변값이 아닐 수 있다(ex.배열)
