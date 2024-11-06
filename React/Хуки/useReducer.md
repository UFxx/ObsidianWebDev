Этот хук никак не предназначен для Redux. Используя этот его - мы получаем лишь аналог Redux в React. Он предназначен для хранения данных без привязки к компоненту (в этом преимущество `useReducer` перед `useState`). 
При использовании этого хука - мы выносим состояние за пределы компонентов, а затем можем использовать в любом компоненте импортируя его. Мы не храним состояние для каждого компонента отдельно, как в случае с `useState`, а так же нам не надо передавать каждый раз состояние в `props`, что может привести к `props drilling`.
Пример:
```
import  { useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
    </>
  );
}

export default Counter;
```

Создаём функцию, которая отвечает за логику обновления состояния. Затем создаём константу, куда передаём: `[состояние, диспетчер] = useReducer(функция, начальное состояние)`. Диспетчер (`dispatch`) отвечает за то, чтобы отправлять действия в функцию `reducer`.

Чтобы, в нашем случае увеличить или уменьшить счетчик - следует передать `dispatch` в другой компонент в `props` или с помощью `useContext`.

---
[[Хуки]]