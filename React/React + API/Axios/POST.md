POST - метод для передачи данных на сервер. В React выглядит следующим образом:
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

Во второй аргумент мы передаем объект, состоящий из пар ключ-значение (usernam - ключ, loginValue - значение). 

---
[[React/React + API/Axios/Методы|Методы]]