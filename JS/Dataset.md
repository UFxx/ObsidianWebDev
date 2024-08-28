В HTML элементам можно задавать атрибуты. В том числе можно задать атрибут `data`, к примеру: `data-start-position`. В JS мы можем взять все атрибуты начинающиеся с `data`:
```
// "[data]" - выбор элементов по названию аттрибута
const elementsWithData = document.querySelectorAll('[data]');
elementsWithData.forEach(el => {
  console.log(el.dataset);
})
```

**Пояснение**
В HTML можно задать элементу атрибут с любым названием, если он начинается с `data`. То есть написав `data-` и продолжив любым названием, которое нужно. 
К примеру:
`data-color`, `data-start-position`...

К этим атрибутам мы можем обратиться из JS использовав `dataset` (пример выше). По-мимо простого обращения к атрибуту `data`, мы можем устанавливать и менять его:
```
const elementsWithData = document.querySelectorAll("[data]");
elementsWithData.forEach((el, i) => {
  el.dataset.number = i;
  console.log(el.dataset); // Элемент с номером i в dataset
});
```

```
elementsWithData.forEach(el => {
  el.dataset.number = 1;
  console.log(el.dataset); // Элемент с номером 1 в dataset
});
```

Это позволяет удобно хранить, устанавливать и считывать любые значения, которые нужны.

Как упоминалось выше в `dataset` попадают все атрибуты элемента, которые начинаются с `data-` (в HTML). Соответственно названия атрибутов будут написаны через дефис, и обращение к ним будут выглядеть следующим образом: 
```
// Если в HTML есть атрибут "data-background-color"
console.log(el.dataset.backgroundColor)
```

То есть обращение к таким атрибутам аналогично обращения к стилям элемента (`el.style.zIndex`, `el.style.fontSize`).


---
[[JS]]