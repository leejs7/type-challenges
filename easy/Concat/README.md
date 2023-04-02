# type-challenges : Concat

## Array.concat유형 시스템에서 JavaScript 기능을 구현하십시오 . 
## 유형은 두 개의 인수를 사용합니다. 출력은 ltr 순서로 입력을 포함하는 새로운 배열이어야 합니다.

```ts
// 예시 코드
type Result = Concat<[1], [2]> // expected to be [1, 2]
```

### 문제 풀이

#### 1. 두 인자의 타입이 정해져 있지 않습니다.

타입이 정해져 있지 않은 배열이므로 "extends unknown[]" 또는 "extends any[]" 로 두 입력 값을 전달받도록 구현합니다.
```ts
// unknown[] 사용
type Concat<T extends unknown[], U extends unknown[]> = ...
// any[] 사용
type Concat<T extends any[], U extends any[]> = ...
```

#### 2. 두 입력값이 순서대로 저장된 새로운 배열 반환하도록 합니다.

스프래드 연산자를 사용해서 두 제네릭의 원소들을 새로운 하나의 배열로 생성해 반환합니다.
입력값이 순서대로 포함된 새로운 배열을 반환하기 위해 T, U 순서로 배열에 저장합니다.
```ts
// unknown 사용
type Concat<T extends unknown[], U extends unknown[]> = [...T, ...U];
// any 사용
type Concat<T extends any[], U extends any[]> = [...T, ...U];
```

### any[]과 unknown[]의 차이점
두 개의 타입 별칭은 Concat 이라는 이름으로, 두 개의 배열 타입을 합쳐서 하나의 배열 타입으로 만드는 역할을 합니다.

하지만, 첫 번째 타입 별칭 Concat<T extends any[], U extends any[]>에서는 제네릭 타입 매개변수 T와 U가 any[]로 제한되어 있습니다. 
이는 T와 U가 배열 타입이어야 한다는 것을 의미합니다. 그러므로 이 타입 별칭은 T와 U의 타입 매개변수가 배열 타입임을 보장하며, 배열에 있는 요소들의 타입에 제약을 두지 않습니다.

반면, 두 번째 타입 별칭 Concat<T extends unknown[], U extends unknown[]>에서는 T와 U가 unknown[]로 제한됩니다. 
이는 T와 U가 배열 타입이어야 한다는 것을 의미하지만, 배열 요소의 타입이 unknown일 수 있다는 것을 의미합니다. unknown은 타입 안정성을 유지하기 위해 TypeScript 3.0에서 도입된 타입입니다. 
이는 모든 타입의 하위 타입이며, 다른 타입과 호환되지 않습니다. 따라서 이 타입 별칭은 T와 U의 타입 매개변수가 배열 타입임을 보장하면서도, 배열에 있는 요소들의 타입에 대한 제약을 두지 않습니다.

즉, 첫 번째 타입 별칭은 제네릭 타입 매개변수 T와 U에 대해 배열 타입만 허용하고, 배열에 있는 요소들의 타입을 제약하지 않습니다. 
두 번째 타입 별칭은 제네릭 타입 매개변수 T와 U에 대해 배열 타입만 허용하며, 배열에 있는 요소들의 타입에 대한 제약을 두지 않지만 unknown 타입을 사용합니다.