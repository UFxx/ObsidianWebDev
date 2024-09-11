Предположим, что у нас есть 2 компонента: родительский и дочерний. Мы создаём в родительском компоненте функцию и передаём её в дочерний. Нам нужно изменить из дочернего компонента что-то в родительском - это обычная практика.
```
// App.jsx
function App() {
  const [value, valueChange] = useState(Math.random());
  const changer = () => valueChange(Math.random());

  return (
    <>
      {value}
      <ControlPanel changer={changer} />
    </>
  );
}

// ControlPanel.jsx
const ControlPanel = memo(({ changer }) => {
  return <button onClick={changer}></button>;
});
```

Компонент `ControlPanel` специально обёрнут в `memo`, чтобы этот компонент перерисовывался только в том случае, когда изменились его параметры. Однако, в этом случае возникает проблема: при каждой отрисовке компонента `App` мы будем заново создавать метод `changer`. Соответственно каждый раз будет создан новый метод, следовательно, у `ControlPanel` будут происходить повторные рендеринги.
Избежать этого можно с помощью хука `useCallback`:
```
// App.jsx
const App = () => {
  const [value, valueChange] = useState(Math.random());
 
  const increment = useCallback(() => valueChange(Math.random()), []);
 
  return (
    <div>
      {value}
      <ControlPannel increment={increment} />
    </div>
  );
};

// ControlPanel.jsx
const ControlPanel = memo(({ increment }) => {
  return <button onClick={increment}>+</button>;
});
```

Благодаря этому хуку мы единожды создаём метод и обновляем его только тогда, когда меняется какой-то из параметров, которые мы поместили в качестве элементов массива и передает вторым аргументом (как массив зависимостей в `useEffect`).

---
[[Хуки]]