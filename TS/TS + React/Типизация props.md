Для типизации `props` можно использовать `type` или `interface`:
```
export enum CardVariant {
	outlined = 'outlined',
	primary = 'primary'
}

interface CardProps {
	width?: string;
	height?: string;
	children?: ReactNode;
	variant: CardVariant;
	onClick: () => void;
}

const Card: FC<CardProps> = ({ width, height, children, variant, onClick }) => {
	return (
		<div
			style={{
				width,
				height,
				border: variant === CardVariant.outlined ? '2px solid white' : 'none',
				background: variant === CardVariant.primary ? 'white' : 'black'
			}}
			onClick={onClick}
		>
			{children}
		</div>
	);
};
```

В этом случае в `props` мы получаем ширину, высоту, какой-то дочерний элемент, вариант отрисовки карточки, а так же событие `onClick`.

Если с шириной и высотой всё понятно - это просто строки, то стоит разобрать что за типизация у `children`, `variant`, и события `onClick`:
- У `children` тип `ReactNode` - это встроенный тип, который описывает данные, которые рендерятся в React.
- У `variant` тип `CardVariant`, который в свою очередь является `enum` (перечисление). Также стоит заметить, что у `enum` есть `export`, чтобы передать его в `props` из родительского компонента.
- При типизации передаваемой функции нужно указать типизацию параметров (если есть), а так же возвращаемый тип. То есть, если б функция `onClick` принимала некоторые параметры, а затем ничего не возвращала, это выглядело бы так: `onClick: (num: number) => void`.

Рассмотрим как передаются эти `props`:
```
import Card, { CardVariant } from './components/Card';

<Card
	onClick={() => console.log('aa')}
	variant={CardVariant.outlined}
	// width & height
>	
	<button>Кнопка</button>
</Card>
```

Добавим событие, которое использует переданную функцию:
```
interface CardProps {
	// ...
	onClick: (num: number) => void;
}

const Card: FC<CardProps> = ({ width, height, children, variant, onClick }) => {
	const [state, setState] = useState(0);

	return (
		<div
			style={{
				// ...
			}}
			onClick={() => onClick(state)}
		>
			{children}
		</div>
	);
};
```

App.js:
```
const App: React.FC = function App() {
	return (
		<>
			<Card
				onClick={(num: number) => console.log('aa', num)}
				// ...
			>
				<button>Кнопка</button>
			</Card>
		</>
	);
};
```

То есть мы передаем функцию `onClick`, затем вызываем её в дочернем компоненте в событии `onClick`, передавая в качестве параметра состояние.

---
[[Типизация функциональных компонентов]]