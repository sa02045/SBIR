# TIP2. let과 const로 유효 범위 충돌을 줄여라

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
 서
let b = 2;
let b = 4; // X 재선언
b = 3; // O 재할당
```

## 정리

- const를 사용하되, 반드시 재할당이 일어나는 경우에는 let을 사용하자
- var는 `lexical scop`, `함수 스코프`를 따르고 let과 const는 `블록 레벨 스코프`를
- let으로 var이 가지고 있는 재선언, 재할당으로 일어날 수 있는 버그를 막을 수 있다
