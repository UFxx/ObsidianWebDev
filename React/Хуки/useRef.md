Этот хук нужен для получении ссылки на элемент.  
Пример: 
```
import React, { useRef } from "react";
function UseRef() {
	// Объявляем useRef
  const element = useRef();

  return (
	<button
		className="element"
		// "Привязываем"
		ref={element}
		// По клику в консоль будет выводиться ссылка на этот элемент
		onClick={() => console.log(element)}
    >
		Кнопка
	</button>
  );
}  
```

**Пояснение**
Мы объявили хук `useRef` и указали в кнопке с чем она будет связана путем `ref={element}`, теперь мы можем получить к ней доступ через `element`.

---
[[Хуки]]