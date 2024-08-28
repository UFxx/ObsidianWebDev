# Числовой Enum
`enum` (перечисление) - позволяет определить набор именованных констант.
Например:
```
// Определим набор переменных
enum StatusCode {
    SUCCESS,
    IN_PROCESS,
    FAILED
}

const res = {
    message: 'Платёж успешен',
    statusCode: StatusCode.SUCCESS
}

if (res.statusCode === 0) {
    console.log(StatusCode.IN_PROCESS); // --> 1
}
```

При наведении на переменные в `StatusCode` мы увидим чему равно та или иная переменная. Отсчет по умолчанию начинается с 0, но мы можем задать своё значение:
```
enum StatusCode {
    SUCCESS = 1,
    IN_PROCESS,
    FAILED = 15
}
```

В таком случае `SUCCESS` будет равно 1, `IN_PROCCESS` = 2, `FAILED` = 15.

# Строковый Enum
Тоже самое, что и числовой `enum`:
```
enum StatusCode {
    SUCCESS = 's',
    IN_PROCESS = 'p',
    FAILED = 'f'
}
```

# Enum в функции
`enum` можно использовать в функции, чтобы указать аргумент какого типа принимать:
```
function action(status: StatusCode) {
	...
}
```

Мы можем вызвать эту функцию:
```
enum StatusCode {
    SUCCESS = 1,
    IN_PROCESS = 'p',
    FAILED = 15
}

function action(status: StatusCode) {
    console.log(status);
}

action(StatusCode.FAILED) // --> 1
action(1) // --> 1
action('p') // --> Ошибка: Аргумент типа "p" нельзя назначить параметру типа "StatusCode"
```

В целом `enum` можно использовать для ограничения возможных значений (когда нам нужно, чтобы функция принимала только опеределенные значения).

Также можно сделать значением `enum`'a функцию, или что-либо посчитать:
```
enum Units {
	millimeter = 1,
	centimeter = millimeter * 100,
	meter = calculateMeter()
}

function calculateMeter() {
	return Units.centimeter * 10
}
```

---
[[Основные типы]]