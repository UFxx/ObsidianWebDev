POST - [метод](React/React%20+%20API/Axios/Методы.md) для передачи данных на сервер. В [React](obsidian://open?vault=Web%20Dev&file=React%2FReact) выглядит следующим образом:
```
axios.post("http://127.0.0.1:8000/auth/jwt/create",
{
	username: loginValue,
	password: passwordValue
}
);
```

Разберем код подробно:
`axios.post("http://127.0.0.1:8000/auth/jwt/create",` - вызываем у axios метод post и передаем в него 2 аргумента:
1. Ссылка, куда отправить данные
2. Какие данные будем отправлять

**Важно**
Перед вторым пунктом нужно объявить переменные, откуда мы берем данные:
```
const loginValue = document.querySelector('#login-input').value;
const passwordValue = document.querySelector('#login-password').value;
```

Во второй аргумент мы передаем [объект](obsidian://open?vault=Web%20Dev&file=JS%2F%D0%A2%D0%B8%D0%BF%D1%8B%2F%D0%9E%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D1%8B), состоящий из пар ключ-значение (usernam - ключ, loginValue - значение). 