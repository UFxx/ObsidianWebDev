Асинхронные функции нужны для выполнения асинхронных операций: работой с API, базами данных, чтения файлов и так далее.
`Async` и `Await` нужны для того, чтобы дожидаться выполнения асинхронного кода. 
Пример:
```
// Этой функции, мы говорим, что она асинхронная
async function getData() {
// await говорит о том, что мы дожидаемся выполнения асинхронной операции (fetch - асинхронная операция)
  const response = await fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response);
  console.log(response);
}

// Указываем, что функция, в которой вызываются другие функции будет асинхронной
async function go() {
// Дожидаемся ответа от функции getData()
  await getData();
  console.log(2);
}
go() 
```

Так же с помощью `async/await` можно устанавливать порядок исполнения кода.
Пример:
```
async function getData1() {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/todos/1"
  ).then((response) => response);
  console.log(response);
}

async function getData2() {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/todos/2"
  ).then((response) => response);
  console.log(response);
}

async function go() {
  await getData1();
  await getData2()
}
go()
```

Здесь всё тоже самое, что и в примере выше, только добавилась вторая функций, которая тоже делает запрос на сервер. А в функции `go` вызываются обе функций, и при этом вторая функций не будет вызвана, пока не будет получен ответ от первой.
В этом случае вывод будет выглядеть следующим образом:
```
async function a() {
  await getData1(); // -> Данные о первом todo
  await getData2(); // -> Данные о втором todo
}
a()
```

Но так же мы можем поменять порядок, просто поменяв порядок вызова функций:
```
async function a() {
  await getData2(); // -> Данные о втором todo
  await getData1(); // -> Данные о первом todo
}
a()
```

Всё будет выведено в том же порядке, как и записано.

---
[[Асинхронность]]