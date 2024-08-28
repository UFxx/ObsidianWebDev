MutationObserver - позволяет следить за изменениями в DOM. 
Пример использования:
```
const node = document.querySelector(".node");

// Функция, которая будет выполняться при вызове MutationObserver
function callback (mutations) {
	console.log(mutations)
};

// Создаем MutationObserver, который принимает функцию
let observer = new MutationObserver(callback);

// Говорим observer'у, что нужно следить, а затем передаем ему 2 параметра:
// 1 - элемент, за которым надо следить
// 2 - параметры, за изменением которых надо следить
observer.observe(node, { childList: true; });

// Переданная функция будет вызываться каждый раз, когда будут происходить изменения в переданном элементе (с его дочерними элементами)
```

**Подробнее: 
[Видео](https://www.youtube.com/watch?v=RYMsQqinxGY)