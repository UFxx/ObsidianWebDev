Этот хук нужен для динамического изменения данных на странице.
Пример: 
```
const [isOpen, openMenu] = useState(false); 
// Определяем массив с 2 аргументами (переменная и функция, которая ее изменяет), в useState() записываем изначальное значение пременной

    function menuToggle() {
        openMenu(!isOpen); 
        // передаем в функцию созданную нами функцию для изменния переменной и указываем на какое значение
        
    }
    ...
   <div onClick={menuToggle} className='menu-burger-icon'> 
   // Вызываем функцию по клику, она вызывает в свою очередь функцию, которая изменяет значение переменной isOpen и значение меняется с false на true
```

# Подъём состояния
Подъём состояния нужно для того, чтобы иметь доступ к данным в родительском компоненте из дочернего. Пример кода: 
```
// --- Родительский компонент --- 
// This state changes in <Filter/>
const [subjects, setSubject] = useState("");
...
<div className="rating-content">
	<Filter
	  key="1"
	  // Передаем состояние в дочерний компонент
	  subjects={subjects}
	  setSubject={setSubject}
	  userSlug={props.userSlug}
	/>
<div className="ratings">{ratings}</div>
```

```
// Дочерний компонент
// Принимаем props в компоненте
function Filter(props) { 
	// Some code
	
	// Обращемся к переданному состянию через "props"
	for (let i = 0; i < props.subjects.length; i++) {
		disciplines.push(
		  <Discipline disciplineName={props.subjects[i].subject} id={i} key={i} />
		);
	}
}
```

**Пояснение**
Мы вызываем useState в родительском компоненте, затем передаем его переменную  и функцию (см. useState) в дочерний и меняем переменную там.

---
[[Хуки]]