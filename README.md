import { useState } from 'react';
import { CounterInfo } from "./CounterInfo";

export const App = () => {
  const [count, setCount] = useState<number>(0);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Увеличить счетчик</button>
      <CounterInfo value={count} />
      <CounterInfo value={5} />
      <CounterInfo />
    </div>
  );
};

1. В первом компоненте ререндер будет происходить при нажатии на кнопку, так как в обработчик передана функция, которая содержит в себе функцию setCount, которая устанавливает новое состояние для переменной count. При каждом нажатии кнопки значение count будет увеличиваться на 1, так как в обработчике 1 setCount, можно обойтись без функционального подхода в setCount, батчинга нет.
  

interface CounterInfoProps {
  value?: number;
}

export const CounterInfo = ({ value }: CounterInfoProps) => {
  return <div className=”counter-info-container”>
    Значение: {value ?? "нет"}
  </div>;
};

2. В дочернем компоненте ререндер будет происходить при изменении состояния в родительском компоненте, то есть когда в родительском компоненте отработала кнопка и изменила состояние count, App вызовет ререндер у всех дочерних компонентов. Хотя по сути рендерить надо только  <CounterInfo value={count} />, где переданный пропс изменил значение в дочернем компоненте, но второй и третий компоненты тоже ререндерятся, несмотря на то что их пропсы не изменились.

 



