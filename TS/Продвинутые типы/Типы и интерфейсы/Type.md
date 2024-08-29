Type Alias (псевдонимы типов) - позволяет создать новое имя для уже существующего типа данных (просто даёт типу новоё имя). Это позволяет улучшить читаемость кода.
Пример:
```
type httpMethod = 'POST' | 'GET';

function fetchWithAuth (url: string, method: httpMethod) {
	return method
}

fetchWithAuth('aa', 'POST')
```

Мы объявили тип `httpMethod`, значением которого является объединение `POST` и `GET` типов.

# Описание объекта
Описание объекта происходит точно также:
```
type User {
	name: string,
	age: number,
	skills: string[]
}

let user: User = {
	name: 'asd',
	age: 33,
	skills: ['Dev', 'DevOps']
}
```

Создаём тип, который содержит поля нужного объекта и указываем у них тип данных, затем типизируем объект.

# Объединение Type Alias
Мы также можем объединить 2 разных типа, чтобы потом использовать их для типизации:
```
type User = {
	name: string,
	age: number,
	skills: string[]
}

type Role = {
	id: number
}

type UserWithRole = User & Role;

let user: UserWithRole = {
	name: 'asd',
	age: 33,
	skills: ['Dev', 'DevOps'],
	id: 1
}
```

Если у типов, которые мы объединили есть пересекающиеся части (2 одинаковых поля), то мы можем задать их лишь один раз.
То есть если у типа `Role` будет свойство `name`, то в объект `user` нам не нужно писать 2 раза свойство `name`.

---
[[Что использовать]]