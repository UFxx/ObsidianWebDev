Type Guard - один из способов сужения типов.
# Функция-TypeGuard
Функция должна вернуть `true` или `false`. Внутри нее происходит проверка на тип:
```
function isString(x: string | number): x is string {
	return typeof x === 'string';
}
```

Соответственно мы можем использовать эту функцию при сужении типов:
```
if (isString(id)) {
	console.log(id);
}
```

Рассмотрим пример, когда нам нужно поменять роль какому-либо пользователю:
```
function isAdmin(user: User | Admin): user is Admin {
	return 'role' in user;
}

function setRoleZero(user: User | Admin) {
	if (isAdmin(user)) {
		user.role = 0;
	} else {
		throw new Error('Пользователь не администратор');
	}
}
```

---

**Важно**
Возвращаемое значение у функции `isAdmin` не является `boolean`.

---
[[Продвинутые типы]]