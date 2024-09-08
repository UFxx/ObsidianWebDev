`useContext` - хук, который позволяет передавать данные в дочерние компоненты на любом уровне минуя `props`.

Для начала нужно определить контекст на верхнем уровне компонента (перед определением самого компонента):
`export const MyContext = createContext("without provider");`

Затем нужно обернуть компонент(-ы), в которые мы передаем данные:
```
<MyContext.Provider value="Значение из App.js">
	<Parent />
</MyContext.Provider>
```

В компоненте, где эти данные нам нужны вызываем `useContext`, а затем можем его свободно использовать:
```
import { MyContext } from "../../../App";
const contextValue = useContext(MyContext);

function Child() {
const contextValue = useContext(MyContext);

return (
	<p>Значение: {contextValue}</p>
);
}
```

**Важно**
Обязательно нужно указать `export` при создании контекста и `import` при его использовании.

---
[[Хуки]]