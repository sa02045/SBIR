# TIP1. 변수 할당으로 의도를 표현하라

## TIP 1 const로 변하지 않는 값을 표현하라

- 기본적으로 `const`를 사용한 변수선언을 하라!
- 그 이유는 다음과 같다

### 예시

첫 번째 코드

```js
const taxRate = 0.1;
const total = 100 + 100 * taxRate;

// 생략...

     price = item.salePrice;
    }
  }

  //   count가 재할당되버리기 때문에 버그발생!
  if (count) {
    return price;
  }

  // 재고가 없으면 0을 반환
  return 0;
}
```

- 만약 할인 중이지만 할인 재고가 없는 경우 버그를 발생시킴!
- var로 선언했기 때문에 블록 스코프 if문에서 변수 `count`의 재할당이 일어남
- `let`으로 블록 스코프로 선언해서 버그를 피하자

```js
function getLoewsPrice(item) {
  let count = item.inventory;
  let price = item.price;
  if (item.salePrice) {
    //   let은 블록스코프 범위를 가지기 때문에 아리 count는 if문 안에서만 사용됨
    let count = item.saleInventory;
    if (count > 0) {
      price = item.salePrice;
    }
  }
  if (count) {
    return price;
  }

  return 0;
}
```

- `var`은 재선언 `let`과 `const`는 재선언이 불가능

```js
var a = 1;
var a = 3; // O

// 같은 블록스코프 내에return total;
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

## 정리

1. 자바스크립트에서는 var,let,const로 변수를 선언할 수 있지만 cosnt를 기본으로 하자!
2. 상수 선언이라는 것은 개발자로 하여금 그 변수에 대한 이해를 높여준다(예측할 수 있게 한다)
3. const로 선언된 변수라도 불변값이 아닐 수 있다(ex.배열)
