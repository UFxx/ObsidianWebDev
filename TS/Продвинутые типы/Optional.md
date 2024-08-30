`?` - используется, когда поле является необязательным.
Пример:
```
interface User {
  login: string;
  password?: string;
}

const user: User = {
  login: "a@a.ru",
};

```

В этом случае TypeScript не выдает ошибку, когда у нас в объекте нет поля `password`, потому что мы указали, что оно может быть, а может и не быть.

**Важно**
`?` не является аналогом `string | undefined`, потому что при втором случае всё равно нужно добавлять `password` поле в объект:
```
interface User {
  login: string;
  password: string | undefined;
}

const user: User = {
  login: "a@a.ru",
};
```

TypeScript выдает ошибку, потому что нет поля `password`.

# В функциях
`?` можно также использовать в функциях:
```
function multiply(first: number, second?: number): number {
  return first * second;
}
```

В этом случае мы получим ошибку, потому что `second` может просто не "придти" в функцию.

Однако в этом случае запись `number | undefined` является эквивалентом `?`. При наведении на `second?` мы увидим его тип, которым является `number | undefined`.

Чтобы обработать это - можно использовать сужение типов:
```
function multiply(first: number, second?: number): number {
  if (!second) {
    return first * first;
  }
  return first * second;
}
```

Или же можно задать значение по умолчанию:
`function multiply(first: number, second: number = 5): number {}`

# В объекте
`?` также можно использовать в объектах:
```
interface User {
  login: string;
  password?: {
    type: "primary" | "secondary";
    pass: string;
  };
}

function testPass(user: User) {
  const t = user.password?.type;
}
```

Здесь также можно применить сужение типов:
```
function testPass(user: User) {
  const t = user.password ? user.password.type : undefined;
}
```

---
**Важно**
Также есть функция `!`, которая говорит о том, что поле в любом случае не будет `undefined`. (не советуется использовать)

```
function testPass(user: User) {
  const t = user.password!.type;
}
```

# ??
`??` - операция, которая позволяет проверить равна ли переменная `null` или `undefined`:
```
function test(param?: string) {
  const t = param ?? multiply(5);
}
```

Если `param` является `null` или `undefined`, то мы выполняем `multiply(5)`.

---
[[Продвинутые типы]]