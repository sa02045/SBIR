# Includes()로 존재 여부를 확인하라

- ES2016에 추가된 `includes()` 배열 메서드를 이용해 값이 배열에 존재하는지 확인할 수 있다
- true 또는 false를 return한다

## 예시

- includes() 없이 구현하면 index가 0일때를 고려해줘야한다

```js
const sections = ["shipping"];
function displayShipping(sections) {
  if (sections.indexOf("shipping")) {
    //   배열값의 index가 0이기때문에 false
    return true;
  }
  return false;
}
// 항상 false를 반환
// 배열값이 존재하지만 index가 0이기 때문에 false를 반환한다.
```

```js
const sections = ["contact", "shipping"];

// shipping을 포함여부를 반환한다
function displayShipping(sections) {
  return sections.includes("shipping");
}
```
