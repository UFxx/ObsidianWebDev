`never` используется в том случае, когда значение никогда не возвращается:
```
function generateError (message: string): never {
  throw new Error(message)
}
```

Если мы добавим в функцию `return`, то увидим ошибку.

Пусть `never` и похож на `void` - это разные типы. 
`never` стоит использовать в том случае, если функция никогда не завершится.

Довольно полезный пример использования:
```
type paymentAction = 'refund' | 'checkout'

function processAction(action: paymentAction) {
	switch (action) {
		case 'refund':
			// ...
			break
		case 'checkout':
			// ...
			break
		default:
			throw new Error('Нет такого action')
	}
}
```

Допустим, что у нас добавилось еще одно действие - `reject`:
`type paymentAction = 'refund' | 'checkout' | 'reject'`

Добавим в `default` следующий строчку:
`const _: never = action`
И теперь у нас передаётся третий `action`, хотя явно мы этого не указали.

---
[[Продвинутые типы]]