# type-challenges : Exclude

<내장 제네릭 Exclude<T, U>를 구현>

```ts
// 예시 코드
type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
```

union 타입에서 특정 한 것 들을 제외하고자 하는 것이 목적이다.
(타입 U에 포함되어 있지 않은 타입 T의 요소 반환)

<a href="https://www.typescriptlang.org/docs/handbook/2/conditional-types.html#distributive-conditional-types">typescript의 Distributive Conditional Types 문법을 사용</a>


```ts
type MyExclude<T, U> = T extends U ? never : T;
```

타입 T를 순회하며 U의 요소가 포함되어 있다면 never 리턴하고 
타입 T에 U의 요소가 포함되어 있지 않다면 T 리턴합니다.