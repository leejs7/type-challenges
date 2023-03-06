# type-challenges : Length of tuple

```ts
type tesla = ['tesla', 'model 3', 'model X', 'model Y']
type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

type teslaLength = Length<tesla>  // expected 4
type spaceXLength = Length<spaceX> // expected 5
```

튜플을 예상하고 그 길이를 반환하는 유형을 만들어 봅니다.

```ts
type Length<T extends readonly unknown[]> = T['length']
```

Type은 길이가 변경되지 않는 알 수 없는 유형의 배열을 확장합니다.

Type['length']마지막으로 Type에서 길이 속성에 액세스합니다.

감사합니다!

