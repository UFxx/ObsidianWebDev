JWT (JSON web token) -  токен, благодаря которому можно узнать авторизован ли пользователь.
Его можно получить сделав запрос на определенный эндпоинт (ссылка, куда делается запрос).
Пример кода:
```
// Login.jsx
// Функция вызывается по клику на копку "Войти"
function login() {
if (!localStorage.getItem("JWT")) {
// Отправляем username и password с формы
  axios
	.post("http://127.0.0.1:8000/auth/jwt/create/", {
	  username: passwordValue,
	  password: loginValue,
	})
```

```
	// В ответ на POST-запрос нам приходят данные, которые содержат объект из 2    элементов: access и refresh
	.then((data) => {
	  localStorage.setItem("JWT", data.data.access);
```

После того, как мы получили токены записываем access токен в localStorage, а refresh токен нужно записать в HttpOnly cookie. `HttpOnly` говорит о том, что этот токен можно только передать по HTTP запросу, прочесть их нельзя.
```
// App.js
axios.defaults.headers.common["Authorization"] = JWT ${localStorage.getItem("JWT")};
```

**Пояснение**
В App.js есть строчка:
`axios.defaults.headers.common["Authorization"] = JWT ${localStorage.getItem("JWT")};`
она говорит о том, что мы записываем в заголовки страницы по именем `Authorization` JWT токен, которой берем из `localStorage` (ведь туда мы его записали при получении ответа на [POST](POST)-запрос).
Эта строка находится именно в App.js, потому что нам нужно, чтобы это срабатывало при каждом переходе на другую страницу, иначе заголовок `Authorization` пропадет при перезагрузке на любой странице.