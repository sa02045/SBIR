# push()메서드 대신 펼침연산자로 원본 변경을 피하라

- 원본 배열을 조작하는 것인 예상치 못한 결과, 버그를 발생시킨다

- 함수형 프로그래밍처럼 부수효과와 조작이 없는 코드를 작성해야한다.

- push() 메서드는 원본 배열을 조작해서 새로운 항목을 추가한다

- 우리는 `순수함수`를 만들기 위해 노력해야한다

```js
const titles = ["Moby Dick", "White Teeth"];
// titles.push('The Conscious Mind')
const moreTitles = [...titles, "The Conscious Mind"];
```

배열의 시작 부분에 항목을 추가하고 싶다면?

```js
const moreTitles = ["The Conscious Mind", ...titles];
```
