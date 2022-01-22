# TIP3. 블록 유효 범위 변수로 정보를 격리하라

- if문 또는 for문 내부에서 `let` 변수를 선언하면 블록 외부에서는 그 변수에 접근할 수 없다.
- `var`로 할당한 변수는 함수 유효 범위(어휘적 유효 범위)를 지닌다

```js
function addClick(items) {
  for (var i = 0; i < items.length; i++) {
    items[i].onClick = function () {
      return i;
    };
  }
  return items;
}
const example = [{}, {}];
const clickSet = addClick(example);
clickSet[0].onClick();

// 1을 예상했지만 2가 출력된다
```

- 호출한 시점의 i값(2)를 반환합니다. 설정한 시점값이 아닙니다.

## 정리

1. var는 사용하지말자. 대신 let을 사용하자
