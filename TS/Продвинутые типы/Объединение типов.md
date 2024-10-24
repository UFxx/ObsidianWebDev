`Union` - объединение типов. Используется в случае, если надо принимать данные нескольких типов. 
Например:
```
function logId (id: string | number | boolean) {
	console.log(id);
}

logId(1)
logId('строка')
logId(true)
```

То есть мы через `|` перечисляем какие типы будем принимать.

Но если нам нужно привести принятый аргумент к нижнему регистру?
TypeScript выдаст ошибку, где напишет о том, что метода `toLowerCase()` не существует для какого-то типа.

На помощь нам придет стандартная конструкция `if-else`:
```
function logId (id: string | number | boolean) {
	if (typeof id === 'string') {
		console.log(id.toLowerCase);
	} else (typeof id === 'number) {
		console.log(id)
	}
}
```

Этот процесс называется `narrowing` (сужение типа).

Тоже самое можно сделать с массивами:
```
function logError (err: string | string[]) {
	if (Array.isArray(err)) {
		console.log(err);
	}
}
```

Стоит заметить, что при наведении на `err`, который в `console.log()` мы увидим, что его тип `string[]`, что означает - массив.

И с объектами:
```
function logObject (obj : { a: number } | { b: number }) {
	if ('a' in obj) {
		console.log(obj.a);
	}
}
```

В этом случае ключ объекта может быть либо `a`, либо `b`.
С помощью оператора `in` мы проверяем есть ли в объекте такой ключ.

---
[[Продвинутые типы]]