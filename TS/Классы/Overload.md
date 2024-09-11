Overload - когда имея сигнатуру функций (сигнатура содержит информацию о том какие аргументы она принимает и какое значение возвращает) дополняем её альтернативной сигнатурой, чтобы, например можно было создать пользователя только с именем, так и только с возрастом.

Допустим, нам нужно создать пользователя без имени. Для этого понадобится создать еще несколько конструкторов. 
```
class User {
	name: string;

	constructor();
	constructor(name: string);
	constructor(name?: string) {
		if (typeof name === 'string') {
			this.name = name;
		}
	}
}

const user = new User('Дмитрий');
const user2 = new User();
```

А теперь нам нужно создать пользователя только с возрастом, но при этом оставить возможность создать пользователя с именем и без него:
```
class User {
	name: string;
	age: number;

	constructor();
	constructor(name: string);
	constructor(age: number);
	constructor(name: string, age: number);
	constructor(ageOrName?: string | number, age?: number) {
		if (typeof ageOrName === 'string') {
			this.name = ageOrName;
		} else if (typeof ageOrName === 'number') {
			this.age = ageOrName;
		}
		if (typeof age === 'number') {
			this.age = age;
		}
	}
}

const user = new User('Дмитрий');
const user2 = new User();
const user3 = new User(33);
```

Нам нужно создавать конструкторы для каждого допустимого случая. Перегрузки (overload) - очень полезный функционал, когда нужно сделать 1-2-3 реализации, но сложность с каждой перезагрузкой нарастает, поэтому, в случаях, когда перезагрузок надо довольно много - следует использовать статичные методы, которые и будут собирать пользователя.

---
[[Конструктор]]