# type-challenges : Get Return Type

## 내장 ReturnType<T>제네릭을 사용하지 않고 구현하십시오.

```ts
// 예시 코드
const fn = (v: boolean) => {
  if (v)
    return 1
  else
    return 2
}

type a = MyReturnType<typeof fn> // should be "1 | 2"
```

### 문제 풀이

```ts
type MyReturnType<T> = T extends (...args: any[]) => infer R ? R : never;
```

코드에서 사용된 MyReturnType&#60;T&#62; 제네릭 타입은 함수의 반환 타입을 추론하는 역할을 합니다.

제네릭 타입 T가 함수 타입인 경우, T extends (...args: any[]) => infer R 부분이 매치됩니다. 여기서 ...args는 함수의 매개변수 타입들을 표현하는 나머지 인수들(rest parameter) 입니다. infer R은 타입 추론을 통해 추론된 함수의 반환 타입을 저장할 타입 변수입니다.

extends 키워드를 사용하여 T가 함수 타입인지를 확인하고, 함수 타입인 경우에는 반환 타입을 R에 저장합니다. 이 때, R은 infer 키워드를 사용하여 추론된 타입이므로, T extends (...args: any[]) => R처럼 사용할 수 있습니다.

만약 제네릭 타입 T가 함수 타입이 아닌 경우, never 타입을 반환합니다. 이는 반환 타입을 추론할 수 없는 경우를 대비하여 사용됩니다.

따라서 MyReturnType	&#60;typeof fn&#62;은 fn 함수의 반환 타입인 1 | 2와 일치합니다. typeof fn은 함수 타입을 나타내며, 이 함수는 boolean 값을 받아 1 또는 2를 반환하므로, MyReturnType	&#60;typeof fn&#62;은 1 | 2입니다.
