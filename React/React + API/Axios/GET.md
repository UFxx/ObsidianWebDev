GET - [метод](React/React%20+%20API/Axios/Методы.md) для передачи данных на сервер. В [React](obsidian://open?vault=Web%20Dev&file=React%2FReact) выглядит следующим образом:
```
axios.get('http://127.0.0.1:8000/api-timetable/timetable/4-1is/')
.then(
	// some code
);
```

`axios.get("http://127.0.0.1:8000/auth/jwt/create",` - вызываем у [axios](Axios) [метод](Методы) GET и передаем в него ссылку, откуда надо брать данные.

**Важно**
В [[React]] нужно обернуть конструкцию в [useEffect](obsidian://open?vault=Web%20Dev&file=React%2F%D0%A5%D1%83%D0%BA%D0%B8%2FuseEffect), чтобы получать данные при каждом вызове [компонента](Компоненты). А так же нужно добавить массив зависимостей, чтобы запросы отправлялись не бесконечно, а один раз при рендере [компонента](Компоненты).
```
useEffect(() => {
	axios.get('http://127.0.0.1:8000/api-timetable/timetable/4-1is/')
	.then((data) => setPairs(data.data.timetable));
}, []);
```