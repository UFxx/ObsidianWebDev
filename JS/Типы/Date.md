# Дата и время
В JS представлен простой класс `Date`, который представляет числа, которые представляют дату и время. Экземпляры класса `Date` являются объектами, но они так же имеют числовое представление в отметок времени в миллисекундах, которые прошли с 1 января 1970 года.
```
let timestamp = Date.now(); // Текущее время как отметка времени (число)
let now = new Date(); // Текущее время как объект Date
let ms = now.getTime(); // Преобразовать в миллисекундную отметку времени
let iso = now.toISOString(); // Преобразовать в строку со стандартным форматом
```

---
[Типы](Типы)