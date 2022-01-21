# let과 const로 유효 범위 충돌을 줄여라

- 변수가 반드시 재할당해야하는 경우 `let`을 사용할 수 있다.
- var는 `lexical scop`를 따르고, let은 `block scop`를 따른다.

```js
function getLoewsPrice(item) {
  var count = item.inventory;
  var price = item.price;
  if (item.salePrice) {
    var count = item.saleInventory;
    // 할인 중이고 할인 재고가 있다면 할인 가격으로
    if (count > 0) {
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

// 같은 블록스코프 내에서
let b = 2;
let b = 4; // X 재선언
b = 3; // O 재할당
```

# 정리

- const를 사용하되, 반드시 재할당이 일어나는 경우에는 let을 사용하자
- var는 `lexical scop`, `함수 스코프`를 따르고 let과 const는 `블록 레벨 스코프`를
- let으로 var이 가지고 있는 재선언, 재할당으로 일어날 수 있는 버그를 막을 수 있다
