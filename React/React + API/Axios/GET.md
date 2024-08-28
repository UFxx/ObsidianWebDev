GET - метод для передачи данных на сервер. В React выглядит следующим образом:
```
axios.get('http://127.0.0.1:8000/api-timetable/timetable/4-1is/')
.then(
	// some code
);
```

`axios.get("http://127.0.0.1:8000/auth/jwt/create",` - вызываем у `axios` метод GET и передаем в него ссылку, откуда надо брать данные.

**Важно**
В React нужно обернуть конструкцию в useEffect, чтобы получать данные при каждом вызове компонента. А так же нужно добавить массив зависимостей, чтобы запросы отправлялись не бесконечно, а один раз при рендере компонента.
```
useEffect(() => {
	axios.get('http://127.0.0.1:8000/api-timetable/timetable/4-1is/')
	.then((data) => setPairs(data.data.timetable));
}, []);
```

---
[[React/React + API/Axios/Методы|Методы]]