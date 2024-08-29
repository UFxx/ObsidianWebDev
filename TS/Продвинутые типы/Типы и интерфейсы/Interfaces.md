Интерфейсы - тоже самое, что и `type`, но имеются различия в их записи и добавлении новый свойств:
```
interface User {
	name: string,
	age: number,
	skills: string[]
}

interface UserWithRole extends User {
	roleId: number,
}

let user: UserWithRole = {
	name: 'asd',
	age: 33,
	skills: ['Dev', 'DevOps'],
	roleId: 1
}
```

В том случае мы не создали еще один тип `Role`, а просто написали, что еще должен включать (`extends`) интерфейс (в нашем случае он включает в себя интерфейс `User`).

# Описание функции
Так же в интерфейсе мы можем описать и функцию:
```
interface User {
	name: string,
	age: number,
	skills: string[]

	log: (id: number) => string
}

let user: User = {
	name: 'asd',
	age: 33,
	skills: ['Dev', 'DevOps'],

	log(id) {
		return '';
	},
}
```


---
[[Что использовать]]