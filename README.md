```
React + Vita 
Начнем с основ и постепенно перейдем к более сложным концепциям. 
Часть 1: Основы JSX и компонентов
```
Пример 1: Простой функциональный компонент
```jsx
// Импортируем React
import React from 'react';

// Создаем функциональный компонент
function Welcome() {
  // Возвращаем JSX - разметку компонента
  return <h1>Привет, мир!</h1>;
}

// Экспортируем компонент для использования в других файлах
export default Welcome;
```
Пример 2: Компонент с пропсами (props)
```jsx
import React from 'react';

// Компонент принимает пропс `name`
function Greeting(props) {
  // Используем пропс в JSX
  return <h2>Здравствуй, {props.name}!</h2>;
}

export default Greeting;
```
Пример 3: Использование компонента
```jsx
import React from 'react';
import Greeting from './Greeting';

function App() {
  return (
    <div>
      {/* Передаем пропс name компоненту Greeting */}
      <Greeting name="Анна" />
      <Greeting name="Петр" />
      <Greeting name="Мария" />
    </div>
  );
}

export default App;
```
Пример 4: Компонент с деструктуризацией пропсов
```jsx
import React from 'react';

// Деструктурируем пропсы для удобства
function UserCard({ name, age, email }) {
  return (
    <div className="user-card">
      <h3>{name}</h3>
      <p>Возраст: {age}</p>
      <p>Email: {email}</p>
    </div>
  );
}

export default UserCard;
```
Пример 5: Вложенные компоненты
```jsx
import React from 'react';

function Header() {
  return <header>Мой сайт</header>;
}

function Main() {
  return <main>Основное содержимое</main>;
}

function Footer() {
  return <footer>© 2024</footer>;
}

function Layout() {
  return (
    <div>
      <Header />
      <Main />
      <Footer />
    </div>
  );
}

export default Layout;
```
Пример 6: JSX выражения
```jsx
import React from 'react';

function Calculator() {
  const a = 5;
  const b = 3;
  
  return (
    <div>
      <p>{a} + {b} = {a + b}</p>
      <p>{a} * {b} = {a * b}</p>
      <p>{a > b ? 'a больше b' : 'b больше или равно a'}</p>
    </div>
  );
}

export default Calculator;
```
Пример 7: Атрибуты в JSX
```jsx
import React from 'react';

function ImageComponent() {
  const imageUrl = "https://via.placeholder.com/150";
  const altText = "Заполнитель изображения";
  
  return (
    <div>
      {/* Атрибуты похожи на HTML, но используют camelCase */}
      <img 
        src={imageUrl} 
        alt={altText}
        width={150}
        height={150}
        className="my-image"
      />
    </div>
  );
}

export default ImageComponent;
```
Пример 8: Стили в JSX
```jsx
import React from 'react';

function StyledComponent() {
  // Стили задаются как объект
  const divStyle = {
    backgroundColor: 'lightblue',
    padding: '20px',
    borderRadius: '8px',
    textAlign: 'center'
  };
  
  return (
    <div style={divStyle}>
      <h2 style={{ color: 'darkblue' }}>Стилизованный заголовок</h2>
      <p style={{ fontSize: '16px', lineHeight: '1.5' }}>
        Этот текст имеет собственные стили
      </p>
    </div>
  );
}

export default StyledComponent;
```
Пример 9: Компонент с детьми (children)
```jsx
import React from 'react';

// Компонент принимает children
function Container({ children, title }) {
  return (
    <div className="container">
      <h2>{title}</h2>
      {/* children - это всё, что находится между открывающим и закрывающим тегом */}
      <div className="content">
        {children}
      </div>
    </div>
  );
}

function App() {
  return (
    <Container title="Мой контейнер">
      <p>Это содержимое контейнера</p>
      <button>Кнопка внутри</button>
    </Container>
  );
}

export default App;
```
Пример 10: Условный рендеринг
```jsx
import React from 'react';

function ConditionalRender({ isLoggedIn, username }) {
  return (
    <div>
      {/* Условный рендеринг с помощью && */}
      {isLoggedIn && <p>Добро пожаловать, {username}!</p>}
      
      {/* Условный рендеринг с тернарным оператором */}
      {isLoggedIn ? (
        <button>Выйти</button>
      ) : (
        <button>Войти</button>
      )}
    </div>
  );
}

export default ConditionalRender;
Часть 2: Работа с состоянием (useState)
```
Пример 11: Простой счетчик
```jsx
import React, { useState } from 'react';

function Counter() {
  // useState возвращает массив: [текущее значение, функция для обновления]
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>Счетчик: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Увеличить
      </button>
      <button onClick={() => setCount(count - 1)}>
        Уменьшить
      </button>
      <button onClick={() => setCount(0)}>
        Сбросить
      </button>
    </div>
  );
}

export default Counter;
```
Пример 12: Работа с формами
```jsx
import React, { useState } from 'react';

function SimpleForm() {
  // Состояние для хранения значения input
  const [name, setName] = useState('');
  
  // Обработчик изменения input
  const handleChange = (event) => {
    setName(event.target.value);
  };
  
  // Обработчик отправки формы
  const handleSubmit = (event) => {
    event.preventDefault(); // Предотвращаем перезагрузку страницы
    alert(`Привет, ${name}!`);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <label>
        Ваше имя:
        <input 
          type="text" 
          value={name} 
          onChange={handleChange}
        />
      </label>
      <button type="submit">Отправить</button>
      <p>Текущее имя: {name}</p>
    </form>
  );
}

export default SimpleForm;
```
Пример 13: Несколько полей формы
```jsx
import React, { useState } from 'react';

function MultiFieldForm() {
  // Состояние для нескольких полей
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: '',
    age: ''
  });
  
  // Универсальный обработчик изменений
  const handleChange = (event) => {
    const { name, value } = event.target;
    setFormData(prevData => ({
      ...prevData, // Копируем предыдущее состояние
      [name]: value // Обновляем нужное поле
    }));
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Данные формы:', formData);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        name="firstName"
        value={formData.firstName}
        onChange={handleChange}
        placeholder="Имя"
      />
      <input
        type="text"
        name="lastName"
        value={formData.lastName}
        onChange={handleChange}
        placeholder="Фамилия"
      />
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
        placeholder="Email"
      />
      <input
        type="number"
        name="age"
        value={formData.age}
        onChange={handleChange}
        placeholder="Возраст"
      />
      <button type="submit">Отправить</button>
    </form>
  );
}

export default MultiFieldForm;
```
Пример 14: Переключение состояния
```jsx
import React, { useState } from 'react';

function ToggleComponent() {
  const [isOn, setIsOn] = useState(false);
  
  const toggle = () => {
    setIsOn(!isOn);
  };
  
  return (
    <div>
      <p>Статус: {isOn ? 'ВКЛ' : 'ВЫКЛ'}</p>
      <button onClick={toggle}>
        {isOn ? 'Выключить' : 'Включить'}
      </button>
      <div style={{
        width: '100px',
        height: '100px',
        backgroundColor: isOn ? 'green' : 'red'
      }}>
        {isOn ? '✅' : '❌'}
      </div>
    </div>
  );
}

export default ToggleComponent;
```
Пример 15: Работа с массивом в состоянии
```jsx
import React, { useState } from 'react';

function TodoList() {
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState('');
  
  const addTodo = () => {
    if (inputValue.trim()) {
      setTodos([...todos, inputValue]);
      setInputValue('');
    }
  };
  
  const removeTodo = (index) => {
    const newTodos = todos.filter((_, i) => i !== index);
    setTodos(newTodos);
  };
  
  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        placeholder="Новая задача"
      />
      <button onClick={addTodo}>Добавить</button>
      
      <ul>
        {todos.map((todo, index) => (
          <li key={index}>
            {todo}
            <button onClick={() => removeTodo(index)}>Удалить</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TodoList;
```
Пример 16: Работа с объектом в состоянии
```jsx
import React, { useState } from 'react';

function UserProfile() {
  const [user, setUser] = useState({
    name: '',
    age: '',
    city: ''
  });
  
  const updateField = (field, value) => {
    setUser(prev => ({
      ...prev,
      [field]: value
    }));
  };
  
  return (
    <div>
      <input
        type="text"
        placeholder="Имя"
        value={user.name}
        onChange={(e) => updateField('name', e.target.value)}
      />
      <input
        type="number"
        placeholder="Возраст"
        value={user.age}
        onChange={(e) => updateField('age', e.target.value)}
      />
      <input
        type="text"
        placeholder="Город"
        value={user.city}
        onChange={(e) => updateField('city', e.target.value)}
      />
      
      <div>
        <h3>Профиль пользователя:</h3>
        <p>Имя: {user.name}</p>
        <p>Возраст: {user.age}</p>
        <p>Город: {user.city}</p>
      </div>
    </div>
  );
}

export default UserProfile;
```
Пример 17: Сложный счетчик с историей
```jsx
import React, { useState } from 'react';

function AdvancedCounter() {
  const [count, setCount] = useState(0);
  const [history, setHistory] = useState([]);
  
  const increment = () => {
    const newCount = count + 1;
    setCount(newCount);
    setHistory([...history, `Увеличили до ${newCount}`]);
  };
  
  const decrement = () => {
    const newCount = count - 1;
    setCount(newCount);
    setHistory([...history, `Уменьшили до ${newCount}`]);
  };
  
  const reset = () => {
    setCount(0);
    setHistory([...history, 'Сбросили до 0']);
  };
  
  return (
    <div>
      <h2>Счетчик: {count}</h2>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={reset}>Сбросить</button>
      
      <h3>История изменений:</h3>
      <ul>
        {history.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

export default AdvancedCounter;
```
Пример 18: Фильтр списка
```jsx
import React, { useState } from 'react';

function FilterList() {
  const items = ['Яблоко', 'Банан', 'Апельсин', 'Виноград', 'Киви'];
  const [filter, setFilter] = useState('');
  
  const filteredItems = items.filter(item =>
    item.toLowerCase().includes(filter.toLowerCase())
  );
  
  return (
    <div>
      <input
        type="text"
        placeholder="Фильтровать список..."
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
      />
      
      <ul>
        {filteredItems.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
      
      {filteredItems.length === 0 && <p>Ничего не найдено</p>}
    </div>
  );
}

export default FilterList;
```
Пример 19: Темная тема
```jsx
import React, { useState } from 'react';

function ThemeSwitcher() {
  const [isDark, setIsDark] = useState(false);
  
  const theme = {
    backgroundColor: isDark ? '#333' : '#fff',
    color: isDark ? '#fff' : '#333',
    padding: '20px',
    minHeight: '100vh'
  };
  
  return (
    <div style={theme}>
      <h1>{isDark ? 'Темная тема' : 'Светлая тема'}</h1>
      <button onClick={() => setIsDark(!isDark)}>
        Переключить на {isDark ? 'светлую' : 'темную'} тему
      </button>
      <p>Это ```
Пример переключения тем с помощью состояния</p>
    </div>
  );
}

export default ThemeSwitcher;
```
Пример 20: Корзина покупок
```jsx
import React, { useState } from 'react';

function ShoppingCart() {
  const [cart, setCart] = useState([]);
  const products = [
    { id: 1, name: 'Телефон', price: 1000 },
    { id: 2, name: 'Ноутбук', price: 2000 },
    { id: 3, name: 'Наушники', price: 100 }
  ];
  
  const addToCart = (product) => {
    setCart([...cart, product]);
  };
  
  const removeFromCart = (productId) => {
    setCart(cart.filter(item => item.id !== productId));
  };
  
  const total = cart.reduce((sum, item) => sum + item.price, 0);
  
  return (
    <div>
      <h2>Товары:</h2>
      {products.map(product => (
        <div key={product.id}>
          <span>{product.name} - ${product.price}</span>
          <button onClick={() => addToCart(product)}>Добавить в корзину</button>
        </div>
      ))}
      
      <h2>Корзина:</h2>
      {cart.map(item => (
        <div key={item.id}>
          <span>{item.name} - ${item.price}</span>
          <button onClick={() => removeFromCart(item.id)}>Удалить</button>
        </div>
      ))}
      
      <h3>Итого: ${total}</h3>
    </div>
  );
}

export default ShoppingCart;
Часть 3: Эффекты (useEffect)
```
Пример 21: Простой useEffect
```jsx
import React, { useState, useEffect } from 'react';

function SimpleEffect() {
  const [count, setCount] = useState(0);
  
  // useEffect выполняется после каждого рендера
  useEffect(() => {
    console.log(`Компонент обновился, счетчик: ${count}`);
  });
  
  return (
    <div>
      <p>Счетчик: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Увеличить
      </button>
    </div>
  );
}

export default SimpleEffect;
```
Пример 22: useEffect с зависимостями
```jsx
import React, { useState, useEffect } from 'react';

function EffectWithDependencies() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('');
  
  // Выполняется только при изменении count
  useEffect(() => {
    console.log(`Счетчик изменился: ${count}`);
  }, [count]); // Зависимость от count
  
  // Выполняется только при изменении name
  useEffect(() => {
    console.log(`Имя изменилось: ${name}`);
  }, [name]); // Зависимость от name
  
  return (
    <div>
      <input
        type="text"
        placeholder="Введите имя"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>Счетчик: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Увеличить счетчик
      </button>
    </div>
  );
}

export default EffectWithDependencies;
```
Пример 23: Загрузка данных с useEffect
```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  // useEffect с пустым массивом зависимостей выполняется один раз при монтировании
  useEffect(() => {
    const fetchData = async () => {
      try {
        setLoading(true);
        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
        const jsonData = await response.json();
        setData(jsonData);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    
    fetchData();
  }, []); // Пустой массив = выполнить один раз
  
  if (loading) return <div>Загрузка...</div>;
  if (error) return <div>Ошибка: {error}</div>;
  
  return (
    <div>
      <h2>Загруженные данные:</h2>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default DataFetcher;
```
Пример 24: Таймер с useEffect
```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);
  
  useEffect(() => {
    // Создаем интервал
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);
    
    // Функция очистки - выполняется при размонтировании компонента
    return () => clearInterval(interval);
  }, []); // Пустой массив зависимостей = эффект выполняется один раз
  
  return (
    <div>
      <h2>Таймер: {seconds} секунд</h2>
    </div>
  );
}

export default Timer;
```
Пример 25: Отслеживание размера окна
```jsx
import React, { useState, useEffect } from 'react';

function WindowSizeTracker() {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight
  });
  
  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight
      });
    };
    
    // Добавляем слушатель события
    window.addEventListener('resize', handleResize);
    
    // Очистка слушателя при размонтировании
    return () => window.removeEventListener('resize', handleResize);
  }, []); // Пустой массив = эффект выполняется один раз
  
  return (
    <div>
      <h2>Размер окна:</h2>
      <p>Ширина: {windowSize.width}px</p>
      <p>Высота: {windowSize.height}px</p>
    </div>
  );
}

export default WindowSizeTracker;
```
Пример 26: Локальное хранилище
```jsx
import React, { useState, useEffect } from 'react';

function LocalStorageExample() {
  const [name, setName] = useState('');
  
  // Загружаем данные из localStorage при монтировании
  useEffect(() => {
    const savedName = localStorage.getItem('userName');
    if (savedName) {
      setName(savedName);
    }
  }, []);
  
  // Сохраняем данные в localStorage при изменении name
  useEffect(() => {
    localStorage.setItem('userName', name);
  }, [name]);
  
  return (
    <div>
      <input
        type="text"
        placeholder="Введите ваше имя"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>Привет, {name || 'незнакомец'}!</p>
      <p>Имя сохраняется в localStorage</p>
    </div>
  );
}

export default LocalStorageExample;
```
Пример 27: Кастомный хук для localStorage
```jsx
import React, { useState, useEffect } from 'react';

// Создаем кастомный хук
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });
  
  useEffect(() => {
    window.localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);
  
  return [value, setValue];
}

function LocalStorageHookExample() {
  const [name, setName] = useLocalStorage('userName', '');
  const [age, setAge] = useLocalStorage('userAge', '');
  
  return (
    <div>
      <input
        type="text"
        placeholder="Имя"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <input
        type="number"
        placeholder="Возраст"
        value={age}
        onChange={(e) => setAge(e.target.value)}
      />
      <p>Имя: {name}, Возраст: {age}</p>
    </div>
  );
}

export default LocalStorageHookExample;
```
Пример 28: Отслеживание скролла
```jsx
import React, { useState, useEffect } from 'react';

function ScrollTracker() {
  const [scrollY, setScrollY] = useState(0);
  
  useEffect(() => {
    const handleScroll = () => {
      setScrollY(window.scrollY);
    };
    
    window.addEventListener('scroll', handleScroll);
    
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);
  
  return (
    <div style={{ height: '200vh' }}>
      <div style={{
        position: 'fixed',
        top: '20px',
        right: '20px',
        background: 'rgba(0,0,0,0.8)',
        color: 'white',
        padding: '10px',
        borderRadius: '5px'
      }}>
        Позиция скролла: {scrollY}px
      </div>
      <p>Прокрутите страницу вниз</p>
    </div>
  );
}

export default ScrollTracker;
```
Пример 29: Зависимый запрос данных
```jsx
import React, { useState, useEffect } from 'react';

function UserPosts() {
  const [userId, setUserId] = useState(1);
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(false);
  
  // Эффект выполняется при изменении userId
  useEffect(() => {
    const fetchPosts = async () => {
      setLoading(true);
      try {
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/posts?userId=${userId}`
        );
        const data = await response.json();
        setPosts(data);
      } catch (error) {
        console.error('Ошибка:', error);
      } finally {
        setLoading(false);
      }
    };
    
    fetchPosts();
  }, [userId]); // Зависимость от userId
  
  return (
    <div>
      <h2>Посты пользователя {userId}</h2>
      <select 
        value={userId} 
        onChange={(e) => setUserId(Number(e.target.value))}
      >
        <option value={1}>Пользователь 1</option>
        <option value={2}>Пользователь 2</option>
        <option value={3}>Пользователь 3</option>
      </select>
      
      {loading ? (
        <p>Загрузка...</p>
      ) : (
        <ul>
          {posts.map(post => (
            <li key={post.id}>
              <h3>{post.title}</h3>
              <p>{post.body}</p>
            </li>
          ))}
        </ul>
      )}
    </div>
  );
}

export default UserPosts;
```
Пример 30: Управление заголовком документа
```jsx
import React, { useState, useEffect } from 'react';

function DocumentTitle() {
  const [count, setCount] = useState(0);
  
  // Изменяем заголовок документа
  useEffect(() => {
    document.title = `Счетчик: ${count}`;
  }, [count]); // Зависимость от count
  
  return (
    <div>
      <p>Счетчик: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Увеличить
      </button>
      <p>Посмотрите на заголовок вкладки!</p>
    </div>
  );
}

export default DocumentTitle;
Часть 4: Обработка событий
```
Пример 31: Обработчики событий
```jsx
import React, { useState } from 'react';

function EventHandlers() {
  const [message, setMessage] = useState('');
  
  const handleClick = () => {
    setMessage('Кнопка была нажата!');
  };
  
  const handleMouseOver = () => {
    setMessage('Мышь над кнопкой!');
  };
  
  const handleMouseOut = () => {
    setMessage('Мышь ушла с кнопки!');
  };
  
  const handleKeyPress = (event) => {
    if (event.key === 'Enter') {
      setMessage('Была нажата клавиша Enter!');
    }
  };
  
  return (
    <div>
      <button 
        onClick={handleClick}
        onMouseOver={handleMouseOver}
        onMouseOut={handleMouseOut}
      >
        Наведи и нажми меня
      </button>
      
      <input
        type="text"
        placeholder="Нажми Enter"
        onKeyPress={handleKeyPress}
      />
      
      <p>{message}</p>
    </div>
  );
}

export default EventHandlers;
```
Пример 32: Форма с валидацией
```jsx
import React, { useState } from 'react';

function ValidationForm() {
  const [formData, setFormData] = useState({
    email: '',
    password: ''
  });
  const [errors, setErrors] = useState({});
  
  const validate = () => {
    const newErrors = {};
    
    if (!formData.email) {
      newErrors.email = 'Email обязателен';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Некорректный email';
    }
    
    if (!formData.password) {
      newErrors.password = 'Пароль обязателен';
    } else if (formData.password.length < 6) {
      newErrors.password = 'Пароль должен быть не менее 6 символов';
    }
    
    return newErrors;
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    const validationErrors = validate();
    
    if (Object.keys(validationErrors).length === 0) {
      alert('Форма отправлена успешно!');
      // Очистка формы
      setFormData({ email: '', password: '' });
      setErrors({});
    } else {
      setErrors(validationErrors);
    }
  };
  
  const handleChange = (event) => {
    const { name, value } = event.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <div>
        <input
          type="email"
          name="email"
          placeholder="Email"
          value={formData.email}
          onChange={handleChange}
        />
        {errors.email && <span style={{color: 'red'}}>{errors.email}</span>}
      </div>
      
      <div>
        <input
          type="password"
          name="password"
          placeholder="Пароль"
          value={formData.password}
          onChange={handleChange}
        />
        {errors.password && <span style={{color: 'red'}}>{errors.password}</span>}
      </div>
      
      <button type="submit">Отправить</button>
    </form>
  );
}

export default ValidationForm;
```
Пример 33: Drag and Drop
```jsx
import React, { useState } from 'react';

function DragDrop() {
  const [items, setItems] = useState(['Item 1', 'Item 2', 'Item 3']);
  const [draggedItem, setDraggedItem] = useState(null);
  
  const handleDragStart = (index) => {
    setDraggedItem(index);
  };
  
  const handleDragOver = (event) => {
    event.preventDefault();
  };
  
  const handleDrop = (index) => {
    if (draggedItem === null) return;
    
    const newItems = [...items];
    const item = newItems[draggedItem];
    newItems.splice(draggedItem, 1);
    newItems.splice(index, 0, item);
    
    setItems(newItems);
    setDraggedItem(null);
  };
  
  return (
    <div>
      <h2>Перетащи элементы:</h2>
      {items.map((item, index) => (
        <div
          key={index}
          draggable
          onDragStart={() => handleDragStart(index)}
          onDragOver={handleDragOver}
          onDrop={() => handleDrop(index)}
          style={{
            padding: '10px',
            margin: '5px',
            backgroundColor: '#f0f0f0',
            border: '1px solid #ccc',
            cursor: 'grab'
          }}
        >
          {item}
        </div>
      ))}
    </div>
  );
}

export default DragDrop;
```
Пример 34: Дебаунс поиска
```jsx
import React, { useState, useEffect } from 'react';

function DebounceSearch() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);
  const [loading, setLoading] = useState(false);
  
  // Эффект с дебаунсом
  useEffect(() => {
    if (!query) {
      setResults([]);
      return;
    }
    
    setLoading(true);
    
    const timeoutId = setTimeout(async () => {
      try {
        // Имитация API запроса
        const mockResults = [
          `Результат 1 для "${query}"`,
          `Результат 2 для "${query}"`,
          `Результат 3 для "${query}"`
        ];
        setResults(mockResults);
      } catch (error) {
        console.error('Ошибка поиска:', error);
      } finally {
        setLoading(false);
      }
    }, 500); // Задержка 500ms
    
    // Очистка таймера при каждом изменении query
    return () => clearTimeout(timeoutId);
  }, [query]);
  
  return (
    <div>
      <input
        type="text"
        placeholder="Поиск..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
      />
      
      {loading && <p>Загрузка...</p>}
      
      <ul>
        {results.map((result, index) => (
          <li key={index}>{result}</li>
        ))}
      </ul>
    </div>
  );
}

export default DebounceSearch;
```
Пример 35: Кастомный хук для дебаунса
```jsx
import React, { useState, useEffect } from 'react';

// Кастомный хук useDebounce
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);
  
  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);
    
    return () => {
      clearTimeout(handler);
    };
  }, [value, delay]);
  
  return debouncedValue;
}

function DebounceHookExample() {
  const [searchTerm, setSearchTerm] = useState('');
  const debouncedSearchTerm = useDebounce(searchTerm, 500);
  const [results, setResults] = useState([]);
  
  // Эффект для поиска
  useEffect(() => {
    if (debouncedSearchTerm) {
      // Имитация API запроса
      const mockResults = [
        `Найдено: ${debouncedSearchTerm} 1`,
        `Найдено: ${debouncedSearchTerm} 2`,
        `Найдено: ${debouncedSearchTerm} 3`
      ];
      setResults(mockResults);
    } else {
      setResults([]);
    }
  }, [debouncedSearchTerm]);
  
  return (
    <div>
      <input
        type="text"
        placeholder="Поиск с дебаунсом..."
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
      />
      <ul>
        {results.map((result, index) => (
          <li key={index}>{result}</li>
        ))}
      </ul>
    </div>
  );
}

export default DebounceHookExample;
Часть 5: Контекст (useContext)
```
Пример 36: Создание контекста
```jsx
import React, { createContext, useContext, useState } from 'react';

// Создаем контекст
const ThemeContext = createContext();

// Провайдер темы
function ThemeProvider({ children }) {
  const [isDark, setIsDark] = useState(false);
  
  const toggleTheme = () => {
    setIsDark(!isDark);
  };
  
  const theme = {
    isDark,
    toggleTheme,
    colors: {
      background: isDark ? '#333' : '#fff',
      text: isDark ? '#fff' : '#333'
    }
  };
  
  return (
    <ThemeContext.Provider value={theme}>
      {children}
    </ThemeContext.Provider>
  );
}

// Компонент, использующий контекст
function ThemedButton() {
  const theme = useContext(ThemeContext);
  
  return (
    <button
      onClick={theme.toggleTheme}
      style={{
        backgroundColor: theme.colors.background,
        color: theme.colors.text,
        padding: '10px 20px',
        border: `2px solid ${theme.colors.text}`
      }}
    >
      Переключить тему
    </button>
  );
}

// Другой компонент, использующий контекст
function ThemedText() {
  const theme = useContext(ThemeContext);
  
  return (
    <p style={{
      color: theme.colors.text,
      backgroundColor: theme.colors.background,
      padding: '20px'
    }}>
      Текущая тема: {theme.isDark ? 'Темная' : 'Светлая'}
    </p>
  );
}

function ContextExample() {
  return (
    <ThemeProvider>
      <div>
        <h1>```
Пример использования Context</h1>
        <ThemedButton />
        <ThemedText />
      </div>
    </ThemeProvider>
  );
}

export default ContextExample;
```
Пример 37: Контекст пользователя
```jsx
import React, { createContext, useContext, useState } from 'react';

const UserContext = createContext();

function UserProvider({ children }) {
  const [user, setUser] = useState(null);
  const [isLoading, setIsLoading] = useState(false);
  
  const login = async (email, password) => {
    setIsLoading(true);
    // Имитация API запроса
    setTimeout(() => {
      setUser({
        id: 1,
        name: 'Иван Иванов',
        email: email
      });
      setIsLoading(false);
    }, 1000);
  };
  
  const logout = () => {
    setUser(null);
  };
  
  const value = {
    user,
    isLoading,
    login,
    logout,
    isAuthenticated: !!user
  };
  
  return (
    <UserContext.Provider value={value}>
      {children}
    </UserContext.Provider>
  );
}

function LoginForm() {
  const { login, isLoading } = useContext(UserContext);
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    login(email, password);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        placeholder="Email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
      />
      <input
        type="password"
        placeholder="Пароль"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
      <button type="submit" disabled={isLoading}>
        {isLoading ? 'Вход...' : 'Войти'}
      </button>
    </form>
  );
}

function UserProfile() {
  const { user, logout } = useContext(UserContext);
  
  return (
    <div>
      <h2>Профиль пользователя</h2>
      <p>Имя: {user.name}</p>
      <p>Email: {user.email}</p>
      <button onClick={logout}>Выйти</button>
    </div>
  );
}

function App() {
  const { isAuthenticated } = useContext(UserContext);
  
  return (
    <div>
      <h1>Мое приложение</h1>
      {isAuthenticated ? <UserProfile /> : <LoginForm />}
    </div>
  );
}

export default function WrappedApp() {
  return (
    <UserProvider>
      <App />
    </UserProvider>
  );
}
Часть 6: useReducer
```
Пример 38: Простой useReducer
```jsx
import React, { useReducer } from 'react';

// Начальное состояние
const initialState = { count: 0 };

// Редуктор - функция, определяющая как обновлять состояние
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    case 'set':
      return { count: action.payload };
    default:
      throw new Error('Неизвестное действие');
  }
}

function CounterReducer() {
  // useReducer возвращает текущее состояние и функцию dispatch
  const [state, dispatch] = useReducer(reducer, initialState);
  
  return (
    <div>
      <h2>Счетчик: {state.count}</h2>
      <button onClick={() => dispatch({ type: 'increment' })}>
        +
      </button>
      <button onClick={() => dispatch({ type: 'decrement' })}>
        -
      </button>
      <button onClick={() => dispatch({ type: 'reset' })}>
        Сбросить
      </button>
      <button onClick={() => dispatch({ type: 'set', payload: 10 })}>
        Установить 10
      </button>
    </div>
  );
}

export default CounterReducer;
```
Пример 39: Сложный useReducer для Todo
```jsx
import React, { useReducer, useState } from 'react';

// Начальное состояние
const initialState = {
  todos: [],
  filter: 'all' // all, active, completed
};

// Редуктор
function todoReducer(state, action) {
  switch (action.type) {
    case 'ADD_TODO':
      return {
        ...state,
        todos: [...state.todos, {
          id: Date.now(),
          text: action.payload,
          completed: false
        }]
      };
      
    case 'TOGGLE_TODO':
      return {
        ...state,
        todos: state.todos.map(todo =>
          todo.id === action.payload
            ? { ...todo, completed: !todo.completed }
            : todo
        )
      };
      
    case 'DELETE_TODO':
      return {
        ...state,
        todos: state.todos.filter(todo => todo.id !== action.payload)
      };
      
    case 'SET_FILTER':
      return {
        ...state,
        filter: action.payload
      };
      
    default:
      return state;
  }
}

function TodoApp() {
  const [state, dispatch] = useReducer(todoReducer, initialState);
  const [inputValue, setInputValue] = useState('');
  
  const addTodo = () => {
    if (inputValue.trim()) {
      dispatch({ type: 'ADD_TODO', payload: inputValue });
      setInputValue('');
    }
  };
  
  const filteredTodos = state.todos.filter(todo => {
    if (state.filter === 'active') return !todo.completed;
    if (state.filter === 'completed') return todo.completed;
    return true;
  });
  
  return (
    <div>
      <h2>Список задач</h2>
      
      <div>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Новая задача"
        />
        <button onClick={addTodo}>Добавить</button>
      </div>
      
      <div>
        <button onClick={() => dispatch({ type: 'SET_FILTER', payload: 'all' })}>
          Все
        </button>
        <button onClick={() => dispatch({ type: 'SET_FILTER', payload: 'active' })}>
          Активные
        </button>
        <button onClick={() => dispatch({ type: 'SET_FILTER', payload: 'completed' })}>
          Завершенные
        </button>
      </div>
      
      <ul>
        {filteredTodos.map(todo => (
          <li key={todo.id}>
            <span
              style={{
                textDecoration: todo.completed ? 'line-through' : 'none',
                cursor: 'pointer'
              }}
              onClick={() => dispatch({ type: 'TOGGLE_TODO', payload: todo.id })}
            >
              {todo.text}
            </span>
            <button onClick={() => dispatch({ type: 'DELETE_TODO', payload: todo.id })}>
              Удалить
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TodoApp;
Часть 7: Кастомные хуки
```
Пример 40: Кастомный хук useToggle
```jsx
import React, { useState } from 'react';

// Кастомный хук для переключения boolean значения
function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);
  
  const toggle = () => {
    setValue(prev => !prev);
  };
  
  const setTrue = () => {
    setValue(true);
  };
  
  const setFalse = () => {
    setValue(false);
  };
  
  return [value, toggle, setTrue, setFalse];
}

function ToggleExample() {
  const [isOn, toggle, turnOn, turnOff] = useToggle(false);
  
  return (
    <div>
      <p>Статус: {isOn ? 'ВКЛ' : 'ВЫКЛ'}</p>
      <button onClick={toggle}>Переключить</button>
      <button onClick={turnOn}>Включить</button>
      <button onClick={turnOff}>Выключить</button>
      
      <div style={{
        width: '100px',
        height: '100px',
        backgroundColor: isOn ? 'green' : 'red',
        margin: '20px auto'
      }} />
    </div>
  );
}

export default ToggleExample;
```
Пример 41: Кастомный хук useFetch
```jsx
import React, { useState, useEffect } from 'react';

// Кастомный хук для выполнения запросов
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  useEffect(() => {
    const fetchData = async () => {
      try {
        setLoading(true);
        setError(null);
        
        const response = await fetch(url);
        if (!response.ok) {
          throw new Error('Ошибка сети');
        }
        
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    
    fetchData();
  }, [url]); // Зависимость от url
  
  return { data, loading, error };
}

function FetchExample() {
  const [postId, setPostId] = useState(1);
  const { data: post, loading, error } = useFetch(
    `https://jsonplaceholder.typicode.com/posts/${postId}`
  );
  
  if (loading) return <div>Загрузка...</div>;
  if (error) return <div>Ошибка: {error}</div>;
  
  return (
    <div>
      <h2>Пост #{postId}</h2>
      <div>
        <button onClick={() => setPostId(1)}>Пост 1</button>
        <button onClick={() => setPostId(2)}>Пост 2</button>
        <button onClick={() => setPostId(3)}>Пост 3</button>
      </div>
      
      {post && (
        <div>
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </div>
      )}
    </div>
  );
}

export default FetchExample;
```
Пример 42: Кастомный хук useLocalStorage
```jsx
import React, { useState, useEffect } from 'react';

// Кастомный хук для работы с localStorage
function useLocalStorage(key, initialValue) {
  // Функция для получения начального значения из localStorage
  const [value, setValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(`Ошибка чтения localStorage ключа "${key}":`, error);
      return initialValue;
    }
  });
  
  // Эффект для сохранения значения в localStorage при изменении
  useEffect(() => {
    try {
      window.localStorage.setItem(key, JSON.stringify(value));
    } catch (error) {
      console.error(`Ошибка записи в localStorage ключа "${key}":`, error);
    }
  }, [key, value]);
  
  return [value, setValue];
}

function LocalStorageHook() {
  const [name, setName] = useLocalStorage('userName', '');
  const [theme, setTheme] = useLocalStorage('theme', 'light');
  
  return (
    <div style={{
      backgroundColor: theme === 'dark' ? '#333' : '#fff',
      color: theme === 'dark' ? '#fff' : '#333',
      padding: '20px',
      minHeight: '100vh'
    }}>
      <h2>Кастомный хук useLocalStorage</h2>
      
      <div>
        <input
          type="text"
          placeholder="Введите имя"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />
        <p>Привет, {name || 'незнакомец'}!</p>
      </div>
      
      <div>
        <button onClick={() => setTheme('light')}>Светлая тема</button>
        <button onClick={() => setTheme('dark')}>Темная тема</button>
        <p>Текущая тема: {theme}</p>
      </div>
      
      <p>Данные сохраняются в localStorage и восстанавливаются при перезагрузке</p>
    </div>
  );
}

export default LocalStorageHook;
Часть 8: Оптимизация
```
Пример 43: React.memo
```jsx
import React, { useState, memo } from 'react';

// Компонент обернут в memo для предотвращения лишних рендеров
const ExpensiveComponent = memo(({ value, onClick }) => {
  console.log('ExpensiveComponent rendered');
  
  // Имитация тяжелых вычислений
  const expensiveValue = value * 2;
  
  return (
    <div>
      <p>Значение: {value}</p>
      <p>Удвоенное значение: {expensiveValue}</p>
      <button onClick={onClick}>Обновить</button>
    </div>
  );
});

function MemoExample() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState('');
  
  const handleClick = () => {
    setCount(count + 1);
  };
  
  return (
    <div>
      <h2>React.memo ```
Пример</h2>
      
      <input
        type="text"
        placeholder="Введите текст..."
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      
      {/* ExpensiveComponent не будет перерендериваться при изменении text */}
      <ExpensiveComponent value={count} onClick={handleClick} />
      
      <p>Текст: {text}</p>
    </div>
  );
}

export default MemoExample;
```
Пример 44: useCallback
```jsx
import React, { useState, useCallback, memo } from 'react';

const Button = memo(({ onClick, children }) => {
  console.log(`Button "${children}" rendered`);
  
  return (
    <button onClick={onClick} style={{ margin: '5px' }}>
      {children}
    </button>
  );
});

function CallbackExample() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState('');
  
  // Без useCallback эта функция создается заново при каждом рендере
  const increment = useCallback(() => {
    setCount(prev => prev + 1);
  }, []); // Зависимости пусты - функция создается один раз
  
  const decrement = useCallback(() => {
    setCount(prev => prev - 1);
  }, []);
  
  const reset = useCallback(() => {
    setCount(0);
  }, []);
  
  return (
    <div>
      <h2>useCallback ```
Пример</h2>
      <p>Счетчик: {count}</p>
      
      <Button onClick={increment}>Увеличить</Button>
      <Button onClick={decrement}>Уменьшить</Button>
      <Button onClick={reset}>Сбросить</Button>
      
      <input
        type="text"
        placeholder="Введите текст..."
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      
      <p>Текст: {text}</p>
    </div>
  );
}

export default CallbackExample;
```
Пример 45: useMemo
```jsx
import React, { useState, useMemo } from 'react';

function MemoizedCalculation() {
  const [number, setNumber] = useState(1);
  const [text, setText] = useState('');
  
  // useMemo кэширует результат вычислений
  const expensiveCalculation = useMemo(() => {
    console.log('Выполняется тяжелое вычисление...');
    
    // Имитация тяжелых вычислений
    let result = 0;
    for (let i = 0; i < 100000000; i++) {
      result += number;
    }
    
    return result;
  }, [number]); // Пересчитывается только при изменении number
  
  return (
    <div>
      <h2>useMemo ```
Пример</h2>
      
      <div>
        <input
          type="number"
          value={number}
          onChange={(e) => setNumber(Number(e.target.value))}
        />
        <p>Результат вычисления: {expensiveCalculation}</p>
      </div>
      
      <div>
        <input
          type="text"
          placeholder="Введите текст..."
          value={text}
          onChange={(e) => setText(e.target.value)}
        />
        <p>Текст: {text}</p>
      </div>
      
      <p>Изменение текста не вызывает пересчет expensiveCalculation</p>
    </div>
  );
}

export default MemoizedCalculation;
Часть 9: Формы и управление состоянием
```
Пример 46: Управляемая форма
```jsx
import React, { useState } from 'react';

function ControlledForm() {
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: '',
    gender: '',
    newsletter: false,
    country: ''
  });
  
  const handleChange = (event) => {
    const { name, value, type, checked } = event.target;
    
    setFormData(prevData => ({
      ...prevData,
      [name]: type === 'checkbox' ? checked : value
    }));
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Данные формы:', formData);
    alert('Форма отправлена! Проверьте консоль.');
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <h2>Регистрация</h2>
      
      <div>
        <input
          type="text"
          name="firstName"
          placeholder="Имя"
          value={formData.firstName}
          onChange={handleChange}
          required
        />
      </div>
      
      <div>
        <input
          type="text"
          name="lastName"
          placeholder="Фамилия"
          value={formData.lastName}
          onChange={handleChange}
          required
        />
      </div>
      
      <div>
        <input
          type="email"
          name="email"
          placeholder="Email"
          value={formData.email}
          onChange={handleChange}
          required
        />
      </div>
      
      <div>
        <label>
          <input
            type="radio"
            name="gender"
            value="male"
            checked={formData.gender === 'male'}
            onChange={handleChange}
          />
          Мужской
        </label>
        <label>
          <input
            type="radio"
            name="gender"
            value="female"
            checked={formData.gender === 'female'}
            onChange={handleChange}
          />
          Женский
        </label>
      </div>
      
      <div>
        <select
          name="country"
          value={formData.country}
          onChange={handleChange}
          required
        >
          <option value="">Выберите страну</option>
          <option value="ru">Россия</option>
          <option value="us">США</option>
          <option value="de">Германия</option>
        </select>
      </div>
      
      <div>
        <label>
          <input
            type="checkbox"
            name="newsletter"
            checked={formData.newsletter}
            onChange={handleChange}
          />
          Подписаться на рассылку
        </label>
      </div>
      
      <button type="submit">Зарегистрироваться</button>
      
      <div>
        <h3>Предпросмотр данных:</h3>
        <pre>{JSON.stringify(formData, null, 2)}</pre>
      </div>
    </form>
  );
}

export default ControlledForm;
```
Пример 47: Неуправляемая форма с useRef
```jsx
import React, { useRef } from 'react';

function UncontrolledForm() {
  const nameRef = useRef();
  const emailRef = useRef();
  const fileRef = useRef();
  
  const handleSubmit = (event) => {
    event.preventDefault();
    
    const formData = {
      name: nameRef.current.value,
      email: emailRef.current.value,
      fileName: fileRef.current.files[0]?.name || 'Файл не выбран'
    };
    
    console.log('Данные формы:', formData);
    alert(`Имя: ${formData.name}\nEmail: ${formData.email}\nФайл: ${formData.fileName}`);
    
    // Сброс формы
    event.target.reset();
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <h2>Неуправляемая форма</h2>
      
      <div>
        <input
          type="text"
          ref={nameRef}
          placeholder="Имя"
          defaultValue="" // Начальное значение
        />
      </div>
      
      <div>
        <input
          type="email"
          ref={emailRef}
          placeholder="Email"
          defaultValue=""
        />
      </div>
      
      <div>
        <input
          type="file"
          ref={fileRef}
        />
      </div>
      
      <button type="submit">Отправить</button>
    </form>
  );
}

export default UncontrolledForm;
```
Пример 48: Валидация формы в реальном времени
```jsx
import React, { useState } from 'react';

function RealTimeValidation() {
  const [formData, setFormData] = useState({
    email: '',
    password: '',
    confirmPassword: ''
  });
  
  const [errors, setErrors] = useState({});
  const [touched, setTouched] = useState({});
  
  const validateField = (name, value) => {
    const newErrors = { ...errors };
    
    switch (name) {
      case 'email':
        if (!value) {
          newErrors.email = 'Email обязателен';
        } else if (!/\S+@\S+\.\S+/.test(value)) {
          newErrors.email = 'Некорректный email';
        } else {
          delete newErrors.email;
        }
        break;
        
      case 'password':
        if (!value) {
          newErrors.password = 'Пароль обязателен';
        } else if (value.length < 6) {
          newErrors.password = 'Пароль должен быть не менее 6 символов';
        } else {
          delete newErrors.password;
        }
        break;
        
      case 'confirmPassword':
        if (value !== formData.password) {
          newErrors.confirmPassword = 'Пароли не совпадают';
        } else {
          delete newErrors.confirmPassword;
        }
        break;
        
      default:
        break;
    }
    
    setErrors(newErrors);
  };
  
  const handleChange = (event) => {
    const { name, value } = event.target;
    
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));
    
    // Валидация при изменении
    if (touched[name]) {
      validateField(name, value);
    }
  };
  
  const handleBlur = (event) => {
    const { name } = event.target;
    
    setTouched(prev => ({
      ...prev,
      [name]: true
    }));
    
    validateField(name, formData[name]);
  };
  
  const handleSubmit = (event) => {
    event.preventDefault();
    
    // Проверяем все поля при отправке
    Object.keys(formData).forEach(key => {
      validateField(key, formData[key]);
    });
    
    setTouched({
      email: true,
      password: true,
      confirmPassword: true
    });
    
    if (Object.keys(errors).length === 0) {
      alert('Форма успешно отправлена!');
    }
  };
  
  const isFormValid = Object.keys(errors).length === 0;
  
  return (
    <form onSubmit={handleSubmit}>
      <h2>Регистрация с валидацией</h2>
      
      <div>
        <input
          type="email"
          name="email"
          placeholder="Email"
          value={formData.email}
          onChange={handleChange}
          onBlur={handleBlur}
        />
        {touched.email && errors.email && (
          <span style={{color: 'red'}}>{errors.email}</span>
        )}
      </div>
      
      <div>
        <input
          type="password"
          name="password"
          placeholder="Пароль"
          value={formData.password}
          onChange={handleChange}
          onBlur={handleBlur}
        />
        {touched.password && errors.password && (
          <span style={{color: 'red'}}>{errors.password}</span>
        )}
      </div>
      
      <div>
        <input
          type="password"
          name="confirmPassword"
          placeholder="Подтвердите пароль"
          value={formData.confirmPassword}
          onChange={handleChange}
          onBlur={handleBlur}
        />
        {touched.confirmPassword && errors.confirmPassword && (
          <span style={{color: 'red'}}>{errors.confirmPassword}</span>
        )}
      </div>
      
      <button 
        type="submit" 
        disabled={!isFormValid}
        style={{
          opacity: isFormValid ? 1 : 0.5,
          cursor: isFormValid ? 'pointer' : 'not-allowed'
        }}
      >
        Зарегистрироваться
      </button>
    </form>
  );
}

export default RealTimeValidation;
Часть 10: Продвинутые паттерны
```
Пример 49: Компонент высшего порядка (HOC)
```jsx
import React, { useState, useEffect } from 'react';

// HOC для добавления функциональности загрузки
function withLoading(WrappedComponent) {
  return function WithLoadingComponent(props) {
    const [loading, setLoading] = useState(true);
    
    useEffect(() => {
      // Имитация загрузки
      const timer = setTimeout(() => {
        setLoading(false);
      }, 2000);
      
      return () => clearTimeout(timer);
    }, []);
    
    if (loading) {
      return <div>Загрузка...</div>;
    }
    
    return <WrappedComponent {...props} />;
  };
}

// Обычный компонент
function UserProfile({ user }) {
  return (
    <div>
      <h2>Профиль пользователя</h2>
      <p>Имя: {user.name}</p>
      <p>Email: {user.email}</p>
    </div>
  );
}

// Обернутый компонент с функциональностью загрузки
const UserProfileWithLoading = withLoading(UserProfile);

function HOCExample() {
  const user = {
    name: 'Иван Иванов',
    email: 'ivan@example.com'
  };
  
  return (
    <div>
      <h1>HOC ```
Пример</h1>
      <UserProfileWithLoading user={user} />
    </div>
  );
}

export default HOCExample;
```
Пример 50: Render Props
```jsx
import React, { useState } from 'react';

// Компонент с render prop
function MouseTracker({ render }) {
  const [position, setPosition] = useState({ x: 0, y: 0 });
  
  const handleMouseMove = (event) => {
    setPosition({
      x: event.clientX,
      y: event.clientY
    });
  };
  
  return (
    <div 
      style={{ height: '200px', border: '1px solid #ccc' }}
      onMouseMove={handleMouseMove}
    >
      {render(position)}
    </div>
  );
}

// Компонент, использующий render prop
function RenderPropsExample() {
  return (
    <div>
      <h2>Render Props ```
Пример</h2>
      
      <MouseTracker
        render={({ x, y }) => (
          <div>
            <p>Координаты мыши: {x}, {y}</p>
            <div
              style={{
                position: 'absolute',
                left: x,
                top: y,
                width: '20px',
                height: '20px',
                backgroundColor: 'red',
                borderRadius: '50%',
                transform: 'translate(-50%, -50%)'
              }}
            />
          </div>
        )}
      />
      
      <MouseTracker
        render={({ x, y }) => (
          <p>
            Текущая позиция: X={x}, Y={y}
          </p>
        )}
      />
    </div>
  );
}

export default RenderPropsExample;
```
Пример 51: Компонент портала
```jsx
import React, { useState } from 'react';
import ReactDOM from 'react-dom';

// Модальное окно с использованием портала
function Modal({ isOpen, onClose, children }) {
  if (!isOpen) return null;
  
  return ReactDOM.createPortal(
    <div style={{
      position: 'fixed',
      top: 0,
      left: 0,
      right: 0,
      bottom: 0,
      backgroundColor: 'rgba(0,0,0,0.5)',
      display: 'flex',
      justifyContent: 'center',
      alignItems: 'center',
      zIndex: 1000
    }}>
      <div style={{
        backgroundColor: 'white',
        padding: '20px',
        borderRadius: '8px',
        minWidth: '300px'
      }}>
        {children}
        <button onClick={onClose} style={{ marginTop: '10px' }}>
          Закрыть
        </button>
      </div>
    </div>,
    document.body // Рендерим в body, а не в текущем дереве компонентов
  );
}

function PortalExample() {
  const [isModalOpen, setIsModalOpen] = useState(false);
  
  return (
    <div>
      <h2>Portal ```
Пример</h2>
      <button onClick={() => setIsModalOpen(true)}>
        Открыть модальное окно
      </button>
      
      <Modal 
        isOpen={isModalOpen} 
        onClose={() => setIsModalOpen(false)}
      >
        <h3>Это модальное окно</h3>
        <p>Оно рендерится вне основного DOM дерева с помощью портала!</p>
      </Modal>
    </div>
  );
}

export default PortalExample;
Часть 11: Практические проекты
```
Пример 52: Простое приложение погоды
```jsx
import React, { useState, useEffect } from 'react';

function WeatherApp() {
  const [city, setCity] = useState('Moscow');
  const [weather, setWeather] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  
  const fetchWeather = async (cityName) => {
    setLoading(true);
    setError(null);
    
    try {
      // Имитация API запроса (в реальном приложении используйте реальный API)
      setTimeout(() => {
        const mockWeather = {
          city: cityName,
          temperature: Math.floor(Math.random() * 30) - 5, // -5 to 25
          description: ['Солнечно', 'Облачно', 'Дождь', 'Снег'][Math.floor(Math.random() * 4)],
          humidity: Math.floor(Math.random() * 50) + 50, // 50-100%
          wind: Math.floor(Math.random() * 20) + 1 // 1-20 km/h
        };
        setWeather(mockWeather);
        setLoading(false);
      }, 1000);
    } catch (err) {
      setError('Ошибка загрузки данных');
      setLoading(false);
    }
  };
  
  useEffect(() => {
    fetchWeather(city);
  }, []);
  
  const handleSubmit = (e) => {
    e.preventDefault();
    fetchWeather(city);
  };
  
  return (
    <div style={{ maxWidth: '400px', margin: '0 auto', padding: '20px' }}>
      <h2>Приложение погоды</h2>
      
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={city}
          onChange={(e) => setCity(e.target.value)}
          placeholder="Введите город"
        />
        <button type="submit">Поиск</button>
      </form>
      
      {loading && <p>Загрузка...</p>}
      {error && <p style={{color: 'red'}}>{error}</p>}
      
      {weather && !loading && (
        <div style={{
          marginTop: '20px',
          padding: '20px',
          backgroundColor: '#f5f5f5',
          borderRadius: '8px'
        }}>
          <h3>Погода в {weather.city}</h3>
          <p>Температура: {weather.temperature}°C</p>
          <p>Описание: {weather.description}</p>
          <p>Влажность: {weather.humidity}%</p>
          <p>Ветер: {weather.wind} км/ч</p>
        </div>
      )}
    </div>
  );
}

export default WeatherApp;
```
Пример 53: Приложение для заметок
```jsx
import React, { useState, useEffect } from 'react';

function NotesApp() {
  const [notes, setNotes] = useState([]);
  const [title, setTitle] = useState('');
  const [content, setContent] = useState('');
  const [editIndex, setEditIndex] = useState(null);
  
  // Загрузка заметок из localStorage
  useEffect(() => {
    const savedNotes = localStorage.getItem('notes');
    if (savedNotes) {
      setNotes(JSON.parse(savedNotes));
    }
  }, []);
  
  // Сохранение заметок в localStorage
  useEffect(() => {
    localStorage.setItem('notes', JSON.stringify(notes));
  }, [notes]);
  
  const addNote = () => {
    if (title.trim() && content.trim()) {
      if (editIndex !== null) {
        // Редактирование существующей заметки
        const updatedNotes = [...notes];
        updatedNotes[editIndex] = { title, content, date: new Date().toLocaleDateString() };
        setNotes(updatedNotes);
        setEditIndex(null);
      } else {
        // Добавление новой заметки
        setNotes([...notes, {
          title,
          content,
          date: new Date().toLocaleDateString()
        }]);
      }
      setTitle('');
      setContent('');
    }
  };
  
  const editNote = (index) => {
    const note = notes[index];
    setTitle(note.title);
    setContent(note.content);
    setEditIndex(index);
  };
  
  const deleteNote = (index) => {
    const updatedNotes = notes.filter((_, i) => i !== index);
    setNotes(updatedNotes);
  };
  
  const cancelEdit = () => {
    setTitle('');
    setContent('');
    setEditIndex(null);
  };
  
  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>Мои заметки</h2>
      
      <div style={{ marginBottom: '20px' }}>
        <input
          type="text"
          placeholder="Заголовок заметки"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          style={{ width: '100%', marginBottom: '10px', padding: '8px' }}
        />
        <textarea
          placeholder="Содержание заметки"
          value={content}
          onChange={(e) => setContent(e.target.value)}
          style={{ width: '100%', height: '100px', padding: '8px' }}
        />
        <div>
          <button onClick={addNote}>
            {editIndex !== null ? 'Сохранить изменения' : 'Добавить заметку'}
          </button>
          {editIndex !== null && (
            <button onClick={cancelEdit} style={{ marginLeft: '10px' }}>
              Отмена
            </button>
          )}
        </div>
      </div>
      
      <div>
        {notes.map((note, index) => (
          <div
            key={index}
            style={{
              border: '1px solid #ccc',
              padding: '15px',
              marginBottom: '10px',
              borderRadius: '5px'
            }}
          >
            <h3>{note.title}</h3>
            <p>{note.content}</p>
            <small>Создано: {note.date}</small>
            <div style={{ marginTop: '10px' }}>
              <button onClick={() => editNote(index)}>
                Редактировать
              </button>
              <button 
                onClick={() => deleteNote(index)}
                style={{ marginLeft: '10px', backgroundColor: '#ff4444' }}
              >
                Удалить
              </button>
            </div>
          </div>
        ))}
        
        {notes.length === 0 && (
          <p>Заметок пока нет. Создайте первую!</p>
        )}
      </div>
    </div>
  );
}

export default NotesApp;
Продолжение следует... Я подготовил для вас 53 подробных ```
Примера с объяснениями. Хотите, чтобы я продолжил с оставшимися 147+ ```
Примерами?

да
Отлично! Продолжаем с ```
Примерами React. Вот следующие части:

Часть 12: Работа с API и асинхронными операциями
```
Пример 54: CRUD операции с JSONPlaceholder
```jsx
import React, { useState, useEffect } from 'react';

function ApiCrudExample() {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(false);
  const [newPost, setNewPost] = useState({ title: '', body: '' });

  // GET - получение всех постов
  const fetchPosts = async () => {
    setLoading(true);
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=5');
      const data = await response.json();
      setPosts(data);
    } catch (error) {
      console.error('Ошибка загрузки:', error);
    } finally {
      setLoading(false);
    }
  };

  // POST - создание нового поста
  const createPost = async () => {
    if (!newPost.title || !newPost.body) return;

    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          title: newPost.title,
          body: newPost.body,
          userId: 1,
        }),
      });
      const data = await response.json();
      
      // Добавляем новый пост в начало списка
      setPosts(prev => [data, ...prev]);
      setNewPost({ title: '', body: '' });
      alert('Пост создан!');
    } catch (error) {
      console.error('Ошибка создания:', error);
    }
  };

  // DELETE - удаление поста
  const deletePost = async (postId) => {
    try {
      await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`, {
        method: 'DELETE',
      });
      
      // Удаляем пост из состояния
      setPosts(prev => prev.filter(post => post.id !== postId));
      alert('Пост удален!');
    } catch (error) {
      console.error('Ошибка удаления:', error);
    }
  };

  // PUT - обновление поста
  const updatePost = async (postId) => {
    const postToUpdate = posts.find(post => post.id === postId);
    if (!postToUpdate) return;

    try {
      const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          ...postToUpdate,
          title: `${postToUpdate.title} (обновлено)`,
        }),
      });
      const data = await response.json();
      
      // Обновляем пост в состоянии
      setPosts(prev => prev.map(post => 
        post.id === postId ? data : post
      ));
      alert('Пост обновлен!');
    } catch (error) {
      console.error('Ошибка обновления:', error);
    }
  };

  useEffect(() => {
    fetchPosts();
  }, []);

  if (loading && posts.length === 0) {
    return <div>Загрузка постов...</div>;
  }

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>CRUD операции с API</h2>
      
      {/* Форма создания поста */}
      <div style={{ marginBottom: '30px', padding: '20px', border: '1px solid #ddd' }}>
        <h3>Создать новый пост</h3>
        <input
          type="text"
          placeholder="Заголовок"
          value={newPost.title}
          onChange={(e) => setNewPost(prev => ({ ...prev, title: e.target.value }))}
          style={{ width: '100%', marginBottom: '10px', padding: '8px' }}
        />
        <textarea
          placeholder="Содержание"
          value={newPost.body}
          onChange={(e) => setNewPost(prev => ({ ...prev, body: e.target.value }))}
          style={{ width: '100%', height: '80px', marginBottom: '10px', padding: '8px' }}
        />
        <button onClick={createPost}>Создать пост</button>
      </div>

      {/* Список постов */}
      <div>
        <h3>Список постов ({posts.length})</h3>
        <button onClick={fetchPosts} style={{ marginBottom: '10px' }}>
          Обновить список
        </button>
        
        {posts.map(post => (
          <div
            key={post.id}
            style={{
              border: '1px solid #ccc',
              padding: '15px',
              marginBottom: '10px',
              borderRadius: '5px'
            }}
          >
            <h4>{post.title}</h4>
            <p>{post.body}</p>
            <div>
              <button 
                onClick={() => updatePost(post.id)}
                style={{ marginRight: '10px' }}
              >
                Обновить
              </button>
              <button 
                onClick={() => deletePost(post.id)}
                style={{ backgroundColor: '#ff4444', color: 'white' }}
              >
                Удалить
              </button>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}

export default ApiCrudExample;
```
Пример 55: Пагинация с API
```jsx
import React, { useState, useEffect } from 'react';

function PaginationExample() {
  const [posts, setPosts] = useState([]);
  const [currentPage, setCurrentPage] = useState(1);
  const [totalPages, setTotalPages] = useState(0);
  const [loading, setLoading] = useState(false);
  const postsPerPage = 5;

  const fetchPosts = async (page) => {
    setLoading(true);
    try {
      const response = await fetch(
        `https://jsonplaceholder.typicode.com/posts?_page=${page}&_limit=${postsPerPage}`
      );
      
      // Получаем общее количество постов из заголовков
      const totalCount = response.headers.get('x-total-count');
      setTotalPages(Math.ceil(totalCount / postsPerPage));
      
      const data = await response.json();
      setPosts(data);
    } catch (error) {
      console.error('Ошибка загрузки:', error);
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    fetchPosts(currentPage);
  }, [currentPage]);

  const handlePageChange = (page) => {
    setCurrentPage(page);
  };

  const renderPaginationButtons = () => {
    const buttons = [];
    
    // Кнопка "Назад"
    buttons.push(
      <button
        key="prev"
        onClick={() => handlePageChange(currentPage - 1)}
        disabled={currentPage === 1}
      >
        Назад
      </button>
    );

    // Номера страниц
    for (let i = 1; i <= totalPages; i++) {
      if (
        i === 1 || // Первая страница
        i === totalPages || // Последняя страница
        (i >= currentPage - 1 && i <= currentPage + 1) // Текущая и соседние
      ) {
        buttons.push(
          <button
            key={i}
            onClick={() => handlePageChange(i)}
            style={{
              backgroundColor: currentPage === i ? '#007bff' : 'white',
              color: currentPage === i ? 'white' : 'black'
            }}
          >
            {i}
          </button>
        );
      } else if (i === currentPage - 2 || i === currentPage + 2) {
        // Многоточие для пропущенных страниц
        buttons.push(<span key={i}>...</span>);
      }
    }

    // Кнопка "Вперед"
    buttons.push(
      <button
        key="next"
        onClick={() => handlePageChange(currentPage + 1)}
        disabled={currentPage === totalPages}
      >
        Вперед
      </button>
    );

    return buttons;
  };

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Пагинация с API</h2>
      
      {loading && <div>Загрузка...</div>}
      
      <div style={{ marginBottom: '20px' }}>
        {posts.map(post => (
          <div
            key={post.id}
            style={{
              border: '1px solid #ddd',
              padding: '15px',
              marginBottom: '10px',
              borderRadius: '5px'
            }}
          >
            <h3>{post.title}</h3>
            <p>{post.body}</p>
            <small>ID: {post.id}</small>
          </div>
        ))}
      </div>

      <div style={{ display: 'flex', justifyContent: 'center', gap: '5px' }}>
        {renderPaginationButtons()}
      </div>

      <div style={{ marginTop: '10px', textAlign: 'center' }}>
        Страница {currentPage} из {totalPages}
      </div>
    </div>
  );
}

export default PaginationExample;
```
Пример 56: Бесконечный скролл
```jsx
import React, { useState, useEffect, useCallback } from 'react';

function InfiniteScroll() {
  const [items, setItems] = useState([]);
  const [page, setPage] = useState(1);
  const [loading, setLoading] = useState(false);
  const [hasMore, setHasMore] = useState(true);
  const itemsPerPage = 10;

  const fetchItems = useCallback(async (pageNum) => {
    setLoading(true);
    try {
      // Имитация API запроса
      setTimeout(() => {
        const newItems = Array.from({ length: itemsPerPage }, (_, i) => ({
          id: (pageNum - 1) * itemsPerPage + i + 1,
          name: `Элемент ${(pageNum - 1) * itemsPerPage + i + 1}`,
          description: `Описание элемента ${(pageNum - 1) * itemsPerPage + i + 1}`
        }));

        setItems(prev => [...prev, ...newItems]);
        
        // Предположим, что всего 50 элементов
        if (pageNum >= 5) {
          setHasMore(false);
        }
        
        setLoading(false);
      }, 1000);
    } catch (error) {
      console.error('Ошибка загрузки:', error);
      setLoading(false);
    }
  }, []);

  useEffect(() => {
    fetchItems(page);
  }, [page, fetchItems]);

  // Обработчик скролла
  useEffect(() => {
    const handleScroll = () => {
      if (
        window.innerHeight + document.documentElement.scrollTop !==
          document.documentElement.offsetHeight ||
        loading ||
        !hasMore
      ) {
        return;
      }
      
      setPage(prev => prev + 1);
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, [loading, hasMore]);

  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>Бесконечный скролл</h2>
      
      <div>
        {items.map(item => (
          <div
            key={item.id}
            style={{
              border: '1px solid #ddd',
              padding: '20px',
              marginBottom: '10px',
              borderRadius: '5px',
              backgroundColor: '#f9f9f9'
            }}
          >
            <h3>{item.name}</h3>
            <p>{item.description}</p>
            <small>ID: {item.id}</small>
          </div>
        ))}
      </div>

      {loading && (
        <div style={{ textAlign: 'center', padding: '20px' }}>
          Загрузка...
        </div>
      )}

      {!hasMore && (
        <div style={{ textAlign: 'center', padding: '20px', color: '#666' }}>
          Вы достигли конца списка
        </div>
      )}
    </div>
  );
}

export default InfiniteScroll;
Часть 13: Работа с датами и временем
```
Пример 57: Таймер обратного отсчета
```jsx
import React, { useState, useEffect, useCallback } from 'react';

function CountdownTimer() {
  const [timeLeft, setTimeLeft] = useState(0);
  const [isRunning, setIsRunning] = useState(false);
  const [initialTime, setInitialTime] = useState(300); // 5 минут в секундах

  const startTimer = useCallback((seconds) => {
    setInitialTime(seconds);
    setTimeLeft(seconds);
    setIsRunning(true);
  }, []);

  const resetTimer = () => {
    setIsRunning(false);
    setTimeLeft(initialTime);
  };

  const pauseTimer = () => {
    setIsRunning(false);
  };

  const resumeTimer = () => {
    setIsRunning(true);
  };

  // Форматирование времени в MM:SS
  const formatTime = (seconds) => {
    const mins = Math.floor(seconds / 60);
    const secs = seconds % 60;
    return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
  };

  useEffect(() => {
    let interval;
    
    if (isRunning && timeLeft > 0) {
      interval = setInterval(() => {
        setTimeLeft(prev => prev - 1);
      }, 1000);
    } else if (timeLeft === 0 && isRunning) {
      setIsRunning(false);
      // Можно добавить звуковое оповещение
      alert('Время вышло!');
    }

    return () => clearInterval(interval);
  }, [isRunning, timeLeft]);

  // Проценты для прогресс-бара
  const progress = (timeLeft / initialTime) * 100;

  return (
    <div style={{ maxWidth: '400px', margin: '0 auto', padding: '20px', textAlign: 'center' }}>
      <h2>Таймер обратного отсчета</h2>
      
      {/* Отображение времени */}
      <div style={{ fontSize: '3rem', fontWeight: 'bold', margin: '20px 0' }}>
        {formatTime(timeLeft)}
      </div>

      {/* Прогресс-бар */}
      <div style={{
        width: '100%',
        height: '20px',
        backgroundColor: '#f0f0f0',
        borderRadius: '10px',
        margin: '20px 0',
        overflow: 'hidden'
      }}>
        <div
          style={{
            width: `${progress}%`,
            height: '100%',
            backgroundColor: progress > 20 ? '#4CAF50' : '#f44336',
            transition: 'width 1s linear'
          }}
        />
      </div>

      {/* Кнопки быстрого старта */}
      <div style={{ marginBottom: '20px' }}>
        <button onClick={() => startTimer(60)}>1 минута</button>
        <button onClick={() => startTimer(300)}>5 минут</button>
        <button onClick={() => startTimer(600)}>10 минут</button>
      </div>

      {/* Основные кнопки управления */}
      <div style={{ marginBottom: '20px' }}>
        {!isRunning && timeLeft === initialTime && (
          <button onClick={() => startTimer(initialTime)}>Старт</button>
        )}
        
        {isRunning && (
          <button onClick={pauseTimer}>Пауза</button>
        )}
        
        {!isRunning && timeLeft > 0 && timeLeft < initialTime && (
          <button onClick={resumeTimer}>Продолжить</button>
        )}
        
        <button onClick={resetTimer}>Сброс</button>
      </div>

      {/* Кастомный ввод времени */}
      <div>
        <input
          type="number"
          placeholder="Секунды"
          min="1"
          max="3600"
          onChange={(e) => setInitialTime(Number(e.target.value))}
          style={{ marginRight: '10px', padding: '5px' }}
        />
        <button onClick={() => startTimer(initialTime)}>
          Установить время
        </button>
      </div>
    </div>
  );
}

export default CountdownTimer;
```
Пример 58: Мировые часы
```jsx
import React, { useState, useEffect } from 'react';

function WorldClocks() {
  const [time, setTime] = useState(new Date());
  const [clocks, setClocks] = useState([
    { id: 1, city: 'Москва', timezone: 3, time: '' },
    { id: 2, city: 'Лондон', timezone: 0, time: '' },
    { id: 3, city: 'Нью-Йорк', timezone: -5, time: '' },
    { id: 4, city: 'Токио', timezone: 9, time: '' }
  ]);

  // Обновление времени каждую секунду
  useEffect(() => {
    const timer = setInterval(() => {
      setTime(new Date());
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  // Расчет времени для каждого города
  useEffect(() => {
    const updatedClocks = clocks.map(clock => {
      const utc = time.getTime() + (time.getTimezoneOffset() * 60000);
      const cityTime = new Date(utc + (3600000 * clock.timezone));
      
      return {
        ...clock,
        time: cityTime.toLocaleTimeString('ru-RU')
      };
    });

    setClocks(updatedClocks);
  }, [time]);

  const addClock = () => {
    const cityName = prompt('Введите название города:');
    const timezone = prompt('Введите часовой пояс (на```
Пример, +3 или -5):');
    
    if (cityName && timezone) {
      const newClock = {
        id: Date.now(),
        city: cityName,
        timezone: parseInt(timezone),
        time: ''
      };
      
      setClocks(prev => [...prev, newClock]);
    }
  };

  const removeClock = (id) => {
    setClocks(prev => prev.filter(clock => clock.id !== id));
  };

  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>Мировые часы</h2>
      
      <button onClick={addClock} style={{ marginBottom: '20px' }}>
        Добавить город
      </button>

      <div style={{ display: 'grid', gap: '15px' }}>
        {clocks.map(clock => (
          <div
            key={clock.id}
            style={{
              border: '1px solid #ddd',
              padding: '20px',
              borderRadius: '10px',
              backgroundColor: '#f9f9f9',
              display: 'flex',
              justifyContent: 'space-between',
              alignItems: 'center'
            }}
          >
            <div>
              <h3 style={{ margin: '0 0 5px 0' }}>{clock.city}</h3>
              <p style={{ margin: 0, color: '#666' }}>
                GMT {clock.timezone >= 0 ? '+' : ''}{clock.timezone}
              </p>
            </div>
            
            <div style={{ textAlign: 'right' }}>
              <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>
                {clock.time}
              </div>
            </div>
            
            <button
              onClick={() => removeClock(clock.id)}
              style={{
                backgroundColor: '#ff4444',
                color: 'white',
                border: 'none',
                borderRadius: '5px',
                padding: '5px 10px',
                cursor: 'pointer'
              }}
            >
              ×
            </button>
          </div>
        ))}
      </div>

      {/* Текущее локальное время */}
      <div style={{
        marginTop: '30px',
        padding: '15px',
        backgroundColor: '#e3f2fd',
        borderRadius: '8px',
        textAlign: 'center'
      }}>
        <h3>Ваше локальное время</h3>
        <div style={{ fontSize: '1.2rem' }}>
          {time.toLocaleTimeString('ru-RU')}
        </div>
        <div style={{ color: '#666' }}>
          {time.toLocaleDateString('ru-RU', { 
            weekday: 'long', 
            year: 'numeric', 
            month: 'long', 
            day: 'numeric' 
          })}
        </div>
      </div>
    </div>
  );
}

export default WorldClocks;
Часть 14: Анимации и переходы
```
Пример 59: CSS анимации в React
```jsx
import React, { useState } from 'react';
import './Animations.css'; // Создадим отдельный CSS файл

function CssAnimations() {
  const [isVisible, setIsVisible] = useState(false);
  const [bounce, setBounce] = useState(false);
  const [rotate, setRotate] = useState(false);
  const [pulse, setPulse] = useState(false);

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>CSS Анимации в React</h2>
      
      <div style={{ marginBottom: '20px' }}>
        <button onClick={() => setIsVisible(!isVisible)}>
          {isVisible ? 'Скрыть' : 'Показать'}
        </button>
        <button onClick={() => setBounce(!bounce)} style={{ marginLeft: '10px' }}>
          {bounce ? 'Остановить' : 'Запустить'} bounce
        </button>
        <button onClick={() => setRotate(!rotate)} style={{ marginLeft: '10px' }}>
          {rotate ? 'Остановить' : 'Запустить'} вращение
        </button>
        <button onClick={() => setPulse(!pulse)} style={{ marginLeft: '10px' }}>
          {pulse ? 'Остановить' : 'Запустить'} пульсацию
        </button>
      </div>

      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px' }}>
        {/* Fade In/Out */}
        <div className={`fade-box ${isVisible ? 'fade-in' : 'fade-out'}`}>
          <h3>Fade Animation</h3>
          <p>Плавное появление и исчезновение</p>
        </div>

        {/* Bounce */}
        <div className={`animation-box ${bounce ? 'bounce' : ''}`}>
          <h3>Bounce Animation</h3>
          <p>Прыгающая анимация</p>
        </div>

        {/* Rotate */}
        <div className={`animation-box ${rotate ? 'rotate' : ''}`}>
          <h3>Rotate Animation</h3>
          <p>Вращение элемента</p>
        </div>

        {/* Pulse */}
        <div className={`animation-box ${pulse ? 'pulse' : ''}`}>
          <h3>Pulse Animation</h3>
          <p>Пульсирующий эффект</p>
        </div>

        {/* Slide In */}
        <div className={`slide-box ${isVisible ? 'slide-in-left' : ''}`}>
          <h3>Slide Animation</h3>
          <p>Выдвижение слева</p>
        </div>

        {/* Scale */}
        <div className={`scale-box ${isVisible ? 'scale-up' : 'scale-down'}`}>
          <h3>Scale Animation</h3>
          <p>Увеличение и уменьшение</p>
        </div>
      </div>
    </div>
  );
}

// Создаем файл Animations.css
const animationsCSS = `
.animation-box {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 8px;
  text-align: center;
  background: white;
  transition: all 0.3s ease;
}

.fade-box {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 8px;
  text-align: center;
  background: white;
}

.fade-in {
  opacity: 1;
  transition: opacity 0.5s ease-in;
}

.fade-out {
  opacity: 0;
  transition: opacity 0.5s ease-out;
}

.bounce {
  animation: bounce 0.5s infinite alternate;
}

@keyframes bounce {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(-10px);
  }
}

.rotate {
  animation: rotate 2s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.pulse {
  animation: pulse 1s ease-in-out infinite alternate;
}

@keyframes pulse {
  from {
    transform: scale(1);
    box-shadow: 0 0 0 0 rgba(0, 123, 255, 0.7);
  }
  to {
    transform: scale(1.05);
    box-shadow: 0 0 0 10px rgba(0, 123, 255, 0);
  }
}

.slide-box {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 8px;
  text-align: center;
  background: white;
  transform: translateX(-100%);
  transition: transform 0.5s ease;
}

.slide-in-left {
  transform: translateX(0);
}

.scale-box {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 8px;
  text-align: center;
  background: white;
  transition: transform 0.3s ease;
}

.scale-up {
  transform: scale(1.1);
}

.scale-down {
  transform: scale(0.9);
}
`;

// Для демонстрации добавляем стили в документ
const styleSheet = document.styleSheets[0];
styleSheet.insertRule(animationsCSS, styleSheet.cssRules.length);

export default CssAnimations;
```
Пример 60: Анимация появления списка
```jsx
import React, { useState } from 'react';

function ListAnimations() {
  const [items, setItems] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const addItem = () => {
    if (inputValue.trim()) {
      const newItem = {
        id: Date.now(),
        text: inputValue,
        completed: false
      };
      
      setItems(prev => [newItem, ...prev]);
      setInputValue('');
    }
  };

  const toggleItem = (id) => {
    setItems(prev => 
      prev.map(item => 
        item.id === id ? { ...item, completed: !item.completed } : item
      )
    );
  };

  const removeItem = (id) => {
    setItems(prev => prev.filter(item => item.id !== id));
  };

  const handleKeyPress = (e) => {
    if (e.key === 'Enter') {
      addItem();
    }
  };

  return (
    <div style={{ maxWidth: '500px', margin: '0 auto', padding: '20px' }}>
      <h2>Анимированный список задач</h2>
      
      <div style={{ marginBottom: '20px' }}>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          onKeyPress={handleKeyPress}
          placeholder="Введите задачу..."
          style={{
            width: '70%',
            padding: '10px',
            marginRight: '10px',
            border: '1px solid #ddd',
            borderRadius: '4px'
          }}
        />
        <button
          onClick={addItem}
          style={{
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Добавить
        </button>
      </div>

      <div>
        {items.map((item, index) => (
          <div
            key={item.id}
            style={{
              padding: '15px',
              marginBottom: '8px',
              backgroundColor: item.completed ? '#d4edda' : '#f8f9fa',
              border: `1px solid ${item.completed ? '#c3e6cb' : '#ddd'}`,
              borderRadius: '4px',
              display: 'flex',
              justifyContent: 'space-between',
              alignItems: 'center',
              animation: `slideIn 0.3s ease ${index * 0.1}s both`,
              opacity: 0,
              transform: 'translateX(-20px)'
            }}
          >
            <div
              style={{
                textDecoration: item.completed ? 'line-through' : 'none',
                color: item.completed ? '#6c757d' : '#212529',
                cursor: 'pointer',
                flex: 1
              }}
              onClick={() => toggleItem(item.id)}
            >
              {item.text}
            </div>
            
            <button
              onClick={() => removeItem(item.id)}
              style={{
                backgroundColor: '#dc3545',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                padding: '5px 10px',
                cursor: 'pointer',
                marginLeft: '10px'
              }}
            >
              Удалить
            </button>
          </div>
        ))}
      </div>

      {items.length === 0 && (
        <div style={{
          textAlign: 'center',
          color: '#6c757d',
          padding: '40px',
          border: '2px dashed #ddd',
          borderRadius: '8px'
        }}>
          Список задач пуст. Добавьте первую задачу!
        </div>
      )}

      <style>
        {`
          @keyframes slideIn {
            from {
              opacity: 0;
              transform: translateX(-20px);
            }
            to {
              opacity: 1;
              transform: translateX(0);
            }
          }
        `}
      </style>
    </div>
  );
}

export default ListAnimations;
Часть 15: Работа с файлами
```
Пример 61: Загрузка файлов
```jsx
import React, { useState, useRef } from 'react';

function FileUpload() {
  const [files, setFiles] = useState([]);
  const [previews, setPreviews] = useState([]);
  const [uploadProgress, setUploadProgress] = useState({});
  const fileInputRef = useRef();

  const handleFileSelect = (event) => {
    const selectedFiles = Array.from(event.target.files);
    
    // Создаем превью для изображений
    const newPreviews = selectedFiles.map(file => {
      if (file.type.startsWith('image/')) {
        return {
          file,
          preview: URL.createObjectURL(file),
          type: 'image'
        };
      } else {
        return {
          file,
          preview: null,
          type: 'file'
        };
      }
    });

    setFiles(prev => [...prev, ...selectedFiles]);
    setPreviews(prev => [...prev, ...newPreviews]);
  };

  const simulateUpload = (file, index) => {
    setUploadProgress(prev => ({
      ...prev,
      [index]: 0
    }));

    const interval = setInterval(() => {
      setUploadProgress(prev => {
        const newProgress = (prev[index] || 0) + Math.random() * 10;
        
        if (newProgress >= 100) {
          clearInterval(interval);
          return {
            ...prev,
            [index]: 100
          };
        }
        
        return {
          ...prev,
          [index]: newProgress
        };
      });
    }, 200);
  };

  const handleUpload = () => {
    files.forEach((file, index) => {
      simulateUpload(file, index);
    });
  };

  const removeFile = (index) => {
    setFiles(prev => prev.filter((_, i) => i !== index));
    setPreviews(prev => {
      const newPreviews = prev.filter((_, i) => i !== index);
      // Освобождаем URL объекта для предотвращения утечек памяти
      if (prev[index]?.preview) {
        URL.revokeObjectURL(prev[index].preview);
      }
      return newPreviews;
    });
    
    setUploadProgress(prev => {
      const newProgress = { ...prev };
      delete newProgress[index];
      return newProgress;
    });
  };

  const clearAll = () => {
    setFiles([]);
    setPreviews([]);
    setUploadProgress({});
    
    // Освобождаем все URL объектов
    previews.forEach(preview => {
      if (preview.preview) {
        URL.revokeObjectURL(preview.preview);
      }
    });
  };

  const getFileIcon = (fileType) => {
    if (fileType.startsWith('image/')) return '🖼️';
    if (fileType.includes('pdf')) return '📄';
    if (fileType.includes('word')) return '📝';
    if (fileType.includes('zip')) return '📦';
    return '📁';
  };

  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>Загрузка файлов</h2>
      
      <div
        style={{
          border: '2px dashed #ccc',
          borderRadius: '8px',
          padding: '40px',
          textAlign: 'center',
          marginBottom: '20px',
          cursor: 'pointer'
        }}
        onClick={() => fileInputRef.current?.click()}
      >
        <div style={{ fontSize: '3rem', marginBottom: '10px' }}>📁</div>
        <p>Нажмите для выбора файлов или перетащите их сюда</p>
        <input
          ref={fileInputRef}
          type="file"
          multiple
          onChange={handleFileSelect}
          style={{ display: 'none' }}
        />
      </div>

      {/* Кнопки управления */}
      <div style={{ marginBottom: '20px' }}>
        <button
          onClick={handleUpload}
          disabled={files.length === 0}
          style={{ marginRight: '10px' }}
        >
          Загрузить все файлы
        </button>
        <button
          onClick={clearAll}
          disabled={files.length === 0}
        >
          Очистить все
        </button>
      </div>

      {/* Список файлов */}
      <div>
        {previews.map((preview, index) => (
          <div
            key={index}
            style={{
              border: '1px solid #ddd',
              borderRadius: '8px',
              padding: '15px',
              marginBottom: '10px',
              display: 'flex',
              alignItems: 'center',
              justifyContent: 'space-between'
            }}
          >
            <div style={{ display: 'flex', alignItems: 'center', flex: 1 }}>
              {preview.type === 'image' ? (
                <img
                  src={preview.preview}
                  alt="Preview"
                  style={{
                    width: '50px',
                    height: '50px',
                    objectFit: 'cover',
                    borderRadius: '4px',
                    marginRight: '15px'
                  }}
                />
              ) : (
                <div
                  style={{
                    width: '50px',
                    height: '50px',
                    backgroundColor: '#f0f0f0',
                    borderRadius: '4px',
                    display: 'flex',
                    alignItems: 'center',
                    justifyContent: 'center',
                    fontSize: '1.5rem',
                    marginRight: '15px'
                  }}
                >
                  {getFileIcon(files[index].type)}
                </div>
              )}
              
              <div style={{ flex: 1 }}>
                <div style={{ fontWeight: 'bold' }}>
                  {files[index].name}
                </div>
                <div style={{ color: '#666', fontSize: '0.9rem' }}>
                  {(files[index].size / 1024 / 1024).toFixed(2)} MB
                </div>
                
                {/* Прогресс бар */}
                {uploadProgress[index] !== undefined && (
                  <div style={{ marginTop: '5px' }}>
                    <div
                      style={{
                        width: '100%',
                        height: '6px',
                        backgroundColor: '#f0f0f0',
                        borderRadius: '3px',
                        overflow: 'hidden'
                      }}
                    >
                      <div
                        style={{
                          width: `${uploadProgress[index]}%`,
                          height: '100%',
                          backgroundColor: uploadProgress[index] === 100 ? '#4CAF50' : '#2196F3',
                          transition: 'width 0.3s ease'
                        }}
                      />
                    </div>
                    <div style={{ fontSize: '0.8rem', color: '#666', marginTop: '2px' }}>
                      {Math.min(uploadProgress[index], 100).toFixed(0)}%
                    </div>
                  </div>
                )}
              </div>
            </div>
            
            <button
              onClick={() => removeFile(index)}
              style={{
                backgroundColor: '#ff4444',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                padding: '5px 10px',
                cursor: 'pointer',
                marginLeft: '10px'
              }}
            >
              Удалить
            </button>
          </div>
        ))}
      </div>

      {files.length === 0 && (
        <div style={{ textAlign: 'center', color: '#666', padding: '40px' }}>
          Файлы не выбраны
        </div>
      )}

      <div style={{ marginTop: '20px', color: '#666', fontSize: '0.9rem' }}>
        Выбрано файлов: {files.length}
      </div>
    </div>
  );
}

export default FileUpload;
Продолжаем! Следующие части будут включать более сложные ```
Примеры: работа с графиками, геолокацией, WebSocket, PWA и многое другое. Хотите продолжить?

да
Отлично! Продолжаем с более сложными и практическими ```
Примерами:

Часть 16: Работа с графиками и визуализацией данных
```
Пример 62: Простой график с CSS
```jsx
import React, { useState, useEffect } from 'react';

function CssChart() {
  const [data, setData] = useState([]);
  const [maxValue, setMaxValue] = useState(0);

  // Генерация случайных данных
  const generateData = () => {
    const newData = Array.from({ length: 7 }, (_, i) => ({
      day: ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'][i],
      value: Math.floor(Math.random() * 100) + 10
    }));
    
    setData(newData);
    setMaxValue(Math.max(...newData.map(item => item.value)));
  };

  useEffect(() => {
    generateData();
  }, []);

  const getBarHeight = (value) => {
    return (value / maxValue) * 100;
  };

  const getBarColor = (value) => {
    const percentage = (value / maxValue) * 100;
    if (percentage > 80) return '#4CAF50';
    if (percentage > 50) return '#2196F3';
    if (percentage > 30) return '#FFC107';
    return '#F44336';
  };

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>График продаж</h2>
      
      <button onClick={generateData} style={{ marginBottom: '20px' }}>
        Обновить данные
      </button>

      <div style={{ 
        display: 'flex', 
        alignItems: 'flex-end', 
        justifyContent: 'space-between',
        height: '300px',
        padding: '20px',
        backgroundColor: '#f8f9fa',
        borderRadius: '8px',
        border: '1px solid #dee2e6'
      }}>
        {data.map((item, index) => (
          <div
            key={index}
            style={{
              display: 'flex',
              flexDirection: 'column',
              alignItems: 'center',
              width: '12%'
            }}
          >
            <div
              style={{
                height: `${getBarHeight(item.value)}%`,
                width: '80%',
                backgroundColor: getBarColor(item.value),
                borderRadius: '4px 4px 0 0',
                transition: 'height 0.5s ease',
                position: 'relative',
                minHeight: '10px'
              }}
            >
              <div
                style={{
                  position: 'absolute',
                  top: '-25px',
                  left: '50%',
                  transform: 'translateX(-50%)',
                  backgroundColor: 'rgba(0,0,0,0.8)',
                  color: 'white',
                  padding: '2px 6px',
                  borderRadius: '4px',
                  fontSize: '12px',
                  whiteSpace: 'nowrap'
                }}
              >
                {item.value}
              </div>
            </div>
            <div style={{ marginTop: '10px', fontWeight: 'bold' }}>
              {item.day}
            </div>
          </div>
        ))}
      </div>

      {/* Легенда */}
      <div style={{ 
        display: 'flex', 
        justifyContent: 'center', 
        marginTop: '20px',
        gap: '20px'
      }}>
        <div style={{ display: 'flex', alignItems: 'center' }}>
          <div style={{
            width: '20px',
            height: '20px',
            backgroundColor: '#F44336',
            marginRight: '5px',
            borderRadius: '2px'
          }}></div>
          <span>Низкие</span>
        </div>
        <div style={{ display: 'flex', alignItems: 'center' }}>
          <div style={{
            width: '20px',
            height: '20px',
            backgroundColor: '#FFC107',
            marginRight: '5px',
            borderRadius: '2px'
          }}></div>
          <span>Средние</span>
        </div>
        <div style={{ display: 'flex', alignItems: 'center' }}>
          <div style={{
            width: '20px',
            height: '20px',
            backgroundColor: '#2196F3',
            marginRight: '5px',
            borderRadius: '2px'
          }}></div>
          <span>Высокие</span>
        </div>
        <div style={{ display: 'flex', alignItems: 'center' }}>
          <div style={{
            width: '20px',
            height: '20px',
            backgroundColor: '#4CAF50',
            marginRight: '5px',
            borderRadius: '2px'
          }}></div>
          <span>Очень высокие</span>
        </div>
      </div>

      {/* Статистика */}
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(4, 1fr)', 
        gap: '10px',
        marginTop: '30px'
      }}>
        <div style={{ textAlign: 'center', padding: '15px', backgroundColor: '#e3f2fd', borderRadius: '8px' }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>
            {Math.max(...data.map(d => d.value))}
          </div>
          <div>Максимум</div>
        </div>
        <div style={{ textAlign: 'center', padding: '15px', backgroundColor: '#f3e5f5', borderRadius: '8px' }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>
            {Math.min(...data.map(d => d.value))}
          </div>
          <div>Минимум</div>
        </div>
        <div style={{ textAlign: 'center', padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '8px' }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>
            {(data.reduce((sum, d) => sum + d.value, 0) / data.length).toFixed(1)}
          </div>
          <div>Среднее</div>
        </div>
        <div style={{ textAlign: 'center', padding: '15px', backgroundColor: '#fff3e0', borderRadius: '8px' }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>
            {data.reduce((sum, d) => sum + d.value, 0)}
          </div>
          <div>Всего</div>
        </div>
      </div>
    </div>
  );
}

export default CssChart;
```
Пример 63: Интерактивная диаграмма
```jsx
import React, { useState, useRef, useEffect } from 'react';

function InteractivePieChart() {
  const [data, setData] = useState([
    { label: 'JavaScript', value: 30, color: '#f7df1e' },
    { label: 'Python', value: 25, color: '#3776ab' },
    { label: 'Java', value: 20, color: '#ed8b00' },
    { label: 'C++', value: 15, color: '#00599c' },
    { label: 'Ruby', value: 10, color: '#cc342d' }
  ]);
  
  const [hoveredSlice, setHoveredSlice] = useState(null);
  const canvasRef = useRef();

  const drawPieChart = () => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    const centerX = canvas.width / 2;
    const centerY = canvas.height / 2;
    const radius = Math.min(centerX, centerY) - 10;

    // Очищаем canvas
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    let startAngle = 0;
    const total = data.reduce((sum, item) => sum + item.value, 0);

    data.forEach((item, index) => {
      const sliceAngle = (2 * Math.PI * item.value) / total;
      const endAngle = startAngle + sliceAngle;

      // Рисуем сегмент
      ctx.beginPath();
      ctx.moveTo(centerX, centerY);
      ctx.arc(centerX, centerY, radius, startAngle, endAngle);
      ctx.closePath();
      
      // Добавляем эффект при наведении
      const isHovered = hoveredSlice === index;
      ctx.fillStyle = isHovered ? lightenColor(item.color, 20) : item.color;
      ctx.fill();

      // Обводка
      ctx.strokeStyle = 'white';
      ctx.lineWidth = 2;
      ctx.stroke();

      // Подписи
      if (item.value / total > 0.1) { // Только для значительных сегментов
        const labelAngle = startAngle + sliceAngle / 2;
        const labelRadius = radius * 0.7;
        const labelX = centerX + Math.cos(labelAngle) * labelRadius;
        const labelY = centerY + Math.sin(labelAngle) * labelRadius;

        ctx.fillStyle = '#333';
        ctx.font = 'bold 14px Arial';
        ctx.textAlign = 'center';
        ctx.textBaseline = 'middle';
        ctx.fillText(item.label, labelX, labelY);

        // Процент
        const percent = ((item.value / total) * 100).toFixed(1);
        ctx.font = '12px Arial';
        ctx.fillText(`${percent}%`, labelX, labelY + 16);
      }

      startAngle = endAngle;
    });
  };

  const lightenColor = (color, percent) => {
    const num = parseInt(color.replace('#', ''), 16);
    const amt = Math.round(2.55 * percent);
    const R = (num >> 16) + amt;
    const G = (num >> 8 & 0x00FF) + amt;
    const B = (num & 0x0000FF) + amt;
    return `#${(
      0x1000000 +
      (R < 255 ? (R < 1 ? 0 : R) : 255) * 0x10000 +
      (G < 255 ? (G < 1 ? 0 : G) : 255) * 0x100 +
      (B < 255 ? (B < 1 ? 0 : B) : 255)
    ).toString(16).slice(1)}`;
  };

  const handleCanvasClick = (event) => {
    const canvas = canvasRef.current;
    const rect = canvas.getBoundingClientRect();
    const x = event.clientX - rect.left;
    const y = event.clientY - rect.top;
    
    const centerX = canvas.width / 2;
    const centerY = canvas.height / 2;
    const radius = Math.min(centerX, centerY) - 10;
    
    // Проверяем, находится ли клик внутри круга
    const distance = Math.sqrt((x - centerX) ** 2 + (y - centerY) ** 2);
    if (distance <= radius) {
      // Находим угол клика
      let angle = Math.atan2(y - centerY, x - centerX);
      if (angle < 0) angle += 2 * Math.PI;
      
      // Находим соответствующий сегмент
      const total = data.reduce((sum, item) => sum + item.value, 0);
      let currentAngle = 0;
      
      for (let i = 0; i < data.length; i++) {
        const sliceAngle = (2 * Math.PI * data[i].value) / total;
        if (angle >= currentAngle && angle < currentAngle + sliceAngle) {
          alert(`Вы выбрали: ${data[i].label}\nЗначение: ${data[i].value}\nДоля: ${((data[i].value / total) * 100).toFixed(1)}%`);
          break;
        }
        currentAngle += sliceAngle;
      }
    }
  };

  const handleMouseMove = (event) => {
    const canvas = canvasRef.current;
    const rect = canvas.getBoundingClientRect();
    const x = event.clientX - rect.left;
    const y = event.clientY - rect.top;
    
    const centerX = canvas.width / 2;
    const centerY = canvas.height / 2;
    const radius = Math.min(centerX, centerY) - 10;
    
    const distance = Math.sqrt((x - centerX) ** 2 + (y - centerY) ** 2);
    
    if (distance <= radius) {
      let angle = Math.atan2(y - centerY, x - centerX);
      if (angle < 0) angle += 2 * Math.PI;
      
      const total = data.reduce((sum, item) => sum + item.value, 0);
      let currentAngle = 0;
      
      for (let i = 0; i < data.length; i++) {
        const sliceAngle = (2 * Math.PI * data[i].value) / total;
        if (angle >= currentAngle && angle < currentAngle + sliceAngle) {
          setHoveredSlice(i);
          canvas.style.cursor = 'pointer';
          return;
        }
        currentAngle += sliceAngle;
      }
    }
    
    setHoveredSlice(null);
    canvas.style.cursor = 'default';
  };

  useEffect(() => {
    drawPieChart();
  }, [data, hoveredSlice]);

  const addDataPoint = () => {
    const label = prompt('Введите название:');
    const value = parseInt(prompt('Введите значение:'));
    
    if (label && !isNaN(value)) {
      const colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4', '#FFEAA7', '#DDA0DD', '#98D8C8'];
      const color = colors[Math.floor(Math.random() * colors.length)];
      
      setData(prev => [...prev, { label, value, color }]);
    }
  };

  const removeDataPoint = (index) => {
    setData(prev => prev.filter((_, i) => i !== index));
  };

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Интерактивная круговая диаграмма</h2>
      
      <div style={{ display: 'flex', gap: '40px', alignItems: 'flex-start' }}>
        {/* Canvas для диаграммы */}
        <div>
          <canvas
            ref={canvasRef}
            width={400}
            height={400}
            onClick={handleCanvasClick}
            onMouseMove={handleMouseMove}
            style={{ 
              border: '1px solid #ddd', 
              borderRadius: '8px',
              cursor: 'pointer'
            }}
          />
        </div>

        {/* Легенда и управление */}
        <div style={{ flex: 1 }}>
          <button 
            onClick={addDataPoint}
            style={{ 
              marginBottom: '20px',
              padding: '10px 20px',
              backgroundColor: '#4CAF50',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Добавить данные
          </button>

          <div style={{ marginBottom: '20px' }}>
            <h3>Легенда:</h3>
            {data.map((item, index) => (
              <div
                key={index}
                style={{
                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'space-between',
                  padding: '8px',
                  backgroundColor: hoveredSlice === index ? '#f0f0f0' : 'transparent',
                  borderRadius: '4px',
                  marginBottom: '5px'
                }}
                onMouseEnter={() => setHoveredSlice(index)}
                onMouseLeave={() => setHoveredSlice(null)}
              >
                <div style={{ display: 'flex', alignItems: 'center' }}>
                  <div
                    style={{
                      width: '20px',
                      height: '20px',
                      backgroundColor: item.color,
                      marginRight: '10px',
                      borderRadius: '2px'
                    }}
                  />
                  <span>{item.label}</span>
                </div>
                <div style={{ display: 'flex', alignItems: 'center', gap: '10px' }}>
                  <span style={{ fontWeight: 'bold' }}>{item.value}</span>
                  <button
                    onClick={() => removeDataPoint(index)}
                    style={{
                      backgroundColor: '#ff4444',
                      color: 'white',
                      border: 'none',
                      borderRadius: '2px',
                      padding: '2px 6px',
                      cursor: 'pointer',
                      fontSize: '12px'
                    }}
                  >
                    ×
                  </button>
                </div>
              </div>
            ))}
          </div>

          {/* Статистика */}
          {hoveredSlice !== null && (
            <div style={{
              padding: '15px',
              backgroundColor: '#e3f2fd',
              borderRadius: '8px',
              border: '2px solid #2196F3'
            }}>
              <h4>Выбранный элемент:</h4>
              <p><strong>Название:</strong> {data[hoveredSlice].label}</p>
              <p><strong>Значение:</strong> {data[hoveredSlice].value}</p>
              <p><strong>Доля:</strong> {((data[hoveredSlice].value / data.reduce((sum, item) => sum + item.value, 0)) * 100).toFixed(1)}%</p>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}

export default InteractivePieChart;
Часть 17: Геолокация и карты
```
Пример 64: Определение местоположения
```jsx
import React, { useState, useEffect } from 'react';

function GeolocationExample() {
  const [location, setLocation] = useState(null);
  const [error, setError] = useState(null);
  const [watchId, setWatchId] = useState(null);
  const [locationsHistory, setLocationsHistory] = useState([]);

  const getCurrentLocation = () => {
    if (!navigator.geolocation) {
      setError('Геолокация не поддерживается вашим браузером');
      return;
    }

    setError(null);
    
    navigator.geolocation.getCurrentPosition(
      (position) => {
        const newLocation = {
          latitude: position.coords.latitude,
          longitude: position.coords.longitude,
          accuracy: position.coords.accuracy,
          timestamp: new Date(position.timestamp).toLocaleTimeString()
        };
        
        setLocation(newLocation);
        setLocationsHistory(prev => [newLocation, ...prev.slice(0, 9)]); // Сохраняем последние 10 местоположений
      },
      (err) => {
        switch (err.code) {
          case err.PERMISSION_DENIED:
            setError('Доступ к геолокации запрещен пользователем');
            break;
          case err.POSITION_UNAVAILABLE:
            setError('Информация о местоположении недоступна');
            break;
          case err.TIMEOUT:
            setError('Время запроса местоположения истекло');
            break;
          default:
            setError('Произошла неизвестная ошибка');
            break;
        }
      },
      {
        enableHighAccuracy: true,
        timeout: 10000,
        maximumAge: 60000
      }
    );
  };

  const startWatching = () => {
    if (!navigator.geolocation) {
      setError('Геолокация не поддерживается вашим браузером');
      return;
    }

    setError(null);
    
    const id = navigator.geolocation.watchPosition(
      (position) => {
        const newLocation = {
          latitude: position.coords.latitude,
          longitude: position.coords.longitude,
          accuracy: position.coords.accuracy,
          timestamp: new Date().toLocaleTimeString(),
          speed: position.coords.speed || 0
        };
        
        setLocation(newLocation);
        setLocationsHistory(prev => [newLocation, ...prev.slice(0, 9)]);
      },
      (err) => {
        setError('Ошибка отслеживания местоположения: ' + err.message);
      },
      {
        enableHighAccuracy: true,
        timeout: 5000,
        maximumAge: 0
      }
    );
    
    setWatchId(id);
  };

  const stopWatching = () => {
    if (watchId) {
      navigator.geolocation.clearWatch(watchId);
      setWatchId(null);
    }
  };

  const getGoogleMapsLink = (lat, lng) => {
    return `https://www.google.com/maps?q=${lat},${lng}`;
  };

  const getOpenStreetMapLink = (lat, lng) => {
    return `https://www.openstreetmap.org/?mlat=${lat}&mlon=${lng}#map=15/${lat}/${lng}`;
  };

  useEffect(() => {
    return () => {
      if (watchId) {
        navigator.geolocation.clearWatch(watchId);
      }
    };
  }, [watchId]);

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Геолокация в React</h2>
      
      <div style={{ marginBottom: '20px' }}>
        <button 
          onClick={getCurrentLocation}
          style={{ marginRight: '10px' }}
        >
          Получить текущее местоположение
        </button>
        
        {!watchId ? (
          <button 
            onClick={startWatching}
            style={{ marginRight: '10px', backgroundColor: '#4CAF50', color: 'white' }}
          >
            Начать отслеживание
          </button>
        ) : (
          <button 
            onClick={stopWatching}
            style={{ marginRight: '10px', backgroundColor: '#f44336', color: 'white' }}
          >
            Остановить отслеживание
          </button>
        )}
      </div>

      {error && (
        <div style={{ 
          padding: '15px', 
          backgroundColor: '#ffebee', 
          border: '1px solid #f44336',
          borderRadius: '4px',
          marginBottom: '20px',
          color: '#c62828'
        }}>
          {error}
        </div>
      )}

      {location && (
        <div style={{ 
          padding: '20px', 
          backgroundColor: '#e8f5e8', 
          border: '1px solid #4CAF50',
          borderRadius: '8px',
          marginBottom: '20px'
        }}>
          <h3>Текущее местоположение:</h3>
          <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '10px' }}>
            <div>
              <p><strong>Широта:</strong> {location.latitude.toFixed(6)}</p>
              <p><strong>Долгота:</strong> {location.longitude.toFixed(6)}</p>
              <p><strong>Точность:</strong> ±{location.accuracy} метров</p>
            </div>
            <div>
              <p><strong>Время:</strong> {location.timestamp}</p>
              {location.speed && <p><strong>Скорость:</strong> {(location.speed * 3.6).toFixed(1)} км/ч</p>}
              <p><strong>Статус:</strong> {watchId ? 'Отслеживается' : 'Единоразово'}</p>
            </div>
          </div>
          
          <div style={{ marginTop: '15px' }}>
            <a 
              href={getGoogleMapsLink(location.latitude, location.longitude)}
              target="_blank"
              rel="noopener noreferrer"
              style={{ marginRight: '15px' }}
            >
              Открыть в Google Maps
            </a>
            <a 
              href={getOpenStreetMapLink(location.latitude, location.longitude)}
              target="_blank"
              rel="noopener noreferrer"
            >
              Открыть в OpenStreetMap
            </a>
          </div>
        </div>
      )}

      {/* История местоположений */}
      {locationsHistory.length > 0 && (
        <div>
          <h3>История местоположений (последние 10):</h3>
          <div style={{ 
            display: 'grid', 
            gap: '10px',
            maxHeight: '300px',
            overflowY: 'auto'
          }}>
            {locationsHistory.map((loc, index) => (
              <div
                key={index}
                style={{
                  padding: '10px',
                  backgroundColor: index === 0 ? '#e3f2fd' : '#f5f5f5',
                  border: '1px solid #ddd',
                  borderRadius: '4px',
                  fontSize: '14px'
                }}
              >
                <div style={{ display: 'flex', justifyContent: 'space-between' }}>
                  <span>
                    {loc.latitude.toFixed(6)}, {loc.longitude.toFixed(6)}
                  </span>
                  <span style={{ color: '#666' }}>{loc.timestamp}</span>
                </div>
                <div style={{ fontSize: '12px', color: '#666' }}>
                  Точность: ±{loc.accuracy}m
                  {loc.speed && ` • Скорость: ${(loc.speed * 3.6).toFixed(1)} км/ч`}
                </div>
              </div>
            ))}
          </div>
        </div>
      )}

      {/* Информация о поддержке */}
      <div style={{ 
        marginTop: '30px', 
        padding: '15px', 
        backgroundColor: '#fff3e0',
        border: '1px solid #ffb300',
        borderRadius: '8px'
      }}>
        <h4>Информация о геолокации:</h4>
        <ul style={{ fontSize: '14px', margin: 0 }}>
          <li>Для работы требуется разрешение на доступ к местоположению</li>
          <li>Точность зависит от устройства и условий</li>
          <li>Отслеживание в реальном времени может разряжать батарею</li>
          <li>Данные не сохраняются на сервере</li>
        </ul>
      </div>
    </div>
  );
}

export default GeolocationExample;
```
Пример 65: Простая карта с маркерами
```jsx
import React, { useState, useEffect, useRef } from 'react';

function SimpleMap() {
  const [markers, setMarkers] = useState([]);
  const [center, setCenter] = useState({ lat: 55.7558, lng: 37.6173 }); // Москва по умолчанию
  const mapRef = useRef();
  const [mapSize, setMapSize] = useState({ width: 800, height: 400 });

  // Имитация карты с помощью CSS и абсолютного позиционирования
  const addMarker = (event) => {
    const rect = mapRef.current.getBoundingClientRect();
    const x = event.clientX - rect.left;
    const y = event.clientY - rect.top;
    
    const lat = center.lat + (rect.height / 2 - y) / 1000;
    const lng = center.lng + (x - rect.width / 2) / 1000;
    
    const newMarker = {
      id: Date.now(),
      lat,
      lng,
      x: (x / rect.width) * 100,
      y: (y / rect.height) * 100,
      title: `Маркер ${markers.length + 1}`,
      description: `Координаты: ${lat.toFixed(4)}, ${lng.toFixed(4)}`
    };
    
    setMarkers(prev => [...prev, newMarker]);
  };

  const removeMarker = (id) => {
    setMarkers(prev => prev.filter(marker => marker.id !== id));
  };

  const clearAllMarkers = () => {
    setMarkers([]);
  };

  const moveMap = (direction) => {
    const moveStep = 0.1;
    
    switch (direction) {
      case 'up':
        setCenter(prev => ({ ...prev, lat: prev.lat + moveStep }));
        break;
      case 'down':
        setCenter(prev => ({ ...prev, lat: prev.lat - moveStep }));
        break;
      case 'left':
        setCenter(prev => ({ ...prev, lng: prev.lng - moveStep }));
        break;
      case 'right':
        setCenter(prev => ({ ...prev, lng: prev.lng + moveStep }));
        break;
      case 'reset':
        setCenter({ lat: 55.7558, lng: 37.6173 });
        break;
      default:
        break;
    }
  };

  const zoomIn = () => {
    setMapSize(prev => ({
      width: prev.width * 1.2,
      height: prev.height * 1.2
    }));
  };

  const zoomOut = () => {
    setMapSize(prev => ({
      width: prev.width / 1.2,
      height: prev.height / 1.2
    }));
  };

  // Имитация загрузки популярных мест
  const loadPopularPlaces = () => {
    const popularPlaces = [
      { lat: 55.7520, lng: 37.6175, title: 'Красная площадь', description: 'Главная площадь Москвы' },
      { lat: 55.7440, lng: 37.6175, title: 'Парк Горького', description: 'Центральный парк культуры и отдыха' },
      { lat: 55.7495, lng: 37.6238, title: 'Храм Василия Блаженного', description: 'Православный храм на Красной площади' },
      { lat: 55.7517, lng: 37.6178, title: 'ГУМ', description: 'Главный универсальный магазин' }
    ];
    
    const newMarkers = popularPlaces.map((place, index) => {
      const rect = mapRef.current?.getBoundingClientRect() || { width: 800, height: 400 };
      const x = ((place.lng - center.lng) * 1000 + rect.width / 2) / rect.width * 100;
      const y = (rect.height / 2 - (place.lat - center.lat) * 1000) / rect.height * 100;
      
      return {
        id: Date.now() + index,
        ...place,
        x,
        y
      };
    });
    
    setMarkers(newMarkers);
  };

  return (
    <div style={{ maxWidth: '1000px', margin: '0 auto', padding: '20px' }}>
      <h2>Интерактивная карта с маркерами</h2>
      
      {/* Элементы управления картой */}
      <div style={{ marginBottom: '20px', display: 'flex', gap: '10px', flexWrap: 'wrap' }}>
        <button onClick={() => moveMap('up')}>↑ Север</button>
        <button onClick={() => moveMap('down')}>↓ Юг</button>
        <button onClick={() => moveMap('left')}>← Запад</button>
        <button onClick={() => moveMap('right')}>→ Восток</button>
        <button onClick={zoomIn}>+ Приблизить</button>
        <button onClick={zoomOut}>- Отдалить</button>
        <button onClick={() => moveMap('reset')}>Сбросить</button>
        <button onClick={loadPopularPlaces}>Загрузить популярные места</button>
        <button onClick={clearAllMarkers} style={{ backgroundColor: '#ff4444', color: 'white' }}>
          Очистить маркеры
        </button>
      </div>

      {/* Карта */}
      <div
        ref={mapRef}
        style={{
          width: `${mapSize.width}px`,
          height: `${mapSize.height}px`,
          backgroundColor: '#aad3df',
          backgroundImage: `
            linear-gradient(#79bcdb 1px, transparent 1px),
            linear-gradient(90deg, #79bcdb 1px, transparent 1px)
          `,
          backgroundSize: '20px 20px',
          border: '2px solid #333',
          borderRadius: '8px',
          position: 'relative',
          cursor: 'crosshair',
          margin: '0 auto',
          overflow: 'hidden'
        }}
        onClick={addMarker}
      >
        {/* Центр карты */}
        <div
          style={{
            position: 'absolute',
            left: '50%',
            top: '50%',
            transform: 'translate(-50%, -50%)',
            width: '4px',
            height: '4px',
            backgroundColor: 'red',
            borderRadius: '50%'
          }}
        />

        {/* Маркеры */}
        {markers.map(marker => (
          <div
            key={marker.id}
            style={{
              position: 'absolute',
              left: `${marker.x}%`,
              top: `${marker.y}%`,
              transform: 'translate(-50%, -100%)',
              cursor: 'pointer'
            }}
            onClick={(e) => {
              e.stopPropagation();
              alert(`${marker.title}\n${marker.description}`);
            }}
          >
            <div
              style={{
                width: '20px',
                height: '20px',
                backgroundColor: '#ff4444',
                borderRadius: '50% 50% 50% 0',
                transform: 'rotate(-45deg)',
                position: 'relative'
              }}
            >
              <div
                style={{
                  position: 'absolute',
                  top: '-30px',
                  left: '50%',
                  transform: 'translateX(-50%)',
                  backgroundColor: 'rgba(0,0,0,0.8)',
                  color: 'white',
                  padding: '5px 10px',
                  borderRadius: '4px',
                  fontSize: '12px',
                  whiteSpace: 'nowrap',
                  transform: 'rotate(45deg)'
                }}
              >
                {marker.title}
              </div>
            </div>
            
            {/* Кнопка удаления маркера */}
            <button
              onClick={(e) => {
                e.stopPropagation();
                removeMarker(marker.id);
              }}
              style={{
                position: 'absolute',
                top: '-10px',
                right: '-10px',
                backgroundColor: '#ff4444',
                color: 'white',
                border: 'none',
                borderRadius: '50%',
                width: '20px',
                height: '20px',
                fontSize: '12px',
                cursor: 'pointer',
                transform: 'rotate(45deg)'
              }}
            >
              ×
            </button>
          </div>
        ))}
      </div>

      {/* Информация о карте */}
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: '1fr 1fr', 
        gap: '20px', 
        marginTop: '20px' 
      }}>
        <div>
          <h3>Информация о карте:</h3>
          <p><strong>Центр карты:</strong> {center.lat.toFixed(4)}, {center.lng.toFixed(4)}</p>
          <p><strong>Количество маркеров:</strong> {markers.length}</p>
          <p><strong>Размер карты:</strong> {mapSize.width} × {mapSize.height}px</p>
        </div>
        
        <div>
          <h3>Инструкция:</h3>
          <ul style={{ fontSize: '14px', margin: 0 }}>
            <li>Кликните на карте, чтобы добавить маркер</li>
            <li>Кликните на маркер, чтобы увидеть информацию</li>
            <li>Используйте кнопки для навигации по карте</li>
            <li>Нажмите × на маркере, чтобы удалить его</li>
          </ul>
        </div>
      </div>

      {/* Список маркеров */}
      {markers.length > 0 && (
        <div style={{ marginTop: '30px' }}>
          <h3>Список маркеров:</h3>
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: 'repeat(auto-fill, minmax(200px, 1fr))', 
            gap: '10px' 
          }}>
            {markers.map(marker => (
              <div
                key={marker.id}
                style={{
                  padding: '10px',
                  backgroundColor: '#f5f5f5',
                  border: '1px solid #ddd',
                  borderRadius: '4px',
                  fontSize: '14px'
                }}
              >
                <div style={{ fontWeight: 'bold' }}>{marker.title}</div>
                <div style={{ fontSize: '12px', color: '#666' }}>{marker.description}</div>
                <div style={{ fontSize: '11px', color: '#999' }}>
                  Координаты: {marker.lat.toFixed(4)}, {marker.lng.toFixed(4)}
                </div>
              </div>
            ))}
          </div>
        </div>
      )}
    </div>
  );
}

export default SimpleMap;
Часть 18: WebSocket и реальное время
```
Пример 66: Простой WebSocket чат
```jsx
import React, { useState, useEffect, useRef } from 'react';

function WebSocketChat() {
  const [messages, setMessages] = useState([]);
  const [inputMessage, setInputMessage] = useState('');
  const [isConnected, setIsConnected] = useState(false);
  const [username, setUsername] = useState('');
  const [users, setUsers] = useState([]);
  const ws = useRef(null);

  // Имитация WebSocket сервера
  const mockWebSocketServer = {
    clients: [],
    
    connect(client) {
      this.clients.push(client);
      client.onOpen();
      
      // Отправляем приветственное сообщение
      setTimeout(() => {
        client.onMessage(JSON.stringify({
          type: 'system',
          message: 'Добро пожаловать в чат!',
          timestamp: new Date().toISOString()
        }));
      }, 100);
    },
    
    disconnect(client) {
      this.clients = this.clients.filter(c => c !== client);
    },
    
    broadcast(message, excludeClient = null) {
      this.clients.forEach(client => {
        if (client !== excludeClient) {
          client.onMessage(message);
        }
      });
    }
  };

  const connectWebSocket = () => {
    if (!username.trim()) {
      alert('Пожалуйста, введите имя пользователя');
      return;
    }

    // Создаем mock WebSocket клиент
    const mockClient = {
      onOpen: () => {
        setIsConnected(true);
        addSystemMessage('Вы подключились к чату');
        
        // Имитируем подключение других пользователей
        setTimeout(() => {
          addSystemMessage('Пользователь Anna подключился к чату');
          setUsers(['Anna', 'Mike', 'John']);
        }, 1000);
      },
      
      onMessage: (data) => {
        const message = JSON.parse(data);
        setMessages(prev => [...prev, message]);
      },
      
      onClose: () => {
        setIsConnected(false);
        addSystemMessage('Соединение закрыто');
      },
      
      send: (data) => {
        const message = JSON.parse(data);
        
        // Добавляем наше сообщение сразу
        setMessages(prev => [...prev, {
          ...message,
          username: username,
          timestamp: new Date().toISOString()
        }]);
        
        // Имитируем ответы других пользователей
        setTimeout(() => {
          const responses = [
            'Привет! Как дела?',
            'Интересное сообщение!',
            'Согласен с тобой',
            'Хорошая мысль!',
            'Расскажи подробнее'
          ];
          
          const randomUser = users[Math.floor(Math.random() * users.length)];
          const randomResponse = responses[Math.floor(Math.random() * responses.length)];
          
          if (randomUser && Math.random() > 0.3) { // 70% шанс ответа
            setMessages(prev => [...prev, {
              type: 'user',
              username: randomUser,
              message: randomResponse,
              timestamp: new Date().toISOString()
            }]);
          }
        }, 1000 + Math.random() * 2000);
      },
      
      close: () => {
        mockWebSocketServer.disconnect(mockClient);
        mockClient.onClose();
      }
    };

    ws.current = mockClient;
    mockWebSocketServer.connect(mockClient);
  };

  const disconnectWebSocket = () => {
    if (ws.current) {
      ws.current.close();
      ws.current = null;
    }
  };

  const sendMessage = () => {
    if (!inputMessage.trim() || !ws.current) return;

    const message = {
      type: 'user',
      message: inputMessage,
      timestamp: new Date().toISOString()
    };

    ws.current.send(JSON.stringify(message));
    setInputMessage('');
  };

  const addSystemMessage = (text) => {
    setMessages(prev => [...prev, {
      type: 'system',
      message: text,
      timestamp: new Date().toISOString()
    }]);
  };

  const handleKeyPress = (e) => {
    if (e.key === 'Enter' && !e.shiftKey) {
      e.preventDefault();
      sendMessage();
    }
  };

  // Автопрокрутка к новым сообщениям
  const messagesEndRef = useRef(null);
  const scrollToBottom = () => {
    messagesEndRef.current?.scrollIntoView({ behavior: 'smooth' });
  };

  useEffect(() => {
    scrollToBottom();
  }, [messages]);

  const formatTime = (timestamp) => {
    return new Date(timestamp).toLocaleTimeString('ru-RU', {
      hour: '2-digit',
      minute: '2-digit'
    });
  };

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>WebSocket Чат (имитация)</h2>
      
      {/* Подключение */}
      {!isConnected ? (
        <div style={{ 
          padding: '20px', 
          backgroundColor: '#fff3e0', 
          borderRadius: '8px',
          marginBottom: '20px'
        }}>
          <h3>Подключение к чату</h3>
          <div style={{ display: 'flex', gap: '10px', alignItems: 'flex-end' }}>
            <div>
              <label style={{ display: 'block', marginBottom: '5px' }}>
                Ваше имя:
              </label>
              <input
                type="text"
                value={username}
                onChange={(e) => setUsername(e.target.value)}
                placeholder="Введите ваше имя"
                style={{ padding: '8px', width: '200px' }}
              />
            </div>
            <button 
              onClick={connectWebSocket}
              style={{
                padding: '8px 20px',
                backgroundColor: '#4CAF50',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Подключиться
            </button>
          </div>
        </div>
      ) : (
        <div style={{ 
          padding: '15px', 
          backgroundColor: '#e8f5e8', 
          borderRadius: '8px',
          marginBottom: '20px',
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center'
        }}>
          <div>
            <strong>Подключен как:</strong> {username} | 
            <strong> Пользователей онлайн:</strong> {users.length + 1}
          </div>
          <button 
            onClick={disconnectWebSocket}
            style={{
              padding: '5px 15px',
              backgroundColor: '#f44336',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            Отключиться
          </button>
        </div>
      )}

      {/* Окно чата */}
      <div
        style={{
          height: '400px',
          border: '1px solid #ddd',
          borderRadius: '8px',
          padding: '15px',
          backgroundColor: '#fafafa',
          overflowY: 'auto',
          marginBottom: '20px',
          display: 'flex',
          flexDirection: 'column'
        }}
      >
        {messages.map((msg, index) => (
          <div
            key={index}
            style={{
              marginBottom: '10px',
              padding: '8px 12px',
              borderRadius: '8px',
              maxWidth: '70%',
              alignSelf: msg.type === 'system' ? 'center' : 
                        msg.username === username ? 'flex-end' : 'flex-start',
              backgroundColor: msg.type === 'system' ? '#e3f2fd' : 
                              msg.username === username ? '#dcf8c6' : '#ffffff',
              border: msg.type === 'system' ? '1px dashed #2196F3' : '1px solid #e0e0e0'
            }}
          >
            {msg.type === 'system' ? (
              <div style={{ 
                textAlign: 'center', 
                color: '#666', 
                fontSize: '0.9rem',
                fontStyle: 'italic'
              }}>
                {msg.message}
              </div>
            ) : (
              <div>
                <div style={{ 
                  fontSize: '0.8rem', 
                  color: '#666',
                  fontWeight: msg.username === username ? 'bold' : 'normal'
                }}>
                  {msg.username} • {formatTime(msg.timestamp)}
                </div>
                <div style={{ marginTop: '2px' }}>
                  {msg.message}
                </div>
              </div>
            )}
          </div>
        ))}
        <div ref={messagesEndRef} />
        
        {messages.length === 0 && isConnected && (
          <div style={{ 
            textAlign: 'center', 
            color: '#999', 
            padding: '40px',
            fontStyle: 'italic'
          }}>
            Начните общение! Напишите первое сообщение.
          </div>
        )}
      </div>

      {/* Форма отправки сообщения */}
      {isConnected && (
        <div style={{ display: 'flex', gap: '10px' }}>
          <textarea
            value={inputMessage}
            onChange={(e) => setInputMessage(e.target.value)}
            onKeyPress={handleKeyPress}
            placeholder="Введите сообщение..."
            style={{
              flex: 1,
              padding: '10px',
              border: '1px solid #ddd',
              borderRadius: '4px',
              resize: 'vertical',
              minHeight: '60px',
              fontFamily: 'inherit'
            }}
          />
          <button
            onClick={sendMessage}
            disabled={!inputMessage.trim()}
            style={{
              padding: '10px 20px',
              backgroundColor: '#4CAF50',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: inputMessage.trim() ? 'pointer' : 'not-allowed',
              opacity: inputMessage.trim() ? 1 : 0.6,
              alignSelf: 'flex-end'
            }}
          >
            Отправить
          </button>
        </div>
      )}

      {/* Список пользователей */}
      {isConnected && users.length > 0 && (
        <div style={{ marginTop: '20px' }}>
          <h4>Пользователи онлайн:</h4>
          <div style={{ display: 'flex', gap: '10px', flexWrap: 'wrap' }}>
            <div style={{
              padding: '5px 10px',
              backgroundColor: '#4CAF50',
              color: 'white',
              borderRadius: '12px',
              fontSize: '0.8rem'
            }}>
              {username} (Вы)
            </div>
            {users.map((user, index) => (
              <div
                key={index}
                style={{
                  padding: '5px 10px',
                  backgroundColor: '#2196F3',
                  color: 'white',
                  borderRadius: '12px',
                  fontSize: '0.8rem'
                }}
              >
                {user}
              </div>
            ))}
          </div>
        </div>
      )}

      {/* Информация */}
      <div style={{ 
        marginTop: '30px', 
        padding: '15px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px',
        fontSize: '0.9rem'
      }}>
        <h4>Информация о чате:</h4>
        <p>Это имитация WebSocket чата. В реальном приложении здесь было бы:</p>
        <ul>
          <li>Настоящее WebSocket соединение с сервером</li>
          <li>Мгновенная доставка сообщений всем участникам</li>
          <li>Статусы пользователей (online/offline)</li>
          <li>Уведомления о наборе текста</li>
          <li>История сообщений</li>
        </ul>
      </div>
    </div>
  );
}

export default WebSocketChat;
Продолжаем! Следующие части будут включать PWA, сервис-воркеры, TypeScript с React, тестирование и многое другое. Хотите, чтобы я продолжил?

да
Отлично! Продолжаем с продвинутыми ```
Примерами:

Часть 19: PWA и сервис-воркеры
```
Пример 67: Простое PWA с офлайн-режимом
```jsx
import React, { useState, useEffect } from 'react';

function SimplePWA() {
  const [isOnline, setIsOnline] = useState(navigator.onLine);
  const [installPrompt, setInstallPrompt] = useState(null);
  const [isInstalled, setIsInstalled] = useState(false);
  const [cachedData, setCachedData] = useState([]);

  // Отслеживание онлайн/офлайн статуса
  useEffect(() => {
    const handleOnline = () => setIsOnline(true);
    const handleOffline = () => setIsOnline(false);

    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);

    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);

  // Обработчик установки PWA
  useEffect(() => {
    const handleBeforeInstallPrompt = (e) => {
      e.preventDefault();
      setInstallPrompt(e);
    };

    window.addEventListener('beforeinstallprompt', handleBeforeInstallPrompt);

    // Проверяем, установлено ли приложение
    if (window.matchMedia('(display-mode: standalone)').matches) {
      setIsInstalled(true);
    }

    return () => {
      window.removeEventListener('beforeinstallprompt', handleBeforeInstallPrompt);
    };
  }, []);

  const handleInstallClick = async () => {
    if (!installPrompt) return;

    installPrompt.prompt();
    const { outcome } = await installPrompt.userChoice;
    
    if (outcome === 'accepted') {
      setInstallPrompt(null);
      setIsInstalled(true);
    }
  };

  // Имитация кэширования данных
  const fetchData = async () => {
    try {
      // Имитация API запроса
      const mockData = [
        { id: 1, title: 'Статья 1', content: 'Содержание статьи 1' },
        { id: 2, title: 'Статья 2', content: 'Содержание статьи 2' },
        { id: 3, title: 'Статья 3', content: 'Содержание статьи 3' },
      ];

      // Сохраняем в кэш (localStorage)
      localStorage.setItem('cachedArticles', JSON.stringify(mockData));
      setCachedData(mockData);
      
      return mockData;
    } catch (error) {
      console.error('Ошибка загрузки данных:', error);
      
      // Пытаемся загрузить из кэша
      const cached = localStorage.getItem('cachedArticles');
      if (cached) {
        setCachedData(JSON.parse(cached));
        return JSON.parse(cached);
      }
      
      return [];
    }
  };

  const clearCache = () => {
    localStorage.removeItem('cachedArticles');
    setCachedData([]);
  };

  useEffect(() => {
    fetchData();
  }, []);

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Простое PWA приложение</h2>
      
      {/* Статус приложения */}
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', 
        gap: '15px',
        marginBottom: '30px'
      }}>
        <div style={{ 
          padding: '15px', 
          backgroundColor: isOnline ? '#e8f5e8' : '#ffebee',
          border: `2px solid ${isOnline ? '#4CAF50' : '#f44336'}`,
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '2rem', marginBottom: '5px' }}>
            {isOnline ? '🟢' : '🔴'}
          </div>
          <div style={{ fontWeight: 'bold' }}>
            {isOnline ? 'Онлайн' : 'Офлайн'}
          </div>
          <div style={{ fontSize: '0.8rem', color: '#666' }}>
            {isOnline ? 'Соединение активно' : 'Работа в офлайн-режиме'}
          </div>
        </div>

        <div style={{ 
          padding: '15px', 
          backgroundColor: isInstalled ? '#e8f5e8' : '#fff3e0',
          border: `2px solid ${isInstalled ? '#4CAF50' : '#ff9800'}`,
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '2rem', marginBottom: '5px' }}>
            {isInstalled ? '📱' : '💻'}
          </div>
          <div style={{ fontWeight: 'bold' }}>
            {isInstalled ? 'Установлено' : 'Браузер'}
          </div>
          <div style={{ fontSize: '0.8rem', color: '#666' }}>
            {isInstalled ? 'Приложение установлено' : 'Работа в браузере'}
          </div>
        </div>

        <div style={{ 
          padding: '15px', 
          backgroundColor: '#e3f2fd',
          border: '2px solid #2196F3',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '2rem', marginBottom: '5px' }}>💾</div>
          <div style={{ fontWeight: 'bold' }}>
            Кэш: {cachedData.length} записей
          </div>
          <div style={{ fontSize: '0.8rem', color: '#666' }}>
            Данные доступны офлайн
          </div>
        </div>
      </div>

      {/* Кнопки управления */}
      <div style={{ marginBottom: '30px', display: 'flex', gap: '10px', flexWrap: 'wrap' }}>
        {installPrompt && !isInstalled && (
          <button
            onClick={handleInstallClick}
            style={{
              padding: '12px 24px',
              backgroundColor: '#2196F3',
              color: 'white',
              border: 'none',
              borderRadius: '6px',
              cursor: 'pointer',
              fontSize: '16px'
            }}
          >
            📱 Установить приложение
          </button>
        )}
        
        <button
          onClick={fetchData}
          style={{
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          🔄 Обновить данные
        </button>
        
        <button
          onClick={clearCache}
          style={{
            padding: '10px 20px',
            backgroundColor: '#ff9800',
            color: 'white',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          🗑️ Очистить кэш
        </button>
      </div>

      {/* Контент */}
      <div>
        <h3>Кэшированный контент:</h3>
        {cachedData.length > 0 ? (
          <div style={{ display: 'grid', gap: '15px' }}>
            {cachedData.map(item => (
              <div
                key={item.id}
                style={{
                  padding: '20px',
                  border: '1px solid #ddd',
                  borderRadius: '8px',
                  backgroundColor: '#f9f9f9'
                }}
              >
                <h4 style={{ margin: '0 0 10px 0' }}>{item.title}</h4>
                <p style={{ margin: 0, color: '#666' }}>{item.content}</p>
                <div style={{ 
                  marginTop: '10px', 
                  fontSize: '0.8rem', 
                  color: '#999',
                  display: 'flex',
                  justifyContent: 'space-between',
                  alignItems: 'center'
                }}>
                  <span>ID: {item.id}</span>
                  <span>{isOnline ? '🟢 Онлайн' : '🔴 Офлайн'}</span>
                </div>
              </div>
            ))}
          </div>
        ) : (
          <div style={{ 
            padding: '40px', 
            textAlign: 'center', 
            color: '#666',
            border: '2px dashed #ddd',
            borderRadius: '8px'
          }}>
            <div style={{ fontSize: '3rem', marginBottom: '10px' }}>📭</div>
            <p>Нет кэшированных данных</p>
            <button
              onClick={fetchData}
              style={{
                padding: '8px 16px',
                backgroundColor: '#2196F3',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Загрузить данные
            </button>
          </div>
        )}
      </div>

      {/* Информация о PWA */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>О PWA (Progressive Web App)</h3>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '15px' }}>
          <div>
            <h4>🔄 Офлайн-работа</h4>
            <p>Приложение работает без интернета благодаря сервис-воркерам</p>
          </div>
          <div>
            <h4>📱 Установка</h4>
            <p>Можно установить на устройство как нативное приложение</p>
          </div>
          <div>
            <h4>⚡ Быстрая загрузка</h4>
            <p>Кэширование ресурсов для мгновенной загрузки</p>
          </div>
          <div>
            <h4>🔔 Уведомления</h4>
            <p>Поддержка push-уведомлений</p>
          </div>
        </div>
      </div>

      {/* Инструкция по установке */}
      {!isInstalled && (
        <div style={{ 
          marginTop: '20px', 
          padding: '15px', 
          backgroundColor: '#fff3e0',
          border: '1px solid #ffb300',
          borderRadius: '8px'
        }}>
          <h4>Как установить PWA:</h4>
          <ul style={{ margin: 0, paddingLeft: '20px' }}>
            <li>Нажмите кнопку "Установить приложение" выше</li>
            <li>Или в меню браузера выберите "Установить приложение"</li>
            <li>На iOS: нажмите "Поделиться" и выберите "На экран «Домой»"</li>
          </ul>
        </div>
      )}
    </div>
  );
}

// Service Worker регистрация (обычно в отдельном файле)
const registerServiceWorker = async () => {
  if ('serviceWorker' in navigator) {
    try {
      const registration = await navigator.serviceWorker.register('/sw.js');
      console.log('Service Worker зарегистрирован:', registration);
    } catch (error) {
      console.error('Ошибка регистрации Service Worker:', error);
    }
  }
};

// Имитация service worker
const mockServiceWorker = `
// sw.js - Service Worker
const CACHE_NAME = 'pwa-cache-v1';
const urlsToCache = [
  '/',
  '/styles.css',
  '/app.js',
  '/manifest.json'
];

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then((cache) => cache.addAll(urlsToCache))
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request)
      .then((response) => {
        // Возвращаем кэш или делаем запрос
        return response || fetch(event.request);
      }
    )
  );
});
`;

export default SimplePWA;
```
Пример 68: Уведомления в PWA
```jsx
import React, { useState, useEffect } from 'react';

function PwaNotifications() {
  const [notificationPermission, setNotificationPermission] = useState('default');
  const [scheduledNotifications, setScheduledNotifications] = useState([]);
  const [notificationTime, setNotificationTime] = useState(5); // минуты

  // Проверяем разрешение на уведомления
  useEffect(() => {
    if ('Notification' in window) {
      setNotificationPermission(Notification.permission);
    }
  }, []);

  const requestNotificationPermission = async () => {
    if (!('Notification' in window)) {
      alert('Ваш браузер не поддерживает уведомления');
      return;
    }

    try {
      const permission = await Notification.requestPermission();
      setNotificationPermission(permission);
      
      if (permission === 'granted') {
        showNotification('Разрешение получено!', 'Теперь вы будете получать уведомления');
      }
    } catch (error) {
      console.error('Ошибка запроса разрешения:', error);
    }
  };

  const showNotification = (title, body, delay = 0) => {
    if (notificationPermission !== 'granted') {
      alert('Сначала разрешите уведомления');
      return;
    }

    const show = () => {
      const notification = new Notification(title, {
        body: body,
        icon: '/icon-192x192.png', // Путь к иконке
        badge: '/icon-72x72.png',
        tag: 'pwa-notification',
        requireInteraction: true, // Уведомление не исчезнет само
        actions: [
          {
            action: 'open',
            title: 'Открыть'
          },
          {
            action: 'close',
            title: 'Закрыть'
          }
        ]
      });

      notification.onclick = () => {
        window.focus();
        notification.close();
      };

      notification.onclose = () => {
        console.log('Уведомление закрыто');
      };

      return notification;
    };

    if (delay > 0) {
      const timeoutId = setTimeout(show, delay * 1000);
      const notificationId = Date.now();
      
      setScheduledNotifications(prev => [...prev, {
        id: notificationId,
        title,
        body,
        timeoutId,
        scheduledTime: new Date(Date.now() + delay * 1000).toLocaleTimeString()
      }]);

      return notificationId;
    } else {
      show();
    }
  };

  const scheduleNotification = () => {
    const minutes = notificationTime;
    const title = 'Напоминание';
    const body = `Вы установили напоминание на ${minutes} минут`;
    
    showNotification(title, body, minutes * 60);
  };

  const cancelScheduledNotification = (id) => {
    setScheduledNotifications(prev => {
      const notification = prev.find(n => n.id === id);
      if (notification) {
        clearTimeout(notification.timeoutId);
      }
      return prev.filter(n => n.id !== id);
    });
  };

  const sendTestNotification = () => {
    showNotification('Тестовое уведомление', 'Это тестовое уведомление от PWA приложения!');
  };

  const getPermissionStatusText = () => {
    switch (notificationPermission) {
      case 'granted':
        return '✅ Разрешено';
      case 'denied':
        return '❌ Запрещено';
      case 'default':
        return '❓ Не запрошено';
      default:
        return '❓ Неизвестно';
    }
  };

  return (
    <div style={{ maxWidth: '600px', margin: '0 auto', padding: '20px' }}>
      <h2>PWA Уведомления</h2>

      {/* Статус разрешений */}
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px',
        marginBottom: '30px'
      }}>
        <h3>Статус уведомлений</h3>
        <div style={{ 
          display: 'flex', 
          justifyContent: 'space-between', 
          alignItems: 'center',
          marginBottom: '15px'
        }}>
          <span>Разрешение на уведомления:</span>
          <strong>{getPermissionStatusText()}</strong>
        </div>
        
        {notificationPermission !== 'granted' && (
          <button
            onClick={requestNotificationPermission}
            style={{
              padding: '10px 20px',
              backgroundColor: '#2196F3',
              color: 'white',
              border: 'none',
              borderRadius: '6px',
              cursor: 'pointer',
              width: '100%'
            }}
          >
            Запросить разрешение
          </button>
        )}
      </div>

      {/* Тестовые уведомления */}
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#e8f5e8',
        borderRadius: '8px',
        marginBottom: '30px'
      }}>
        <h3>Тестовые уведомления</h3>
        <p style={{ marginBottom: '15px' }}>
          Проверьте работу уведомлений:
        </p>
        <button
          onClick={sendTestNotification}
          disabled={notificationPermission !== 'granted'}
          style={{
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '6px',
            cursor: notificationPermission === 'granted' ? 'pointer' : 'not-allowed',
            opacity: notificationPermission === 'granted' ? 1 : 0.6,
            marginRight: '10px'
          }}
        >
          Отправить тестовое уведомление
        </button>
      </div>

      {/* Напоминания */}
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#fff3e0',
        borderRadius: '8px',
        marginBottom: '30px'
      }}>
        <h3>Напоминания</h3>
        <div style={{ display: 'flex', gap: '10px', alignItems: 'center', marginBottom: '15px' }}>
          <span>Уведомить через:</span>
          <input
            type="number"
            min="1"
            max="60"
            value={notificationTime}
            onChange={(e) => setNotificationTime(Number(e.target.value))}
            style={{
              width: '60px',
              padding: '5px',
              border: '1px solid #ddd',
              borderRadius: '4px'
            }}
          />
          <span>минут</span>
          <button
            onClick={scheduleNotification}
            disabled={notificationPermission !== 'granted'}
            style={{
              padding: '5px 15px',
              backgroundColor: '#ff9800',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: notificationPermission === 'granted' ? 'pointer' : 'not-allowed',
              opacity: notificationPermission === 'granted' ? 1 : 0.6
            }}
          >
            Установить напоминание
          </button>
        </div>
      </div>

      {/* Запланированные уведомления */}
      {scheduledNotifications.length > 0 && (
        <div style={{ 
          padding: '20px', 
          backgroundColor: '#e3f2fd',
          borderRadius: '8px',
          marginBottom: '30px'
        }}>
          <h3>Запланированные уведомления</h3>
          <div style={{ display: 'grid', gap: '10px' }}>
            {scheduledNotifications.map(notification => (
              <div
                key={notification.id}
                style={{
                  padding: '10px 15px',
                  backgroundColor: 'white',
                  border: '1px solid #ddd',
                  borderRadius: '6px',
                  display: 'flex',
                  justifyContent: 'space-between',
                  alignItems: 'center'
                }}
              >
                <div>
                  <div style={{ fontWeight: 'bold' }}>{notification.title}</div>
                  <div style={{ fontSize: '0.9rem', color: '#666' }}>
                    {notification.body}
                  </div>
                  <div style={{ fontSize: '0.8rem', color: '#999' }}>
                    Запланировано на: {notification.scheduledTime}
                  </div>
                </div>
                <button
                  onClick={() => cancelScheduledNotification(notification.id)}
                  style={{
                    padding: '5px 10px',
                    backgroundColor: '#f44336',
                    color: 'white',
                    border: 'none',
                    borderRadius: '4px',
                    cursor: 'pointer',
                    fontSize: '0.8rem'
                  }}
                >
                  Отменить
                </button>
              </div>
            ))}
          </div>
        </div>
      )}

      {/* Информация об уведомлениях */}
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>О PWA уведомлениях</h3>
        <div style={{ display: 'grid', gap: '10px' }}>
          <div>
            <h4>🔔 Преимущества:</h4>
            <ul style={{ margin: 0, paddingLeft: '20px' }}>
              <li>Работают даже когда приложение закрыто</li>
              <li>Поддержка действий (actions)</li>
              <li>Настраиваемый внешний вид</li>
              <li>Поддержка на всех платформах</li>
            </ul>
          </div>
          <div>
            <h4>📱 Использование:</h4>
            <ul style={{ margin: 0, paddingLeft: '20px' }}>
              <li>Напоминания и уведомления</li>
              <li>Новые сообщения в чате</li>
              <li>Обновления контента</li>
              <li>Системные оповещения</li>
            </ul>
          </div>
        </div>
      </div>

      {/* Отладка */}
      <details style={{ marginTop: '20px' }}>
        <summary style={{ cursor: 'pointer', fontWeight: 'bold' }}>
          Информация для отладки
        </summary>
        <div style={{ 
          marginTop: '10px', 
          padding: '15px', 
          backgroundColor: '#333',
          color: '#fff',
          borderRadius: '4px',
          fontSize: '0.8rem',
          fontFamily: 'monospace'
        }}>
          <div>Notification API: {('Notification' in window) ? '✅ Доступен' : '❌ Недоступен'}</div>
          <div>Service Worker: {('serviceWorker' in navigator) ? '✅ Доступен' : '❌ Недоступен'}</div>
          <div>Разрешение: {notificationPermission}</div>
          <div>Запланировано: {scheduledNotifications.length} уведомлений</div>
        </div>
      </details>
    </div>
  );
}

export default PwaNotifications;
Часть 20: TypeScript с React
```
Пример 69: React компоненты с TypeScript
```jsx
import React, { useState, useEffect } from 'react';

// Типы для пропсов и состояния
interface User {
  id: number;
  name: string;
  email: string;
  age: number;
  isActive: boolean;
}

interface UserCardProps {
  user: User;
  onEdit: (user: User) => void;
  onDelete: (userId: number) => void;
  onToggleActive: (userId: number) => void;
}

interface UserFormProps {
  user?: User | null;
  onSubmit: (user: Omit<User, 'id'>) => void;
  onCancel: () => void;
}

// Тип для формы (без id)
type UserFormData = Omit<User, 'id'>;

// Компонент карточки пользователя
const UserCard: React.FC<UserCardProps> = ({ 
  user, 
  onEdit, 
  onDelete, 
  onToggleActive 
}) => {
  return (
    <div style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '15px',
      marginBottom: '10px',
      backgroundColor: user.isActive ? '#f8f9fa' : '#f5f5f5',
      opacity: user.isActive ? 1 : 0.7
    }}>
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start' }}>
        <div style={{ flex: 1 }}>
          <h3 style={{ margin: '0 0 5px 0' }}>{user.name}</h3>
          <p style={{ margin: '0 0 5px 0', color: '#666' }}>{user.email}</p>
          <div style={{ display: 'flex', gap: '15px', fontSize: '0.9rem' }}>
            <span>Возраст: {user.age}</span>
            <span style={{ 
              color: user.isActive ? '#4CAF50' : '#f44336',
              fontWeight: 'bold'
            }}>
              {user.isActive ? 'Активен' : 'Неактивен'}
            </span>
          </div>
        </div>
        <div style={{ display: 'flex', gap: '5px', flexDirection: 'column' }}>
          <button
            onClick={() => onEdit(user)}
            style={{
              padding: '5px 10px',
              backgroundColor: '#2196F3',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              fontSize: '0.8rem'
            }}
          >
            ✏️
          </button>
          <button
            onClick={() => onToggleActive(user.id)}
            style={{
              padding: '5px 10px',
              backgroundColor: user.isActive ? '#ff9800' : '#4CAF50',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              fontSize: '0.8rem'
            }}
          >
            {user.isActive ? '❌' : '✅'}
          </button>
          <button
            onClick={() => onDelete(user.id)}
            style={{
              padding: '5px 10px',
              backgroundColor: '#f44336',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              fontSize: '0.8rem'
            }}
          >
            🗑️
          </button>
        </div>
      </div>
    </div>
  );
};

// Компонент формы пользователя
const UserForm: React.FC<UserFormProps> = ({ user, onSubmit, onCancel }) => {
  const [formData, setFormData] = useState<UserFormData>({
    name: user?.name || '',
    email: user?.email || '',
    age: user?.age || 18,
    isActive: user?.isActive || true
  });

  const [errors, setErrors] = useState<Partial<UserFormData>>({});

  const validateForm = (): boolean => {
    const newErrors: Partial<UserFormData> = {};

    if (!formData.name.trim()) {
      newErrors.name = 'Имя обязательно';
    }

    if (!formData.email.trim()) {
      newErrors.email = 'Email обязателен';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Некорректный email';
    }

    if (formData.age < 1 || formData.age > 150) {
      newErrors.age = 'Возраст должен быть от 1 до 150';
    }

    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    
    if (validateForm()) {
      onSubmit(formData);
    }
  };

  const handleChange = (field: keyof UserFormData, value: string | number | boolean) => {
    setFormData(prev => ({
      ...prev,
      [field]: value
    }));
    
    // Очищаем ошибку при изменении поля
    if (errors[field]) {
      setErrors(prev => ({
        ...prev,
        [field]: undefined
      }));
    }
  };

  return (
    <form onSubmit={handleSubmit} style={{
      border: '1px solid #ddd',
      borderRadius: '8px',
      padding: '20px',
      backgroundColor: '#f9f9f9',
      marginBottom: '20px'
    }}>
      <h3>{user ? 'Редактировать пользователя' : 'Добавить пользователя'}</h3>
      
      <div style={{ marginBottom: '15px' }}>
        <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
          Имя:
        </label>
        <input
          type="text"
          value={formData.name}
          onChange={(e) => handleChange('name', e.target.value)}
          style={{
            width: '100%',
            padding: '8px',
            border: `1px solid ${errors.name ? '#f44336' : '#ddd'}`,
            borderRadius: '4px'
          }}
        />
        {errors.name && <span style={{ color: '#f44336', fontSize: '0.8rem' }}>{errors.name}</span>}
      </div>

      <div style={{ marginBottom: '15px' }}>
        <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
          Email:
        </label>
        <input
          type="email"
          value={formData.email}
          onChange={(e) => handleChange('email', e.target.value)}
          style={{
            width: '100%',
            padding: '8px',
            border: `1px solid ${errors.email ? '#f44336' : '#ddd'}`,
            borderRadius: '4px'
          }}
        />
        {errors.email && <span style={{ color: '#f44336', fontSize: '0.8rem' }}>{errors.email}</span>}
      </div>

      <div style={{ marginBottom: '15px' }}>
        <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
          Возраст:
        </label>
        <input
          type="number"
          value={formData.age}
          onChange={(e) => handleChange('age', parseInt(e.target.value) || 0)}
          min="1"
          max="150"
          style={{
            width: '100%',
            padding: '8px',
            border: `1px solid ${errors.age ? '#f44336' : '#ddd'}`,
            borderRadius: '4px'
          }}
        />
        {errors.age && <span style={{ color: '#f44336', fontSize: '0.8rem' }}>{errors.age}</span>}
      </div>

      <div style={{ marginBottom: '20px' }}>
        <label style={{ display: 'flex', alignItems: 'center', gap: '10px' }}>
          <input
            type="checkbox"
            checked={formData.isActive}
            onChange={(e) => handleChange('isActive', e.target.checked)}
          />
          <span>Активный пользователь</span>
        </label>
      </div>

      <div style={{ display: 'flex', gap: '10px' }}>
        <button
          type="submit"
          style={{
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          {user ? 'Обновить' : 'Добавить'}
        </button>
        <button
          type="button"
          onClick={onCancel}
          style={{
            padding: '10px 20px',
            backgroundColor: '#9e9e9e',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Отмена
        </button>
      </div>
    </form>
  );
};

// Главный компонент приложения
const TypeScriptReactExample: React.FC = () => {
  const [users, setUsers] = useState<User[]>([
    { id: 1, name: 'Иван Иванов', email: 'ivan@example.com', age: 25, isActive: true },
    { id: 2, name: 'Мария Петрова', email: 'maria@example.com', age: 30, isActive: false },
    { id: 3, name: 'Алексей Сидоров', email: 'alex@example.com', age: 22, isActive: true }
  ]);

  const [editingUser, setEditingUser] = useState<User | null>(null);
  const [showForm, setShowForm] = useState(false);

  // Генератор ID (в реальном приложении ID генерируется на сервере)
  const generateId = (): number => {
    return Math.max(0, ...users.map(u => u.id)) + 1;
  };

  const handleAddUser = (userData: UserFormData) => {
    const newUser: User = {
      id: generateId(),
      ...userData
    };

    setUsers(prev => [...prev, newUser]);
    setShowForm(false);
  };

  const handleEditUser = (userData: UserFormData) => {
    if (!editingUser) return;

    const updatedUser: User = {
      ...editingUser,
      ...userData
    };

    setUsers(prev => prev.map(u => u.id === editingUser.id ? updatedUser : u));
    setEditingUser(null);
  };

  const handleDeleteUser = (userId: number) => {
    if (window.confirm('Вы уверены, что хотите удалить пользователя?')) {
      setUsers(prev => prev.filter(u => u.id !== userId));
    }
  };

  const handleToggleActive = (userId: number) => {
    setUsers(prev => prev.map(u => 
      u.id === userId ? { ...u, isActive: !u.isActive } : u
    ));
  };

  const startEdit = (user: User) => {
    setEditingUser(user);
    setShowForm(true);
  };

  const cancelEdit = () => {
    setEditingUser(null);
    setShowForm(false);
  };

  const activeUsersCount = users.filter(u => u.isActive).length;
  const averageAge = users.length > 0 
    ? Math.round(users.reduce((sum, u) => sum + u.age, 0) / users.length)
    : 0;

  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>React + TypeScript: Управление пользователями</h2>

      {/* Статистика */}
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(3, 1fr)', 
        gap: '15px',
        marginBottom: '30px'
      }}>
        <div style={{ 
          padding: '15px', 
          backgroundColor: '#e3f2fd',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>{users.length}</div>
          <div>Всего пользователей</div>
        </div>
        <div style={{ 
          padding: '15px', 
          backgroundColor: '#e8f5e8',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>{activeUsersCount}</div>
          <div>Активных</div>
        </div>
        <div style={{ 
          padding: '15px', 
          backgroundColor: '#fff3e0',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '1.5rem', fontWeight: 'bold' }}>{averageAge}</div>
          <div>Средний возраст</div>
        </div>
      </div>

      {/* Форма */}
      {showForm ? (
        <UserForm
          user={editingUser}
          onSubmit={editingUser ? handleEditUser : handleAddUser}
          onCancel={cancelEdit}
        />
      ) : (
        <button
          onClick={() => setShowForm(true)}
          style={{
            padding: '12px 24px',
            backgroundColor: '#2196F3',
            color: 'white',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer',
            marginBottom: '20px',
            fontSize: '16px'
          }}
        >
          ➕ Добавить пользователя
        </button>
      )}

      {/* Список пользователей */}
      <div>
        <h3>Список пользователей ({users.length})</h3>
        {users.length > 0 ? (
          <div>
            {users.map(user => (
              <UserCard
                key={user.id}
                user={user}
                onEdit={startEdit}
                onDelete={handleDeleteUser}
                onToggleActive={handleToggleActive}
              />
            ))}
          </div>
        ) : (
          <div style={{ 
            padding: '40px', 
            textAlign: 'center', 
            color: '#666',
            border: '2px dashed #ddd',
            borderRadius: '8px'
          }}>
            <div style={{ fontSize: '3rem', marginBottom: '10px' }}>👥</div>
            <p>Пользователи не найдены</p>
          </div>
        )}
      </div>

      {/* Информация о TypeScript */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>Преимущества TypeScript с React</h3>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '15px' }}>
          <div>
            <h4>🔒 Типизация пропсов</h4>
            <p>Компилятор проверяет правильность передачи пропсов</p>
          </div>
          <div>
            <h4>🚀 Автодополнение</h4>
            <p>IDE подсказывает доступные свойства и методы</p>
          </div>
          <div>
            <h4>🐛 Раннее обнаружение ошибок</h4>
            <p>Ошибки типов обнаруживаются на этапе компиляции</p>
          </div>
          <div>
            <h4>📝 Лучшая документация</h4>
            <p>Типы служат встроенной документацией</p>
          </div>
        </div>
      </div>
    </div>
  );
};

export default TypeScriptReactExample;
```
Пример 70: Кастомные хуки с TypeScript
```jsx
import React, { useState, useEffect, useCallback } from 'react';

// Типы для кастомных хуков
interface UseLocalStorageResult<T> {
  value: T;
  setValue: (value: T | ((prev: T) => T)) => void;
  removeValue: () => void;
}

interface UseApiResult<T> {
  data: T | null;
  loading: boolean;
  error: string | null;
  refetch: () => void;
}

interface UseTimerResult {
  time: number;
  isRunning: boolean;
  start: () => void;
  pause: () => void;
  reset: () => void;
}

// Кастомный хук для работы с localStorage
function useLocalStorage<T>(
  key: string, 
  initialValue: T
): UseLocalStorageResult<T> {
  const [value, setValue] = useState<T>(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(`Ошибка чтения localStorage ключа "${key}":`, error);
      return initialValue;
    }
  });

  const setStoredValue = useCallback((newValue: T | ((prev: T) => T)) => {
    try {
      const valueToStore = newValue instanceof Function ? newValue(value) : newValue;
      setValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error(`Ошибка записи в localStorage ключа "${key}":`, error);
    }
  }, [key, value]);

  const removeValue = useCallback(() => {
    try {
      window.localStorage.removeItem(key);
      setValue(initialValue);
    } catch (error) {
      console.error(`Ошибка удаления localStorage ключа "${key}":`, error);
    }
  }, [key, initialValue]);

  return { value, setValue: setStoredValue, removeValue };
}

// Кастомный хук для API запросов
function useApi<T>(url: string): UseApiResult<T> {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);

  const fetchData = useCallback(async () => {
    setLoading(true);
    setError(null);
    
    try {
      // Имитация API запроса
      setTimeout(() => {
        const mockData = {
          id: 1,
          title: 'Заголовок статьи',
          content: 'Содержание статьи...',
          author: 'Автор',
          date: new Date().toISOString()
        } as T;
        
        setData(mockData);
        setLoading(false);
      }, 1000);
    } catch (err) {
      setError(err instanceof Error ? err.message : 'Произошла ошибка');
      setLoading(false);
    }
  }, [url]);

  useEffect(() => {
    fetchData();
  }, [fetchData]);

  return { data, loading, error, refetch: fetchData };
}

// Кастомный хук для таймера
function useTimer(initialTime: number = 0): UseTimerResult {
  const [time, setTime] = useState<number>(initialTime);
  const [isRunning, setIsRunning] = useState<boolean>(false);

  useEffect(() => {
    let interval: NodeJS.Timeout | null = null;

    if (isRunning) {
      interval = setInterval(() => {
        setTime(prevTime => prevTime + 1);
      }, 1000);
    }

    return () => {
      if (interval) {
        clearInterval(interval);
      }
    };
  }, [isRunning]);

  const start = useCallback(() => {
    setIsRunning(true);
  }, []);

  const pause = useCallback(() => {
    setIsRunning(false);
  }, []);

  const reset = useCallback(() => {
    setTime(initialTime);
    setIsRunning(false);
  }, [initialTime]);

  return { time, isRunning, start, pause, reset };
}

// Компонент для демонстрации useLocalStorage
const LocalStorageDemo: React.FC = () => {
  const { value: name, setValue: setName, removeValue: removeName } = useLocalStorage('userName', '');
  const { value: theme, setValue: setTheme } = useLocalStorage('theme', 'light');

  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: theme === 'dark' ? '#333' : '#fff',
      color: theme === 'dark' ? '#fff' : '#333',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>useLocalStorage Demo</h3>
      
      <div style={{ marginBottom: '15px' }}>
        <input
          type="text"
          value={name}
          onChange={(e) => setName(e.target.value)}
          placeholder="Введите ваше имя"
          style={{ 
            padding: '8px', 
            marginRight: '10px',
            backgroundColor: theme === 'dark' ? '#555' : '#fff',
            color: theme === 'dark' ? '#fff' : '#333',
            border: '1px solid #ddd'
          }}
        />
        <button onClick={() => setName('')}>Очистить</button>
        <button onClick={removeName}>Удалить из storage</button>
      </div>

      <div style={{ marginBottom: '15px' }}>
        <button 
          onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
          style={{ marginRight: '10px' }}
        >
          Переключить тему ({theme})
        </button>
      </div>

      <div>
        <strong>Текущее имя:</strong> {name || 'не установлено'}
      </div>
    </div>
  );
};

// Компонент для демонстрации useApi
const ApiDemo: React.FC = () => {
  interface Article {
    id: number;
    title: string;
    content: string;
    author: string;
    date: string;
  }

  const { data: article, loading, error, refetch } = useApi<Article>('/api/article');

  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: '#f5f5f5',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>useApi Demo</h3>
      
      <button onClick={refetch} disabled={loading} style={{ marginBottom: '15px' }}>
        {loading ? 'Загрузка...' : 'Загрузить данные'}
      </button>

      {loading && <div>Загрузка статьи...</div>}
      {error && <div style={{ color: 'red' }}>Ошибка: {error}</div>}
      
      {article && (
        <div style={{ 
          padding: '15px', 
          backgroundColor: 'white', 
          borderRadius: '4px',
          border: '1px solid #ddd'
        }}>
          <h4>{article.title}</h4>
          <p>{article.content}</p>
          <div style={{ fontSize: '0.8rem', color: '#666' }}>
            Автор: {article.author} | Дата: {new Date(article.date).toLocaleDateString()}
          </div>
        </div>
      )}
    </div>
  );
};

// Компонент для демонстрации useTimer
const TimerDemo: React.FC = () => {
  const { time, isRunning, start, pause, reset } = useTimer();

  const formatTime = (seconds: number): string => {
    const mins = Math.floor(seconds / 60);
    const secs = seconds % 60;
    return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
  };

  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: '#e3f2fd',
      borderRadius: '8px',
      marginBottom: '20px',
      textAlign: 'center'
    }}>
      <h3>useTimer Demo</h3>
      
      <div style={{ fontSize: '3rem', fontWeight: 'bold', margin: '20px 0' }}>
        {formatTime(time)}
      </div>

      <div style={{ display: 'flex', gap: '10px', justifyContent: 'center' }}>
        {!isRunning ? (
          <button onClick={start} style={{ 
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}>
            Старт
          </button>
        ) : (
          <button onClick={pause} style={{ 
            padding: '10px 20px',
            backgroundColor: '#ff9800',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}>
            Пауза
          </button>
        )}
        
        <button onClick={reset} style={{ 
          padding: '10px 20px',
          backgroundColor: '#f44336',
          color: 'white',
          border: 'none',
          borderRadius: '4px',
          cursor: 'pointer'
        }}>
          Сброс
        </button>
      </div>

      <div style={{ marginTop: '10px', color: '#666' }}>
        Статус: {isRunning ? '⏱️ Запущен' : '⏸️ На паузе'}
      </div>
    </div>
  );
};

// Главный компонент
const CustomHooksTypeScript: React.FC = () => {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Кастомные хуки с TypeScript</h2>
      
      <LocalStorageDemo />
      <ApiDemo />
      <TimerDemo />

      {/* Информация о кастомных хуках */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>О кастомных хуках с TypeScript</h3>
        <div style={{ display: 'grid', gap: '15px' }}>
          <div>
            <h4>🎯 Преимущества:</h4>
            <ul style={{ margin: 0, paddingLeft: '20px' }}>
              <li><strong>Переиспользуемость логики</strong> - один раз написали, используем везде</li>
              <li><strong>Типизация</strong> - TypeScript проверяет типы входных и выходных данных</li>
              <li><strong>Тестируемость</strong> - логику легко тестировать отдельно от компонентов</li>
              <li><strong>Чистота компонентов</strong> - бизнес-логика вынесена в хуки</li>
            </ul>
          </div>
          
          <div>
            <h4>📝 Лучшие практики:</h4>
            <ul style={{ margin: 0, paddingLeft: '20px' }}>
              <li>Начинайте названия хуков с "use"</li>
              <li>Четко определяйте интерфейсы входных и выходных данных</li>
              <li>Используйте дженерики для переиспользуемых хуков</li>
              <li>Документируйте типы и поведение хука</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  );
};

export default CustomHooksTypeScript;
Продолжаем! Следующие части будут включать тестирование, оптимизацию производительности, серверный рендеринг и многое другое. Хотите, чтобы я продолжил?

да
Отлично! Продолжаем с тестированием и продвинутыми темами:

Часть 21: Тестирование React компонентов
```
Пример 71: Тестируемый компонент счетчика
```jsx
import React, { useState } from 'react';

// Простой тестируемый компонент счетчика
export const Counter: React.FC = () => {
  const [count, setCount] = useState(0);

  const increment = () => setCount(prev => prev + 1);
  const decrement = () => setCount(prev => prev - 1);
  const reset = () => setCount(0);
  const setValue = (value: number) => setCount(value);

  return (
    <div data-testid="counter-component">
      <h2 data-testid="counter-title">Счетчик: <span data-testid="counter-value">{count}</span></h2>
      
      <div style={{ display: 'flex', gap: '10px', marginBottom: '15px' }}>
        <button 
          data-testid="increment-btn"
          onClick={increment}
          style={{
            padding: '10px 20px',
            backgroundColor: '#4CAF50',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          + Увеличить
        </button>
        
        <button 
          data-testid="decrement-btn"
          onClick={decrement}
          style={{
            padding: '10px 20px',
            backgroundColor: '#f44336',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          - Уменьшить
        </button>
        
        <button 
          data-testid="reset-btn"
          onClick={reset}
          style={{
            padding: '10px 20px',
            backgroundColor: '#ff9800',
            color: 'white',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer'
          }}
        >
          Сбросить
        </button>
      </div>

      <div style={{ marginBottom: '15px' }}>
        <input
          data-testid="value-input"
          type="number"
          value={count}
          onChange={(e) => setValue(Number(e.target.value))}
          style={{
            padding: '8px',
            border: '1px solid #ddd',
            borderRadius: '4px',
            width: '100px'
          }}
        />
      </div>

      {/* Сообщения в зависимости от значения */}
      <div data-testid="status-message">
        {count === 0 && (
          <p style={{ color: '#666' }}>Счетчик сброшен</p>
        )}
        {count > 0 && (
          <p style={{ color: '#4CAF50' }}>Положительное значение</p>
        )}
        {count < 0 && (
          <p style={{ color: '#f44336' }}>Отрицательное значение</p>
        )}
        {count > 10 && (
          <p style={{ color: '#2196F3', fontWeight: 'bold' }}>Большое число!</p>
        )}
      </div>
    </div>
  );
};

// Компонент с формой для тестирования
export const UserForm: React.FC = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    age: ''
  });
  const [submitted, setSubmitted] = useState(false);

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const { name, value } = e.target;
    setFormData(prev => ({
      ...prev,
      [name]: value
    }));
  };

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    setSubmitted(true);
  };

  const resetForm = () => {
    setFormData({ name: '', email: '', age: '' });
    setSubmitted(false);
  };

  if (submitted) {
    return (
      <div data-testid="success-message">
        <h3>Форма отправлена!</h3>
        <p><strong>Имя:</strong> {formData.name}</p>
        <p><strong>Email:</strong> {formData.email}</p>
        <p><strong>Возраст:</strong> {formData.age}</p>
        <button 
          data-testid="reset-form-btn"
          onClick={resetForm}
        >
          Заполнить снова
        </button>
      </div>
    );
  }

  return (
    <form data-testid="user-form" onSubmit={handleSubmit}>
      <h3>Форма пользователя</h3>
      
      <div style={{ marginBottom: '15px' }}>
        <label>
          Имя:
          <input
            data-testid="name-input"
            type="text"
            name="name"
            value={formData.name}
            onChange={handleChange}
            required
            style={{ display: 'block', width: '100%', padding: '8px', marginTop: '5px' }}
          />
        </label>
      </div>

      <div style={{ marginBottom: '15px' }}>
        <label>
          Email:
          <input
            data-testid="email-input"
            type="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
            required
            style={{ display: 'block', width: '100%', padding: '8px', marginTop: '5px' }}
          />
        </label>
      </div>

      <div style={{ marginBottom: '15px' }}>
        <label>
          Возраст:
          <input
            data-testid="age-input"
            type="number"
            name="age"
            value={formData.age}
            onChange={handleChange}
            min="1"
            max="150"
            style={{ display: 'block', width: '100%', padding: '8px', marginTop: '5px' }}
          />
        </label>
      </div>

      <button 
        data-testid="submit-btn"
        type="submit"
        disabled={!formData.name || !formData.email || !formData.age}
        style={{
          padding: '10px 20px',
          backgroundColor: '#2196F3',
          color: 'white',
          border: 'none',
          borderRadius: '4px',
          cursor: 'pointer'
        }}
      >
        Отправить
      </button>
    </form>
  );
};

// Демонстрационный компонент
const TestingExample: React.FC = () => {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Тестируемые React компоненты</h2>
      
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '40px' }}>
        <div>
          <Counter />
        </div>
        <div>
          <UserForm />
        </div>
      </div>

      {/* Информация о тестировании */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>О тестировании React компонентов</h3>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '20px' }}>
          <div>
            <h4>🧪 Jest + Testing Library</h4>
            <ul>
              <li><strong>Jest</strong> - test runner и assertion library</li>
              <li><strong>React Testing Library</strong> - утилиты для тестирования React</li>
              <li><strong>DOM Testing Library</strong> - работа с DOM элементами</li>
              <li><strong>User Event</strong> - симуляция действий пользователя</li>
            </ul>
          </div>
          
          <div>
            <h4>🎯 Лучшие практики</h4>
            <ul>
              <li>Используйте data-testid для поиска элементов</li>
              <li>Тестируйте поведение, а не реализацию</li>
              <li>Симулируйте действия пользователя</li>
              <li>Пишите понятные названия тестов</li>
            </ul>
          </div>
        </div>

        {/* ```
Пример тестов */}
        <details style={{ marginTop: '20px' }}>
          <summary style={{ cursor: 'pointer', fontWeight: 'bold' }}>
            ```
Пример тестов для компонента Counter
          </summary>
          <pre style={{ 
            backgroundColor: '#333', 
            color: '#fff', 
            padding: '15px', 
            borderRadius: '4px',
            overflow: 'auto',
            fontSize: '0.8rem',
            marginTop: '10px'
          }}>
{`// Counter.test.js
import { render, screen, fireEvent } from '@testing-library/react';
import { Counter } from './Counter';

describe('Counter Component', () => {
  test('renders counter with initial value 0', () => {
    render(<Counter />);
    expect(screen.getByTestId('counter-value')).toHaveTextContent('0');
  });

  test('increments counter when + button is clicked', () => {
    render(<Counter />);
    const incrementBtn = screen.getByTestId('increment-btn');
    fireEvent.click(incrementBtn);
    expect(screen.getByTestId('counter-value')).toHaveTextContent('1');
  });

  test('decrements counter when - button is clicked', () => {
    render(<Counter />);
    const decrementBtn = screen.getByTestId('decrement-btn');
    fireEvent.click(decrementBtn);
    expect(screen.getByTestId('counter-value')).toHaveTextContent('-1');
  });

  test('resets counter when reset button is clicked', () => {
    render(<Counter />);
    const incrementBtn = screen.getByTestId('increment-btn');
    const resetBtn = screen.getByTestId('reset-btn');
    
    fireEvent.click(incrementBtn);
    fireEvent.click(incrementBtn);
    expect(screen.getByTestId('counter-value')).toHaveTextContent('2');
    
    fireEvent.click(resetBtn);
    expect(screen.getByTestId('counter-value')).toHaveTextContent('0');
  });

  test('shows positive message when count > 0', () => {
    render(<Counter />);
    const incrementBtn = screen.getByTestId('increment-btn');
    fireEvent.click(incrementBtn);
    expect(screen.getByText('Положительное значение')).toBeInTheDocument();
  });
});
`}
          </pre>
        </details>
      </div>
    </div>
  );
};

export default TestingExample;
```
Пример 72: Асинхронное тестирование
```jsx
import React, { useState, useEffect } from 'react';

// Компонент с асинхронными операциями для тестирования
export const AsyncComponent: React.FC = () => {
  const [data, setData] = useState<string | null>(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);
  const [user, setUser] = useState<any>(null);

  // Функция для имитации API запроса
  const fetchData = async (shouldFail: boolean = false): Promise<string> => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        if (shouldFail) {
          reject(new Error('Ошибка загрузки данных'));
        } else {
          resolve('Данные успешно загружены!');
        }
      }, 1000);
    });
  };

  const loadData = async (shouldFail: boolean = false) => {
    setLoading(true);
    setError(null);
    
    try {
      const result = await fetchData(shouldFail);
      setData(result);
    } catch (err) {
      setError(err instanceof Error ? err.message : 'Неизвестная ошибка');
    } finally {
      setLoading(false);
    }
  };

  const loadUser = async (userId: number) => {
    setLoading(true);
    
    // Имитация запроса пользователя
    setTimeout(() => {
      setUser({
        id: userId,
        name: 'John Doe',
        email: 'john@example.com'
      });
      setLoading(false);
    }, 500);
  };

  const clearData = () => {
    setData(null);
    setError(null);
    setUser(null);
  };

  return (
    <div data-testid="async-component">
      <h3>Асинхронный компонент</h3>
      
      <div style={{ marginBottom: '20px' }}>
        <button 
          data-testid="load-success-btn"
          onClick={() => loadData(false)}
          disabled={loading}
          style={{ marginRight: '10px' }}
        >
          Загрузить данные (успех)
        </button>
        
        <button 
          data-testid="load-error-btn"
          onClick={() => loadData(true)}
          disabled={loading}
          style={{ marginRight: '10px' }}
        >
          Загрузить данные (ошибка)
        </button>
        
        <button 
          data-testid="load-user-btn"
          onClick={() => loadUser(1)}
          disabled={loading}
          style={{ marginRight: '10px' }}
        >
          Загрузить пользователя
        </button>
        
        <button 
          data-testid="clear-btn"
          onClick={clearData}
        >
          Очистить
        </button>
      </div>

      {loading && (
        <div data-testid="loading-indicator" style={{ color: '#2196F3' }}>
          Загрузка...
        </div>
      )}

      {error && (
        <div data-testid="error-message" style={{ color: '#f44336' }}>
          Ошибка: {error}
        </div>
      )}

      {data && (
        <div data-testid="data-content" style={{ 
          padding: '15px', 
          backgroundColor: '#e8f5e8', 
          borderRadius: '4px',
          marginBottom: '10px'
        }}>
          {data}
        </div>
      )}

      {user && (
        <div data-testid="user-info" style={{ 
          padding: '15px', 
          backgroundColor: '#e3f2fd', 
          borderRadius: '4px'
        }}>
          <h4>Информация о пользователе:</h4>
          <p><strong>ID:</strong> {user.id}</p>
          <p><strong>Имя:</strong> {user.name}</p>
          <p><strong>Email:</strong> {user.email}</p>
        </div>
      )}
    </div>
  );
};

// Компонент с таймером для тестирования
export const TimerComponent: React.FC = () => {
  const [time, setTime] = useState(0);
  const [isRunning, setIsRunning] = useState(false);

  useEffect(() => {
    let interval: NodeJS.Timeout;
    
    if (isRunning) {
      interval = setInterval(() => {
        setTime(prev => prev + 1);
      }, 1000);
    }

    return () => {
      if (interval) {
        clearInterval(interval);
      }
    };
  }, [isRunning]);

  const startTimer = () => setIsRunning(true);
  const pauseTimer = () => setIsRunning(false);
  const resetTimer = () => {
    setTime(0);
    setIsRunning(false);
  };

  return (
    <div data-testid="timer-component">
      <h3>Таймер: <span data-testid="timer-value">{time}</span> сек.</h3>
      
      <div style={{ marginBottom: '15px' }}>
        <button 
          data-testid="start-timer-btn"
          onClick={startTimer}
          disabled={isRunning}
          style={{ marginRight: '10px' }}
        >
          Старт
        </button>
        
        <button 
          data-testid="pause-timer-btn"
          onClick={pauseTimer}
          disabled={!isRunning}
          style={{ marginRight: '10px' }}
        >
          Пауза
        </button>
        
        <button 
          data-testid="reset-timer-btn"
          onClick={resetTimer}
        >
          Сброс
        </button>
      </div>

      <div data-testid="timer-status">
        Статус: {isRunning ? '⏱️ Запущен' : '⏸️ На паузе'}
      </div>
    </div>
  );
};

// Демонстрационный компонент
const AsyncTestingExample: React.FC = () => {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>Асинхронное тестирование React</h2>
      
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '40px' }}>
        <div>
          <AsyncComponent />
        </div>
        <div>
          <TimerComponent />
        </div>
      </div>

      {/* Информация об асинхронном тестировании */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>Асинхронное тестирование в React</h3>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '20px' }}>
          <div>
            <h4>🔄 Async/Await</h4>
            <ul>
              <li><code>waitFor</code> - ожидание появления элемента</li>
              <li><code>findBy*</code> - поиск с ожиданием</li>
              <li><code>await</code> - ожидание промисов</li>
              <li><code>act</code> - обертывание асинхронных операций</li>
            </ul>
          </div>
          
          <div>
            <h4>⏱️ Таймеры</h4>
            <ul>
              <li><code>jest.useFakeTimers()</code> - мокаем таймеры</li>
              <li><code>jest.advanceTimersByTime()</code> - продвигаем время</li>
              <li><code>jest.runOnlyPendingTimers()</code> - запускаем ожидающие таймеры</li>
            </ul>
          </div>
        </div>

        {/* ```
Пример асинхронных тестов */}
        <details style={{ marginTop: '20px' }}>
          <summary style={{ cursor: 'pointer', fontWeight: 'bold' }}>
            ```
Пример асинхронных тестов
          </summary>
          <pre style={{ 
            backgroundColor: '#333', 
            color: '#fff', 
            padding: '15px', 
            borderRadius: '4px',
            overflow: 'auto',
            fontSize: '0.8rem',
            marginTop: '10px'
          }}>
{`// AsyncComponent.test.js
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { AsyncComponent } from './AsyncComponent';

describe('AsyncComponent', () => {
  test('loads data successfully', async () => {
    render(<AsyncComponent />);
    
    const loadButton = screen.getByTestId('load-success-btn');
    fireEvent.click(loadButton);
    
    // Ждем появления индикатора загрузки
    expect(screen.getByTestId('loading-indicator')).toBeInTheDocument();
    
    // Ждем появления данных
    await waitFor(() => {
      expect(screen.getByTestId('data-content')).toBeInTheDocument();
    });
    
    expect(screen.getByText('Данные успешно загружены!')).toBeInTheDocument();
  });

  test('handles loading error', async () => {
    render(<AsyncComponent />);
    
    const loadButton = screen.getByTestId('load-error-btn');
    fireEvent.click(loadButton);
    
    await waitFor(() => {
      expect(screen.getByTestId('error-message')).toBeInTheDocument();
    });
    
    expect(screen.getByText(/Ошибка загрузки данных/)).toBeInTheDocument();
  });

  test('loads user data', async () => {
    render(<AsyncComponent />);
    
    const loadUserButton = screen.getByTestId('load-user-btn');
    fireEvent.click(loadUserButton);
    
    await waitFor(() => {
      expect(screen.getByTestId('user-info')).toBeInTheDocument();
    });
    
    expect(screen.getByText('John Doe')).toBeInTheDocument();
  });
});

// TimerComponent.test.js
import { render, screen, fireEvent, act } from '@testing-library/react';
import { TimerComponent } from './TimerComponent';

describe('TimerComponent', () => {
  beforeEach(() => {
    jest.useFakeTimers();
  });

  afterEach(() => {
    jest.useRealTimers();
  });

  test('starts and increments timer', () => {
    render(<TimerComponent />);
    
    const startButton = screen.getByTestId('start-timer-btn');
    fireEvent.click(startButton);
    
    // Продвигаем время на 1 секунду
    act(() => {
      jest.advanceTimersByTime(1000);
    });
    
    expect(screen.getByTestId('timer-value')).toHaveTextContent('1');
    
    // Продвигаем еще на 2 секунды
    act(() => {
      jest.advanceTimersByTime(2000);
    });
    
    expect(screen.getByTestId('timer-value')).toHaveTextContent('3');
  });

  test('pauses timer', () => {
    render(<TimerComponent />);
    
    const startButton = screen.getByTestId('start-timer-btn');
    const pauseButton = screen.getByTestId('pause-timer-btn');
    
    fireEvent.click(startButton);
    
    act(() => {
      jest.advanceTimersByTime(3000);
    });
    
    fireEvent.click(pauseButton);
    
    const currentTime = screen.getByTestId('timer-value').textContent;
    
    act(() => {
      jest.advanceTimersByTime(2000);
    });
    
    // Время не должно измениться после паузы
    expect(screen.getByTestId('timer-value')).toHaveTextContent(currentTime);
  });
});
`}
          </pre>
        </details>
      </div>
    </div>
  );
};

export default AsyncTestingExample;
Часть 22: Оптимизация производительности
```
Пример 73: Оптимизация с React.memo, useMemo, useCallback
```jsx
import React, { useState, useMemo, useCallback, memo } from 'react';

// Дорогой для вычисления компонент
interface ExpensiveComponentProps {
  data: { id: number; value: number };
  onUpdate: (id: number, value: number) => void;
}

const ExpensiveComponent: React.FC<ExpensiveComponentProps> = memo(({ data, onUpdate }) => {
  console.log(`🔁 ExpensiveComponent ${data.id} перерендерен`);
  
  // Имитация тяжелых вычислений
  const expensiveValue = useMemo(() => {
    console.log(`🧮 Вычисление для элемента ${data.id}`);
    let result = 0;
    for (let i = 0; i < 1000000; i++) {
      result += Math.sqrt(data.value) * Math.random();
    }
    return result;
  }, [data.value]);

  const handleUpdate = useCallback(() => {
    onUpdate(data.id, data.value + 1);
  }, [data.id, data.value, onUpdate]);

  return (
    <div style={{
      padding: '15px',
      border: '1px solid #ddd',
      borderRadius: '8px',
      marginBottom: '10px',
      backgroundColor: '#f9f9f9'
    }}>
      <h4>Элемент {data.id}</h4>
      <p>Значение: {data.value}</p>
      <p>Результат вычислений: {expensiveValue.toFixed(2)}</p>
      <button onClick={handleUpdate}>
        Увеличить значение
      </button>
    </div>
  );
});

// Компонент списка с оптимизацией
interface DataItem {
  id: number;
  value: number;
}

const OptimizedList: React.FC = memo(() => {
  const [items, setItems] = useState<DataItem[]>(() => 
    Array.from({ length: 5 }, (_, i) => ({ id: i + 1, value: 1 }))
  );
  const [filter, setFilter] = useState('');
  const [newItemValue, setNewItemValue] = useState(1);

  // Оптимизированная функция обновления
  const handleUpdateItem = useCallback((id: number, newValue: number) => {
    setItems(prev => prev.map(item => 
      item.id === id ? { ...item, value: newValue } : item
    ));
  }, []);

  // Оптимизированная функция добавления
  const handleAddItem = useCallback(() => {
    const newId = Math.max(0, ...items.map(i => i.id)) + 1;
    setItems(prev => [...prev, { id: newId, value: newItemValue }]);
  }, [items, newItemValue]);

  // Оптимизированная функция удаления
  const handleRemoveItem = useCallback((id: number) => {
    setItems(prev => prev.filter(item => item.id !== id));
  }, []);

  // Мемоизированный отфильтрованный список
  const filteredItems = useMemo(() => {
    console.log('🔍 Фильтрация списка...');
    return items.filter(item => 
      item.id.toString().includes(filter) || 
      item.value.toString().includes(filter)
    );
  }, [items, filter]);

  // Мемоизированная статистика
  const stats = useMemo(() => {
    console.log('📊 Расчет статистики...');
    return {
      total: items.length,
      sum: items.reduce((acc, item) => acc + item.value, 0),
      average: items.length > 0 ? items.reduce((acc, item) => acc + item.value, 0) / items.length : 0
    };
  }, [items]);

  return (
    <div style={{ padding: '20px' }}>
      <h3>Оптимизированный список</h3>
      
      {/* Элементы управления */}
      <div style={{ marginBottom: '20px', padding: '15px', backgroundColor: '#f0f0f0', borderRadius: '8px' }}>
        <div style={{ display: 'flex', gap: '10px', marginBottom: '10px', flexWrap: 'wrap' }}>
          <input
            type="text"
            placeholder="Фильтр по ID или значению..."
            value={filter}
            onChange={(e) => setFilter(e.target.value)}
            style={{ padding: '8px', border: '1px solid #ddd', borderRadius: '4px' }}
          />
          
          <input
            type="number"
            value={newItemValue}
            onChange={(e) => setNewItemValue(Number(e.target.value))}
            style={{ padding: '8px', border: '1px solid #ddd', borderRadius: '4px', width: '80px' }}
          />
          
          <button onClick={handleAddItem}>
            Добавить элемент
          </button>
        </div>
        
        {/* Статистика */}
        <div style={{ display: 'flex', gap: '15px', fontSize: '0.9rem' }}>
          <span>Элементов: {stats.total}</span>
          <span>Сумма: {stats.sum}</span>
          <span>Среднее: {stats.average.toFixed(2)}</span>
          <span>Отфильтровано: {filteredItems.length}</span>
        </div>
      </div>

      {/* Список элементов */}
      <div>
        {filteredItems.map(item => (
          <div key={item.id} style={{ display: 'flex', alignItems: 'center', gap: '10px' }}>
            <ExpensiveComponent 
              data={item} 
              onUpdate={handleUpdateItem}
            />
            <button 
              onClick={() => handleRemoveItem(item.id)}
              style={{
                padding: '5px 10px',
                backgroundColor: '#f44336',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Удалить
            </button>
          </div>
        ))}
        
        {filteredItems.length === 0 && (
          <div style={{ textAlign: 'center', padding: '20px', color: '#666' }}>
            Элементы не найдены
          </div>
        )}
      </div>
    </div>
  );
});

// Неоптимизированная версия для сравнения
const UnoptimizedList: React.FC = () => {
  const [items, setItems] = useState<DataItem[]>(() => 
    Array.from({ length: 5 }, (_, i) => ({ id: i + 1, value: 1 }))
  );
  const [filter, setFilter] = useState('');
  const [newItemValue, setNewItemValue] = useState(1);

  // Неоптимизированные функции
  const handleUpdateItem = (id: number, newValue: number) => {
    setItems(prev => prev.map(item => 
      item.id === id ? { ...item, value: newValue } : item
    ));
  };

  const handleAddItem = () => {
    const newId = Math.max(0, ...items.map(i => i.id)) + 1;
    setItems(prev => [...prev, { id: newId, value: newItemValue }]);
  };

  const handleRemoveItem = (id: number) => {
    setItems(prev => prev.filter(item => item.id !== id));
  };

  // Неоптимизированные вычисления
  const filteredItems = items.filter(item => 
    item.id.toString().includes(filter) || 
    item.value.toString().includes(filter)
  );

  const stats = {
    total: items.length,
    sum: items.reduce((acc, item) => acc + item.value, 0),
    average: items.length > 0 ? items.reduce((acc, item) => acc + item.value, 0) / items.length : 0
  };

  const UnoptimizedExpensiveComponent: React.FC<{ data: DataItem }> = ({ data }) => {
    console.log(`🔁 Неоптимизированный компонент ${data.id} перерендерен`);
    
    // Тяжелые вычисления без useMemo
    let expensiveValue = 0;
    for (let i = 0; i < 1000000; i++) {
      expensiveValue += Math.sqrt(data.value) * Math.random();
    }

    return (
      <div style={{
        padding: '15px',
        border: '1px solid #ddd',
        borderRadius: '8px',
        marginBottom: '10px',
        backgroundColor: '#fff0f0'
      }}>
        <h4>Элемент {data.id} (неоптимизированный)</h4>
        <p>Значение: {data.value}</p>
        <p>Результат вычислений: {expensiveValue.toFixed(2)}</p>
        <button onClick={() => handleUpdateItem(data.id, data.value + 1)}>
          Увеличить значение
        </button>
      </div>
    );
  };

  return (
    <div style={{ padding: '20px' }}>
      <h3>Неоптимизированный список</h3>
      
      <div style={{ marginBottom: '20px', padding: '15px', backgroundColor: '#f0f0f0', borderRadius: '8px' }}>
        <div style={{ display: 'flex', gap: '10px', marginBottom: '10px', flexWrap: 'wrap' }}>
          <input
            type="text"
            placeholder="Фильтр по ID или значению..."
            value={filter}
            onChange={(e) => setFilter(e.target.value)}
            style={{ padding: '8px', border: '1px solid #ddd', borderRadius: '4px' }}
          />
          
          <input
            type="number"
            value={newItemValue}
            onChange={(e) => setNewItemValue(Number(e.target.value))}
            style={{ padding: '8px', border: '1px solid #ddd', borderRadius: '4px', width: '80px' }}
          />
          
          <button onClick={handleAddItem}>
            Добавить элемент
          </button>
        </div>
        
        <div style={{ display: 'flex', gap: '15px', fontSize: '0.9rem' }}>
          <span>Элементов: {stats.total}</span>
          <span>Сумма: {stats.sum}</span>
          <span>Среднее: {stats.average.toFixed(2)}</span>
          <span>Отфильтровано: {filteredItems.length}</span>
        </div>
      </div>

      <div>
        {filteredItems.map(item => (
          <div key={item.id} style={{ display: 'flex', alignItems: 'center', gap: '10px' }}>
            <UnoptimizedExpensiveComponent data={item} />
            <button 
              onClick={() => handleRemoveItem(item.id)}
              style={{
                padding: '5px 10px',
                backgroundColor: '#f44336',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Удалить
            </button>
          </div>
        ))}
      </div>
    </div>
  );
};

// Главный компонент сравнения
const PerformanceOptimization: React.FC = () => {
  const [showOptimized, setShowOptimized] = useState(true);
  const [renderCount, setRenderCount] = useState(0);

  // Принудительный перерендер для демонстрации
  const forceRerender = () => {
    setRenderCount(prev => prev + 1);
  };

  return (
    <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '20px' }}>
      <h2>Оптимизация производительности React</h2>
      <p>Количество перерендеров: {renderCount}</p>
      
      <div style={{ marginBottom: '20px' }}>
        <button 
          onClick={() => setShowOptimized(!showOptimized)}
          style={{ marginRight: '10px' }}
        >
          Показать {showOptimized ? 'неоптимизированную' : 'оптимизированную'} версию
        </button>
        
        <button onClick={forceRerender}>
          Принудительный перерендер
        </button>
      </div>

      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px' }}>
        {showOptimized ? (
          <>
            <OptimizedList />
            <div style={{ padding: '20px', backgroundColor: '#e8f5e8', borderRadius: '8px' }}>
              <h3>✅ Оптимизированная версия</h3>
              <p><strong>Используются:</strong></p>
              <ul>
                <li>React.memo для компонентов</li>
                <li>useMemo для тяжелых вычислений</li>
                <li>useCallback для функций</li>
                <li>Ключи для списков</li>
              </ul>
              <p><strong>Преимущества:</strong></p>
              <ul>
                <li>Меньше перерендеров</li>
                <li>Быстрые вычисления</li>
                <li>Эффективное использование памяти</li>
              </ul>
            </div>
          </>
        ) : (
          <>
            <UnoptimizedList />
            <div style={{ padding: '20px', backgroundColor: '#ffebee', borderRadius: '8px' }}>
              <h3>❌ Неоптимизированная версия</h3>
              <p><strong>Проблемы:</strong></p>
              <ul>
                <li>Лишние перерендеры компонентов</li>
                <li>Повторные тяжелые вычисления</li>
                <li>Новые функции при каждом рендере</li>
                <li>Медленная фильтрация</li>
              </ul>
              <p><strong>Последствия:</strong></p>
              <ul>
                <li>Медленный интерфейс</li>
                <li>Высокая нагрузка на CPU</li>
                <li>Плохой пользовательский опыт</li>
              </ul>
            </div>
          </>
        )}
      </div>

      {/* Сравнение инструментов оптимизации */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h3>Инструменты оптимизации React</h3>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '20px' }}>
          <div>
            <h4>🔄 React.memo</h4>
            <p><strong>Назначение:</strong> Запоминание компонентов</p>
            <p><strong>Использование:</strong> Для чистых компонентов</p>
            <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`const MyComponent = memo(({ prop }) => {
  return <div>{prop}</div>;
});`}
            </pre>
          </div>
          
          <div>
            <h4>💾 useMemo</h4>
            <p><strong>Назначение:</strong> Запоминание значений</p>
            <p><strong>Использование:</strong> Для тяжелых вычислений</p>
            <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`const expensiveValue = useMemo(() => {
  return heavyCalculation(data);
}, [data]);`}
            </pre>
          </div>
          
          <div>
            <h4>📝 useCallback</h4>
            <p><strong>Назначение:</strong> Запоминание функций</p>
            <p><strong>Использование:</strong> Для колбэков</p>
            <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`const handleClick = useCallback(() => {
  doSomething(id);
}, [id]);`}
            </pre>
          </div>
        </div>
      </div>
    </div>
  );
};

export default PerformanceOptimization;
```
Пример 74: Виртуализация списков
```jsx
import React, { useState, useMemo, useCallback, useRef, useEffect } from 'react';

// Интерфейс для элемента списка
interface ListItem {
  id: number;
  name: string;
  description: string;
  value: number;
  category: string;
}

// Генератор случайных данных
const generateData = (count: number): ListItem[] => {
  const categories = ['Технологии', 'Наука', 'Искусство', 'Спорт', 'Музыка'];
  
  return Array.from({ length: count }, (_, index) => ({
    id: index + 1,
    name: `Элемент ${index + 1}`,
    description: `Это описание элемента ${index + 1} в категории ${categories[index % categories.length]}`,
    value: Math.floor(Math.random() * 1000),
    category: categories[index % categories.length]
  }));
};

// Компонент виртуализированного списка
interface VirtualizedListProps {
  items: ListItem[];
  itemHeight?: number;
  containerHeight?: number;
}

const VirtualizedList: React.FC<VirtualizedListProps> = ({ 
  items, 
  itemHeight = 80, 
  containerHeight = 400 
}) => {
  const [scrollTop, setScrollTop] = useState(0);
  const containerRef = useRef<HTMLDivElement>(null);

  // Количество видимых элементов
  const visibleCount = Math.ceil(containerHeight / itemHeight);
  
  // Индекс первого видимого элемента
  const startIndex = Math.floor(scrollTop / itemHeight);
  
  // Индекс последнего видимого элемента
  const endIndex = Math.min(startIndex + visibleCount + 1, items.length - 1);

  // Видимые элементы
  const visibleItems = useMemo(() => {
    return items.slice(startIndex, endIndex + 1);
  }, [items, startIndex, endIndex]);

  // Обработчик скролла
  const handleScroll = useCallback((e: React.UIEvent<HTMLDivElement>) => {
    setScrollTop(e.currentTarget.scrollTop);
  }, []);

  // Смещение для виртуального скролла
  const offsetY = startIndex * itemHeight;

  // Статистика для отладки
  const stats = useMemo(() => ({
    total: items.length,
    visible: visibleItems.length,
    startIndex,
    endIndex,
    offsetY,
    scrollTop
  }), [items.length, visibleItems.length, startIndex, endIndex, offsetY, scrollTop]);

  return (
    <div>
      {/* Статистика */}
      <div style={{ 
        padding: '10px', 
        backgroundColor: '#e3f2fd', 
        borderRadius: '4px',
        marginBottom: '10px',
        fontSize: '0.8rem'
      }}>
        Элементы: {stats.visible} из {stats.total} | 
        Позиция: {stats.startIndex}-{stats.endIndex} | 
        Смещение: {stats.offsetY}px
      </div>

      {/* Контейнер списка */}
      <div
        ref={containerRef}
        onScroll={handleScroll}
        style={{
          height: `${containerHeight}px`,
          overflow: 'auto',
          border: '1px solid #ddd',
          borderRadius: '4px',
          position: 'relative'
        }}
      >
        {/* Виртуальный контейнер с правильной высотой */}
        <div
          style={{
            height: `${items.length * itemHeight}px`,
            position: 'relative'
          }}
        >
          {/* Видимые элементы */}
          <div
            style={{
              position: 'absolute',
              top: 0,
              left: 0,
              right: 0,
              transform: `translateY(${offsetY}px)`
            }}
          >
            {visibleItems.map((item, index) => (
              <div
                key={item.id}
                style={{
                  height: `${itemHeight}px`,
                  padding: '10px',
                  borderBottom: '1px solid #eee',
                  backgroundColor: index % 2 === 0 ? '#f9f9f9' : '#fff',
                  display: 'flex',
                  flexDirection: 'column',
                  justifyContent: 'center'
                }}
              >
                <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
                  <div>
                    <strong>{item.name}</strong>
                    <span style={{ 
                      marginLeft: '10px', 
                      padding: '2px 6px', 
                      backgroundColor: '#e0e0e0',
                      borderRadius: '10px',
                      fontSize: '0.7rem'
                    }}>
                      {item.category}
                    </span>
                  </div>
                  <div style={{ fontWeight: 'bold', color: '#2196F3' }}>
                    {item.value}
                  </div>
                </div>
                <div style={{ 
                  fontSize: '0.8rem', 
                  color: '#666',
                  marginTop: '5px'
                }}>
                  {item.description}
                </div>
              </div>
            ))}
          </div>
        </div>
      </div>
    </div>
  );
};

// Обычный список для сравнения
const RegularList: React.FC<{ items: ListItem[] }> = ({ items }) => {
  return (
    <div
      style={{
        height: '400px',
        overflow: 'auto',
        border: '1px solid #ddd',
        borderRadius: '4px'
      }}
    >
      {items.map((item, index) => (
        <div
          key={item.id}
          style={{
            height: '80px',
            padding: '10px',
            borderBottom: '1px solid #eee',
            backgroundColor: index % 2 === 0 ? '#f9f9f9' : '#fff',
            display: 'flex',
            flexDirection: 'column',
            justifyContent: 'center'
          }}
        >
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
            <div>
              <strong>{item.name}</strong>
              <span style={{ 
                marginLeft: '10px', 
                padding: '2px 6px', 
                backgroundColor: '#e0e0e0',
                borderRadius: '10px',
                fontSize: '0.7rem'
              }}>
                {item.category}
              </span>
            </div>
            <div style={{ fontWeight: 'bold', color: '#2196F3' }}>
              {item.value}
            </div>
          </div>
          <div style={{ 
            fontSize: '0.8rem', 
            color: '#666',
            marginTop: '5px'
          }}>
            {item.description}
          </div>
        </div>
      ))}
    </div>
  );
};

// Компонент для измерения производительности
const PerformanceMonitor: React.FC<{ 
  virtualized: boolean; 
  itemCount: number;
  renderTime: number;
}> = ({ virtualized, itemCount, renderTime }) => {
  const memoryUsage = useMemo(() => {
    // Приблизительная оценка использования памяти
    const baseMemory = 50; // MB базовое использование
    const perItemMemory = virtualized ? 0.1 : 2; // MB на элемент
    return (baseMemory + itemCount * perItemMemory).toFixed(1);
  }, [itemCount, virtualized]);

  return (
    <div style={{ 
      padding: '15px', 
      backgroundColor: virtualized ? '#e8f5e8' : '#ffebee',
      border: `2px solid ${virtualized ? '#4CAF50' : '#f44336'}`,
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>{virtualized ? '✅ Виртуализированный список' : '❌ Обычный список'}</h3>
      
      <div style={{ display: 'grid', gridTemplateColumns: 'repeat(2, 1fr)', gap: '10px', fontSize: '0.9rem' }}>
        <div>
          <strong>Элементов:</strong> {itemCount.toLocaleString()}
        </div>
        <div>
          <strong>Время рендера:</strong> {renderTime}ms
        </div>
        <div>
          <strong>Память (приблизительно):</strong> {memoryUsage}MB
        </div>
        <div>
          <strong>DOM элементов:</strong> {virtualized ? '~20' : itemCount}
        </div>
      </div>
    </div>
  );
};

// Главный компонент
const VirtualizationExample: React.FC = () => {
  const [itemCount, setItemCount] = useState(1000);
  const [showVirtualized, setShowVirtualized] = useState(true);
  const [renderTime, setRenderTime] = useState(0);

  // Генерация данных
  const items = useMemo(() => generateData(itemCount), [itemCount]);

  // Измерение времени рендера
  useEffect(() => {
    const startTime = performance.now();
    
    // Имитация времени рендера
    const timer = setTimeout(() => {
      const endTime = performance.now();
      setRenderTime(Math.round(endTime - startTime));
    }, 0);

    return () => clearTimeout(timer);
  }, [items, showVirtualized]);

  return (
    <div style={{ maxWidth: '1000px', margin: '0 auto', padding: '20px' }}>
      <h2>Виртуализация списков в React</h2>
      
      {/* Управление */}
      <div style={{ marginBottom: '20px', padding: '15px', backgroundColor: '#f5f5f5', borderRadius: '8px' }}>
        <div style={{ display: 'flex', gap: '15px', alignItems: 'center', flexWrap: 'wrap' }}>
          <div>
            <label>
              Количество элементов: 
              <input
                type="range"
                min="100"
                max="10000"
                step="100"
                value={itemCount}
                onChange={(e) => setItemCount(Number(e.target.value))}
                style={{ margin: '0 10px' }}
              />
              {itemCount.toLocaleString()}
            </label>
          </div>
          
          <button 
            onClick={() => setShowVirtualized(!showVirtualized)}
            style={{
              padding: '8px 16px',
              backgroundColor: showVirtualized ? '#4CAF50' : '#f44336',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer'
            }}
          >
            {showVirtualized ? 'Показать обычный список' : 'Показать виртуализированный'}
          </button>
        </div>
      </div>

      {/* Монитор производительности */}
      <PerformanceMonitor 
        virtualized={showVirtualized}
        itemCount={itemCount}
        renderTime={renderTime}
      />

      {/* Списки */}
      {showVirtualized ? (
        <VirtualizedList items={items} />
      ) : (
        <RegularList items={items} />
      )}

      {/* Сравнение подходов */}
      <div style={{ 
        marginTop: '40px', 
        padding: '20px', 
        backgroundColor: '#fff3e0',
        borderRadius: '8px'
      }}>
        <h3>Сравнение подходов</h3>
        
        <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px' }}>
          <div>
            <h4>✅ Виртуализация</h4>
            <ul>
              <li><strong>Производительность:</strong> Высокая, независимо от количества данных</li>
              <li><strong>Память:</strong> Эффективное использование</li>
              <li><strong>Загрузка:</strong> Быстрая инициализация</li>
              <li><strong>Скроллинг:</strong> Плавный</li>
              <li><strong>Использование:</strong> Большие списки (1000+ элементов)</li>
            </ul>
          </div>
          
          <div>
            <h4>❌ Обычный список</h4>
            <ul>
              <li><strong>Производительность:</strong> Низкая при больших данных</li>
              <li><strong>Память:</strong> Высокое потребление</li>
              <li><strong>Загрузка:</strong> Медленная инициализация</li>
              <li><strong>Скроллинг:</strong> Задержки при большом количестве элементов</li>
              <li><strong>Использование:</strong> Маленькие списки (до 100 элементов)</li>
            </ul>
          </div>
        </div>
      </div>

      {/* Библиотеки для виртуализации */}
      <div style={{ 
        marginTop: '20px', 
        padding: '20px', 
        backgroundColor: '#e3f2fd',
        borderRadius: '8px'
      }}>
        <h3>Популярные библиотеки виртуализации</h3>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', gap: '15px' }}>
          <div>
            <h4>📚 react-window</h4>
            <p>Легковесная библиотека для фиксированных и переменных размеров</p>
            <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`import { FixedSizeList as List } from 'react-window';

const Row = ({ index, style }) => (
  <div style={style}>Row {index}</div>
);

const Example = () => (
  <List height={400} itemCount={1000} itemSize={35}>
    {Row}
  </List>
);`}
            </pre>
          </div>
          
          <div>
            <h4>📊 react-virtualized</h4>
            <p>Более мощная библиотека с дополнительными функциями</p>
            <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`import { List } from 'react-virtualized';

const rowRenderer = ({ key, index, style }) => (
  <div key={key} style={style}>
    Row {index}
  </div>
);

<List
  width={300}
  height={300}
  rowCount={1000}
  rowHeight={20}
  rowRenderer={rowRenderer}
/>`}
            </pre>
          </div>
        </div>
      </div>
    </div>
  );
};

export default VirtualizationExample;
Продолжаем! Следующие части будут включать серверный рендеринг (Next.js), мобильную оптимизацию, доступность (a11y) и многое другое. Хотите, чтобы я продолжил?

да
Отлично! Продолжаем с серверным рендерингом и продвинутыми темами:

Часть 23: Серверный рендеринг (SSR) и Next.js
```
Пример 75: Базовое SSR приложение
```jsx
import React, { useState, useEffect } from 'react';

// Компонент, который работает как на клиенте, так и на сервере
const ServerSideComponent: React.FC<{ initialData: string; serverTime: string }> = ({ 
  initialData, 
  serverTime 
}) => {
  const [clientTime, setClientTime] = useState<string>('');
  const [hydrated, setHydrated] = useState(false);
  const [counter, setCounter] = useState(0);

  // Эффект только на клиенте
  useEffect(() => {
    setHydrated(true);
    setClientTime(new Date().toISOString());
  }, []);

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #4CAF50',
      borderRadius: '8px',
      marginBottom: '20px',
      backgroundColor: '#f9f9f9'
    }}>
      <h3>🚀 Серверный рендеринг (SSR)</h3>
      
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px', marginBottom: '20px' }}>
        <div style={{ padding: '15px', backgroundColor: '#e3f2fd', borderRadius: '4px' }}>
          <h4>Серверные данные:</h4>
          <p><strong>Время на сервере:</strong> {serverTime}</p>
          <p><strong>Данные с сервера:</strong> {initialData}</p>
          <p><strong>Статус:</strong> ✅ Предварительно отрендерено</p>
        </div>
        
        <div style={{ padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '4px' }}>
          <h4>Клиентские данные:</h4>
          <p><strong>Время на клиенте:</strong> {clientTime || 'Загрузка...'}</p>
          <p><strong>Гидрация:</strong> {hydrated ? '✅ Завершена' : '⏳ В процессе'}</p>
          <p><strong>Счетчик:</strong> {counter}</p>
        </div>
      </div>

      {/* Интерактивные элементы */}
      <div style={{ marginBottom: '15px' }}>
        <button 
          onClick={() => setCounter(prev => prev + 1)}
          style={{ marginRight: '10px' }}
        >
          Увеличить счетчик
        </button>
        <button onClick={() => setCounter(0)}>
          Сбросить
        </button>
      </div>

      {/* Индикатор гидрации */}
      <div style={{ 
        padding: '10px', 
        backgroundColor: hydrated ? '#4CAF50' : '#ff9800',
        color: 'white',
        borderRadius: '4px',
        textAlign: 'center',
        fontWeight: 'bold'
      }}>
        {hydrated ? '✅ Приложение гидратировано' : '🔄 Идет гидрация...'}
      </div>
    </div>
  );
};

// Компонент с загрузкой данных
const DataFetchingComponent: React.FC<{ initialPosts: any[] }> = ({ initialPosts }) => {
  const [posts, setPosts] = useState(initialPosts);
  const [loading, setLoading] = useState(false);
  const [hydrated, setHydrated] = useState(false);

  useEffect(() => {
    setHydrated(true);
  }, []);

  // Функция для перезагрузки данных на клиенте
  const refetchData = async () => {
    setLoading(true);
    
    // Имитация API запроса
    setTimeout(() => {
      const newPosts = [
        { id: 1, title: 'Новый пост 1', body: 'Содержание нового поста 1' },
        { id: 2, title: 'Новый пост 2', body: 'Содержание нового поста 2' },
        { id: 3, title: 'Новый пост 3', body: 'Содержание нового поста 3' },
      ];
      
      setPosts(newPosts);
      setLoading(false);
    }, 1000);
  };

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #2196F3',
      borderRadius: '8px',
      marginBottom: '20px',
      backgroundColor: '#f0f8ff'
    }}>
      <h3>📡 Загрузка данных (SSR + Client)</h3>
      
      <div style={{ marginBottom: '15px', display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
        <div>
          <strong>Статус:</strong> {hydrated ? '✅ Гидратирован' : '🔄 Серверный рендер'}
        </div>
        <button 
          onClick={refetchData} 
          disabled={loading}
        >
          {loading ? 'Загрузка...' : 'Обновить данные'}
        </button>
      </div>

      <div style={{ display: 'grid', gap: '10px' }}>
        {posts.map(post => (
          <div
            key={post.id}
            style={{
              padding: '15px',
              border: '1px solid #ddd',
              borderRadius: '4px',
              backgroundColor: 'white'
            }}
          >
            <h4 style={{ margin: '0 0 10px 0' }}>{post.title}</h4>
            <p style={{ margin: 0, color: '#666' }}>{post.body}</p>
            <div style={{ 
              marginTop: '10px', 
              fontSize: '0.8rem', 
              color: '#999',
              display: 'flex',
              justifyContent: 'space-between'
            }}>
              <span>ID: {post.id}</span>
              <span>Источник: {post.source || 'Сервер'}</span>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
};

// Компонент с динамическим импортом (для code splitting)
const LazyComponent: React.FC = () => {
  const [showHeavy, setShowHeavy] = useState(false);
  const [HeavyComponent, setHeavyComponent] = useState<React.ComponentType | null>(null);

  const loadHeavyComponent = async () => {
    // Имитация динамического импорта
    setTimeout(() => {
      const MockHeavyComponent: React.FC = () => (
        <div style={{ 
          padding: '20px', 
          backgroundColor: '#fff3e0',
          border: '2px dashed #ff9800',
          borderRadius: '8px',
          textAlign: 'center'
        }}>
          <h4>🏗️ Динамически загруженный компонент</h4>
          <p>Этот компонент был загружен только когда стал нужен!</p>
          <p>Отлично для оптимизации начальной загрузки.</p>
        </div>
      );
      
      setHeavyComponent(() => MockHeavyComponent);
    }, 500);
  };

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #ff9800',
      borderRadius: '8px',
      marginBottom: '20px',
      backgroundColor: '#fffaf0'
    }}>
      <h3>⚡ Code Splitting & Lazy Loading</h3>
      
      <button 
        onClick={() => {
          setShowHeavy(!showHeavy);
          if (!showHeavy && !HeavyComponent) {
            loadHeavyComponent();
          }
        }}
        style={{ marginBottom: '15px' }}
      >
        {showHeavy ? 'Скрыть' : 'Показать'} тяжелый компонент
      </button>

      {showHeavy && (
        <div>
          {HeavyComponent ? (
            <HeavyComponent />
          ) : (
            <div style={{ textAlign: 'center', padding: '20px', color: '#666' }}>
              ⏳ Загрузка компонента...
            </div>
          )}
        </div>
      )}
    </div>
  );
};

// Главный компонент SSR демо
const SSRExample: React.FC = () => {
  // Имитация данных, которые пришли с сервера
  const serverData = {
    initialData: 'Данные, загруженные на сервере во время рендеринга',
    serverTime: new Date().toISOString(), // В реальном SSR это время сервера
    initialPosts: [
      { id: 1, title: 'Пост 1 с сервера', body: 'Этот пост был загружен на сервере', source: 'SSR' },
      { id: 2, title: 'Пост 2 с сервера', body: 'Этот пост также загружен на сервере', source: 'SSR' },
      { id: 3, title: 'Пост 3 с сервера', body: 'И этот пост пришел с сервера', source: 'SSR' },
    ]
  };

  return (
    <div style={{ maxWidth: '900px', margin: '0 auto', padding: '20px' }}>
      <h1>🚀 Server-Side Rendering (SSR) в React</h1>
      
      <ServerSideComponent 
        initialData={serverData.initialData}
        serverTime={serverData.serverTime}
      />
      
      <DataFetchingComponent initialPosts={serverData.initialPosts} />
      
      <LazyComponent />

      {/* Объяснение SSR */}
      <div style={{ 
        marginTop: '40px', 
        padding: '25px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h2>📖 О Server-Side Rendering (SSR)</h2>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '20px' }}>
          <div>
            <h3>🔄 Как работает SSR?</h3>
            <ol style={{ paddingLeft: '20px' }}>
              <li><strong>Запрос на сервер</strong> - пользователь запрашивает страницу</li>
              <li><strong>Рендеринг на сервере</strong> - React рендерит компоненты в HTML</li>
              <li><strong>Отправка HTML</strong> - браузер получает готовую разметку</li>
              <li><strong>Гидрация</strong> - React "оживляет" статичную разметку</li>
              <li><strong>Интерактивность</strong> - приложение становится полностью интерактивным</li>
            </ol>
          </div>
          
          <div>
            <h3>🎯 Преимущества SSR</h3>
            <ul style={{ paddingLeft: '20px' }}>
              <li><strong>SEO-friendly</strong> - поисковые системы видят контент</li>
              <li><strong>Быстрая начальная загрузка</strong> - пользователь сразу видит контент</li>
              <li><strong>Лучший UX</strong> - нет белого экрана при загрузке</li>
              <li><strong>Социальные сети</strong> - правильные превью при шаринге</li>
              <li><strong>Доступность</strong> - работает без JavaScript</li>
            </ul>
          </div>
        </div>

        {/* Сравнение подходов */}
        <div style={{ marginTop: '30px' }}>
          <h3>📊 Сравнение CSR vs SSR</h3>
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: '1fr 1fr', 
            gap: '20px',
            marginTop: '15px'
          }}>
            <div style={{ padding: '15px', backgroundColor: '#ffebee', borderRadius: '4px' }}>
              <h4>❌ Client-Side Rendering (CSR)</h4>
              <ul style={{ margin: 0, paddingLeft: '20px' }}>
                <li>Пустой HTML → Загрузка JS → Рендеринг</li>
                <li>Медленная начальная загрузка</li>
                <li>Плохо для SEO</li>
                <li>Белый экран при загрузке</li>
                <li>Проще в разработке</li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '4px' }}>
              <h4>✅ Server-Side Rendering (SSR)</h4>
              <ul style={{ margin: 0, paddingLeft: '20px' }}>
                <li>Готовый HTML → Быстрая загрузка → Гидрация</li>
                <li>Быстрая начальная загрузка</li>
                <li>Отлично для SEO</li>
                <li>Контент виден сразу</li>
                <li>Сложнее в настройке</li>
              </ul>
            </div>
          </div>
        </div>

        {/* Next.js информация */}
        <div style={{ 
          marginTop: '30px', 
          padding: '20px', 
          backgroundColor: '#000',
          color: '#fff',
          borderRadius: '8px'
        }}>
          <h3>⚡ Next.js - React Framework для Production</h3>
          <p>Next.js предоставляет встроенную поддержку SSR, SSG, ISR и многих других возможностей:</p>
          
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '15px', marginTop: '15px' }}>
            <div>
              <h4>🔧 getServerSideProps</h4>
              <p>SSR - данные загружаются на каждый запрос</p>
            </div>
            <div>
              <h4>📄 getStaticProps</h4>
              <p>SSG - статическая генерация на build time</p>
            </div>
            <div>
              <h4>🔄 getStaticPaths</h4>
              <p>Динамические маршруты для SSG</p>
            </div>
            <div>
              <h4>⚡ ISR</h4>
              <p>Инкрементальная статическая регенерация</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default SSRExample;
```
Пример 76: Next.js роутинг и API routes
```jsx
import React, { useState, useEffect } from 'react';

// Имитация Next.js роутинга
const NextJsRoutingDemo: React.FC = () => {
  const [currentPage, setCurrentPage] = useState('home');
  const [posts, setPosts] = useState<any[]>([]);
  const [loading, setLoading] = useState(false);

  // Имитация API routes Next.js
  const fetchPosts = async () => {
    setLoading(true);
    
    // Имитация запроса к /api/posts
    setTimeout(() => {
      const mockPosts = [
        { id: 1, title: 'Пост о Next.js', content: 'Next.js - отличный фреймворк для React!' },
        { id: 2, title: 'SSR преимущества', content: 'Серверный рендеринг улучшает SEO и производительность.' },
        { id: 3, title: 'API Routes', content: 'Создавайте API endpoints прямо в Next.js приложении.' },
      ];
      
      setPosts(mockPosts);
      setLoading(false);
    }, 1000);
  };

  const fetchUser = async (userId: number) => {
    setLoading(true);
    
    // Имитация запроса к /api/users/[id]
    setTimeout(() => {
      const mockUser = {
        id: userId,
        name: `Пользователь ${userId}`,
        email: `user${userId}@example.com`,
        role: userId === 1 ? 'admin' : 'user'
      };
      
      setCurrentPage('user');
      setLoading(false);
      return mockUser;
    }, 800);
  };

  // Динамические страницы
  const renderPage = () => {
    switch (currentPage) {
      case 'home':
        return (
          <div>
            <h2>🏠 Главная страница</h2>
            <p>Добро пожаловать в Next.js приложение!</p>
            <div style={{ 
              display: 'grid', 
              gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', 
              gap: '15px',
              marginTop: '20px'
            }}>
              <div style={{ padding: '15px', backgroundColor: '#e3f2fd', borderRadius: '8px' }}>
                <h4>📄 Страницы</h4>
                <p>File-based routing система</p>
              </div>
              <div style={{ padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '8px' }}>
                <h4>🔧 API Routes</h4>
                <p>Backend API в том же проекте</p>
              </div>
              <div style={{ padding: '15px', backgroundColor: '#fff3e0', borderRadius: '8px' }}>
                <h4>⚡ Производительность</h4>
                <p>Автоматическая оптимизация</p>
              </div>
            </div>
          </div>
        );
      
      case 'about':
        return (
          <div>
            <h2>📖 О нас</h2>
            <p>Узнайте больше о нашем проекте и технологии Next.js.</p>
            
            <div style={{ 
              padding: '20px', 
              backgroundColor: '#f5f5f5', 
              borderRadius: '8px',
              marginTop: '20px'
            }}>
              <h3>Технологический стек:</h3>
              <ul>
                <li>Next.js 14+</li>
                <li>React 18</li>
                <li>TypeScript</li>
                <li>Tailwind CSS</li>
                <li>Vercel Deployment</li>
              </ul>
            </div>
          </div>
        );
      
      case 'blog':
        return (
          <div>
            <h2>📝 Блог</h2>
            <p>Статьи и новости о разработке.</p>
            
            <button 
              onClick={fetchPosts}
              disabled={loading}
              style={{ margin: '20px 0' }}
            >
              {loading ? 'Загрузка...' : 'Загрузить посты'}
            </button>
            
            {posts.length > 0 && (
              <div style={{ display: 'grid', gap: '15px' }}>
                {posts.map(post => (
                  <div
                    key={post.id}
                    style={{
                      padding: '15px',
                      border: '1px solid #ddd',
                      borderRadius: '8px',
                      backgroundColor: 'white'
                    }}
                  >
                    <h4 style={{ margin: '0 0 10px 0' }}>{post.title}</h4>
                    <p style={{ margin: 0, color: '#666' }}>{post.content}</p>
                  </div>
                ))}
              </div>
            )}
          </div>
        );
      
      case 'user':
        return (
          <div>
            <h2>👤 Профиль пользователя</h2>
            <p>Страница пользователя с динамическим ID.</p>
            
            <div style={{ 
              padding: '20px', 
              backgroundColor: '#e3f2fd', 
              borderRadius: '8px',
              marginTop: '20px'
            }}>
              <h4>Динамические маршруты:</h4>
              <p>Next.js поддерживает динамические сегменты в URL:</p>
              <ul>
                <li><code>/users/[id]</code> - один параметр</li>
                <li><code>/posts/[year]/[slug]</code> - multiple параметры</li>
                <li><code>/categories/[...slug]</code> - catch-all routes</li>
              </ul>
            </div>
          </div>
        );
      
      case 'contact':
        return (
          <div>
            <h2>📞 Контакты</h2>
            <p>Свяжитесь с нами через форму обратной связи.</p>
            
            <div style={{ 
              padding: '20px', 
              backgroundColor: '#fff3e0', 
              borderRadius: '8px',
              marginTop: '20px'
            }}>
              <h4>Форма обратной связи:</h4>
              <form style={{ display: 'grid', gap: '10px', maxWidth: '400px' }}>
                <input 
                  type="text" 
                  placeholder="Ваше имя" 
                  style={{ padding: '10px', border: '1px solid #ddd', borderRadius: '4px' }}
                />
                <input 
                  type="email" 
                  placeholder="Email" 
                  style={{ padding: '10px', border: '1px solid #ddd', borderRadius: '4px' }}
                />
                <textarea 
                  placeholder="Сообщение" 
                  rows={4}
                  style={{ padding: '10px', border: '1px solid #ddd', borderRadius: '4px' }}
                />
                <button type="submit">Отправить</button>
              </form>
            </div>
          </div>
        );
      
      default:
        return <div>Страница не найдена</div>;
    }
  };

  // Навигационное меню (имитация Next.js Link)
  const Navigation: React.FC = () => (
    <nav style={{ 
      display: 'flex', 
      gap: '15px', 
      marginBottom: '30px',
      padding: '15px',
      backgroundColor: '#f5f5f5',
      borderRadius: '8px',
      flexWrap: 'wrap'
    }}>
      <button 
        onClick={() => setCurrentPage('home')}
        style={{ 
          fontWeight: currentPage === 'home' ? 'bold' : 'normal',
          color: currentPage === 'home' ? '#2196F3' : 'inherit'
        }}
      >
        🏠 Главная
      </button>
      <button 
        onClick={() => setCurrentPage('about')}
        style={{ 
          fontWeight: currentPage === 'about' ? 'bold' : 'normal',
          color: currentPage === 'about' ? '#2196F3' : 'inherit'
        }}
      >
        📖 О нас
      </button>
      <button 
        onClick={() => setCurrentPage('blog')}
        style={{ 
          fontWeight: currentPage === 'blog' ? 'bold' : 'normal',
          color: currentPage === 'blog' ? '#2196F3' : 'inherit'
        }}
      >
        📝 Блог
      </button>
      <button 
        onClick={() => fetchUser(1)}
        style={{ 
          fontWeight: currentPage === 'user' ? 'bold' : 'normal',
          color: currentPage === 'user' ? '#2196F3' : 'inherit'
        }}
      >
        👤 Профиль
      </button>
      <button 
        onClick={() => setCurrentPage('contact')}
        style={{ 
          fontWeight: currentPage === 'contact' ? 'bold' : 'normal',
          color: currentPage === 'contact' ? '#2196F3' : 'inherit'
        }}
      >
        📞 Контакты
      </button>
    </nav>
  );

  return (
    <div style={{ maxWidth: '900px', margin: '0 auto', padding: '20px' }}>
      <h1>⚡ Next.js Роутинг и API Routes</h1>
      
      <Navigation />
      
      {loading ? (
        <div style={{ 
          textAlign: 'center', 
          padding: '40px', 
          color: '#666',
          fontSize: '1.2rem'
        }}>
          ⏳ Загрузка...
        </div>
      ) : (
        renderPage()
      )}

      {/* Информация о Next.js роутинге */}
      <div style={{ 
        marginTop: '40px', 
        padding: '25px', 
        backgroundColor: '#000',
        color: '#fff',
        borderRadius: '8px'
      }}>
        <h2>🎯 Next.js File-Based Routing</h2>
        
        <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px', marginTop: '20px' }}>
          <div>
            <h3>📁 Структура папок:</h3>
            <pre style={{ 
              backgroundColor: '#333', 
              color: '#fff', 
              padding: '15px', 
              borderRadius: '4px',
              fontSize: '0.8rem',
              overflow: 'auto'
            }}>
{`pages/
  ├── index.tsx          # /
  ├── about.tsx          # /about
  ├── blog/
  │   ├── index.tsx      # /blog
  │   └── [slug].tsx     # /blog/any-slug
  ├── users/
  │   └── [id].tsx       # /users/123
  ├── api/
  │   ├── posts.ts       # /api/posts
  │   └── users/
  │       └── [id].ts    # /api/users/123
  └── 404.tsx            # 404 page`}
            </pre>
          </div>
          
          <div>
            <h3>🔗 Навигация:</h3>
            <pre style={{ 
              backgroundColor: '#333', 
              color: '#fff', 
              padding: '15px', 
              borderRadius: '4px',
              fontSize: '0.8rem'
            }}>
{`// Client-side navigation
import Link from 'next/link'

<Link href="/">Главная</Link>
<Link href="/about">О нас</Link>
<Link href="/blog/post-1">
  Пост 1
</Link>
<Link href="/users/123">
  Пользователь 123
</Link>

// Programmatic navigation
import { useRouter } from 'next/router'

const router = useRouter()
router.push('/about')`}
            </pre>
          </div>
        </div>

        {/* API Routes */}
        <div style={{ marginTop: '30px' }}>
          <h3>🔧 API Routes</h3>
          <p>Создавайте backend API endpoints прямо в Next.js приложении:</p>
          
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', 
            gap: '15px',
            marginTop: '15px'
          }}>
            <div style={{ padding: '15px', backgroundColor: '#333', borderRadius: '4px' }}>
              <h4>📝 Простой API endpoint</h4>
              <pre style={{ color: '#fff', fontSize: '0.7rem' }}>
{`// pages/api/hello.ts
export default function handler(req, res) {
  res.status(200).json({ 
    message: 'Hello World!' 
  })
}`}
              </pre>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#333', borderRadius: '4px' }}>
              <h4>🔍 API с параметрами</h4>
              <pre style={{ color: '#fff', fontSize: '0.7rem' }}>
{`// pages/api/users/[id].ts
export default function handler(req, res) {
  const { id } = req.query
  const user = findUserById(id)
  
  if (!user) {
    return res.status(404).json({ 
      error: 'User not found' 
    })
  }
  
  res.status(200).json(user)
}`}
              </pre>
            </div>
          </div>
        </div>

        {/* Динамические импорты */}
        <div style={{ marginTop: '30px' }}>
          <h3>⚡ Динамические импорты</h3>
          <p>Code splitting для оптимизации загрузки:</p>
          
          <pre style={{ 
            backgroundColor: '#333', 
            color: '#fff', 
            padding: '15px', 
            borderRadius: '4px',
            fontSize: '0.8rem',
            marginTop: '10px'
          }}>
{`import dynamic from 'next/dynamic'

// Ленивая загрузка компонента
const HeavyComponent = dynamic(
  () => import('../components/HeavyComponent'),
  { 
    loading: () => <p>Loading...</p>,
    ssr: false // Отключить SSR для этого компонента
  }
)

// Использование
function HomePage() {
  return (
    <div>
      <h1>Home Page</h1>
      <HeavyComponent />
    </div>
  )
}`}
          </pre>
        </div>
      </div>
    </div>
  );
};

export default NextJsRoutingDemo;
Часть 24: Доступность (a11y) в React
```
Пример 77: Доступные компоненты
```jsx
import React, { useState, useRef, useEffect } from 'react';

// Доступная навигация
const AccessibleNavigation: React.FC = () => {
  const [activeTab, setActiveTab] = useState(0);
  const tabListRef = useRef<HTMLDivElement>(null);

  const tabs = [
    { id: 'tab1', label: 'Главная', content: 'Содержимое главной страницы' },
    { id: 'tab2', label: 'Профиль', content: 'Информация о профиле пользователя' },
    { id: 'tab3', label: 'Настройки', content: 'Настройки приложения' },
    { id: 'tab4', label: 'Помощь', content: 'Раздел помощи и поддержки' }
  ];

  // Обработчик клавиатуры для навигации
  const handleKeyDown = (event: React.KeyboardEvent, index: number) => {
    switch (event.key) {
      case 'ArrowRight':
      case 'ArrowDown':
        event.preventDefault();
        setActiveTab((index + 1) % tabs.length);
        break;
      case 'ArrowLeft':
      case 'ArrowUp':
        event.preventDefault();
        setActiveTab((index - 1 + tabs.length) % tabs.length);
        break;
      case 'Home':
        event.preventDefault();
        setActiveTab(0);
        break;
      case 'End':
        event.preventDefault();
        setActiveTab(tabs.length - 1);
        break;
    }
  };

  // Фокус на активной табе при изменении
  useEffect(() => {
    const activeTabElement = tabListRef.current?.querySelector(
      `[role="tab"][aria-selected="true"]`
    ) as HTMLElement;
    activeTabElement?.focus();
  }, [activeTab]);

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #4CAF50',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>🎯 Доступная навигация (ARIA Tabs)</h3>
      
      <div 
        ref={tabListRef}
        role="tablist" 
        aria-label="Основные разделы сайта"
        style={{ 
          display: 'flex', 
          borderBottom: '2px solid #ddd',
          marginBottom: '20px'
        }}
      >
        {tabs.map((tab, index) => (
          <button
            key={tab.id}
            role="tab"
            aria-selected={activeTab === index}
            aria-controls={`${tab.id}-panel`}
            id={tab.id}
            tabIndex={activeTab === index ? 0 : -1}
            onClick={() => setActiveTab(index)}
            onKeyDown={(e) => handleKeyDown(e, index)}
            style={{
              padding: '12px 20px',
              border: 'none',
              backgroundColor: activeTab === index ? '#4CAF50' : 'transparent',
              color: activeTab === index ? 'white' : '#333',
              cursor: 'pointer',
              fontSize: '16px',
              flex: 1,
              textAlign: 'center',
              transition: 'all 0.3s ease'
            }}
          >
            {tab.label}
          </button>
        ))}
      </div>

      {tabs.map((tab, index) => (
        <div
          key={tab.id}
          role="tabpanel"
          id={`${tab.id}-panel`}
          aria-labelledby={tab.id}
          hidden={activeTab !== index}
          style={{
            padding: '20px',
            backgroundColor: '#f9f9f9',
            borderRadius: '4px',
            minHeight: '100px'
          }}
        >
          <h4>{tab.label}</h4>
          <p>{tab.content}</p>
        </div>
      ))}
    </div>
  );
};

// Доступная форма
const AccessibleForm: React.FC = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    phone: '',
    message: ''
  });
  const [errors, setErrors] = useState<Record<string, string>>({});
  const [submitted, setSubmitted] = useState(false);
  const nameInputRef = useRef<HTMLInputElement>(null);

  // Фокус на первом поле при загрузке
  useEffect(() => {
    nameInputRef.current?.focus();
  }, []);

  const validateForm = () => {
    const newErrors: Record<string, string> = {};

    if (!formData.name.trim()) {
      newErrors.name = 'Имя обязательно для заполнения';
    }

    if (!formData.email.trim()) {
      newErrors.email = 'Email обязателен для заполнения';
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = 'Введите корректный email адрес';
    }

    if (!formData.phone.trim()) {
      newErrors.phone = 'Телефон обязателен для заполнения';
    } else if (!/^[\d\s\-\+\(\)]+$/.test(formData.phone)) {
      newErrors.phone = 'Введите корректный номер телефона';
    }

    if (!formData.message.trim()) {
      newErrors.message = 'Сообщение не может быть пустым';
    }

    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = (event: React.FormEvent) => {
    event.preventDefault();
    
    if (validateForm()) {
      setSubmitted(true);
      // В реальном приложении здесь был бы API вызов
      setTimeout(() => {
        setSubmitted(false);
        setFormData({ name: '', email: '', phone: '', message: '' });
      }, 3000);
    } else {
      // Фокус на первое поле с ошибкой
      const firstErrorField = Object.keys(errors)[0];
      const errorElement = document.getElementById(firstErrorField);
      if (errorElement) {
        (errorElement as HTMLElement).focus();
      }
    }
  };

  const handleChange = (field: string, value: string) => {
    setFormData(prev => ({ ...prev, [field]: value }));
    
    // Очищаем ошибку при изменении поля
    if (errors[field]) {
      setErrors(prev => ({ ...prev, [field]: '' }));
    }
  };

  if (submitted) {
    return (
      <div 
        role="alert"
        aria-live="polite"
        style={{
          padding: '20px',
          backgroundColor: '#e8f5e8',
          border: '2px solid #4CAF50',
          borderRadius: '8px',
          textAlign: 'center'
        }}
      >
        <h3>✅ Форма успешно отправлена!</h3>
        <p>Спасибо за ваше сообщение. Мы свяжемся с вами в ближайшее время.</p>
      </div>
    );
  }

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #2196F3',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>📝 Доступная форма</h3>
      
      <form onSubmit={handleSubmit} noValidate>
        <div style={{ display: 'grid', gap: '20px' }}>
          {/* Поле имени */}
          <div>
            <label htmlFor="name" style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
              Имя *
            </label>
            <input
              ref={nameInputRef}
              id="name"
              type="text"
              value={formData.name}
              onChange={(e) => handleChange('name', e.target.value)}
              aria-required="true"
              aria-invalid={!!errors.name}
              aria-describedby={errors.name ? "name-error" : undefined}
              style={{
                width: '100%',
                padding: '10px',
                border: `2px solid ${errors.name ? '#f44336' : '#ddd'}`,
                borderRadius: '4px',
                fontSize: '16px'
              }}
            />
            {errors.name && (
              <div 
                id="name-error"
                role="alert"
                aria-live="polite"
                style={{ color: '#f44336', fontSize: '14px', marginTop: '5px' }}
              >
                ⚠️ {errors.name}
              </div>
            )}
          </div>

          {/* Поле email */}
          <div>
            <label htmlFor="email" style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
              Email *
            </label>
            <input
              id="email"
              type="email"
              value={formData.email}
              onChange={(e) => handleChange('email', e.target.value)}
              aria-required="true"
              aria-invalid={!!errors.email}
              aria-describedby={errors.email ? "email-error" : undefined}
              style={{
                width: '100%',
                padding: '10px',
                border: `2px solid ${errors.email ? '#f44336' : '#ddd'}`,
                borderRadius: '4px',
                fontSize: '16px'
              }}
            />
            {errors.email && (
              <div 
                id="email-error"
                role="alert"
                aria-live="polite"
                style={{ color: '#f44336', fontSize: '14px', marginTop: '5px' }}
              >
                ⚠️ {errors.email}
              </div>
            )}
          </div>

          {/* Поле телефона */}
          <div>
            <label htmlFor="phone" style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
              Телефон *
            </label>
            <input
              id="phone"
              type="tel"
              value={formData.phone}
              onChange={(e) => handleChange('phone', e.target.value)}
              aria-required="true"
              aria-invalid={!!errors.phone}
              aria-describedby={errors.phone ? "phone-error" : undefined}
              style={{
                width: '100%',
                padding: '10px',
                border: `2px solid ${errors.phone ? '#f44336' : '#ddd'}`,
                borderRadius: '4px',
                fontSize: '16px'
              }}
            />
            {errors.phone && (
              <div 
                id="phone-error"
                role="alert"
                aria-live="polite"
                style={{ color: '#f44336', fontSize: '14px', marginTop: '5px' }}
              >
                ⚠️ {errors.phone}
              </div>
            )}
          </div>

          {/* Поле сообщения */}
          <div>
            <label htmlFor="message" style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
              Сообщение *
            </label>
            <textarea
              id="message"
              value={formData.message}
              onChange={(e) => handleChange('message', e.target.value)}
              rows={4}
              aria-required="true"
              aria-invalid={!!errors.message}
              aria-describedby={errors.message ? "message-error" : undefined}
              style={{
                width: '100%',
                padding: '10px',
                border: `2px solid ${errors.message ? '#f44336' : '#ddd'}`,
                borderRadius: '4px',
                fontSize: '16px',
                resize: 'vertical'
              }}
            />
            {errors.message && (
              <div 
                id="message-error"
                role="alert"
                aria-live="polite"
                style={{ color: '#f44336', fontSize: '14px', marginTop: '5px' }}
              >
                ⚠️ {errors.message}
              </div>
            )}
          </div>

          {/* Кнопка отправки */}
          <button
            type="submit"
            style={{
              padding: '12px 30px',
              backgroundColor: '#2196F3',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              fontSize: '16px',
              cursor: 'pointer',
              justifySelf: 'start'
            }}
          >
            Отправить сообщение
          </button>
        </div>
      </form>
    </div>
  );
};

// Доступные уведомления
const AccessibleNotifications: React.FC = () => {
  const [notifications, setNotifications] = useState<Array<{
    id: number;
    type: 'success' | 'error' | 'warning' | 'info';
    message: string;
    timestamp: Date;
  }>>([]);
  const [notificationId, setNotificationId] = useState(1);

  const addNotification = (type: 'success' | 'error' | 'warning' | 'info', message: string) => {
    const newNotification = {
      id: notificationId,
      type,
      message,
      timestamp: new Date()
    };
    
    setNotifications(prev => [newNotification, ...prev]);
    setNotificationId(prev => prev + 1);

    // Автоматическое удаление через 5 секунд
    setTimeout(() => {
      setNotifications(prev => prev.filter(n => n.id !== newNotification.id));
    }, 5000);
  };

  const removeNotification = (id: number) => {
    setNotifications(prev => prev.filter(n => n.id !== id));
  };

  const getNotificationStyles = (type: string) => {
    const styles = {
      success: { backgroundColor: '#e8f5e8', borderColor: '#4CAF50', icon: '✅' },
      error: { backgroundColor: '#ffebee', borderColor: '#f44336', icon: '❌' },
      warning: { backgroundColor: '#fff3e0', borderColor: '#ff9800', icon: '⚠️' },
      info: { backgroundColor: '#e3f2fd', borderColor: '#2196F3', icon: 'ℹ️' }
    };
    return styles[type as keyof typeof styles] || styles.info;
  };

  return (
    <div style={{ 
      padding: '20px', 
      border: '2px solid #ff9800',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>🔔 Доступные уведомления</h3>
      
      <div style={{ marginBottom: '20px', display: 'flex', gap: '10px', flexWrap: 'wrap' }}>
        <button onClick={() => addNotification('success', 'Операция выполнена успешно!')}>
          ✅ Успех
        </button>
        <button onClick={() => addNotification('error', 'Произошла ошибка при выполнении операции')}>
          ❌ Ошибка
        </button>
        <button onClick={() => addNotification('warning', 'Внимание: требуется подтверждение')}>
          ⚠️ Предупреждение
        </button>
        <button onClick={() => addNotification('info', 'Новая информация доступна')}>
          ℹ️ Информация
        </button>
      </div>

      {/* Область для уведомлений */}
      <div 
        aria-live="polite"
        aria-atomic="false"
        style={{
          position: 'fixed',
          top: '20px',
          right: '20px',
          zIndex: 1000,
          minWidth: '300px'
        }}
      >
        {notifications.map(notification => {
          const styles = getNotificationStyles(notification.type);
          
          return (
            <div
              key={notification.id}
              role="alert"
              aria-live={notification.type === 'error' ? 'assertive' : 'polite'}
              style={{
                padding: '15px',
                marginBottom: '10px',
                backgroundColor: styles.backgroundColor,
                border: `2px solid ${styles.borderColor}`,
                borderRadius: '8px',
                boxShadow: '0 4px 6px rgba(0,0,0,0.1)',
                display: 'flex',
                alignItems: 'flex-start',
                gap: '10px',
                animation: 'slideIn 0.3s ease'
              }}
            >
              <span style={{ fontSize: '18px' }}>{styles.icon}</span>
              <div style={{ flex: 1 }}>
                <p style={{ margin: '0 0 5px 0', fontWeight: 'bold' }}>
                  {notification.type === 'success' && 'Успех'}
                  {notification.type === 'error' && 'Ошибка'}
                  {notification.type === 'warning' && 'Предупреждение'}
                  {notification.type === 'info' && 'Информация'}
                </p>
                <p style={{ margin: 0, fontSize: '14px' }}>{notification.message}</p>
                <p style={{ margin: '5px 0 0 0', fontSize: '12px', color: '#666' }}>
                  {notification.timestamp.toLocaleTimeString()}
                </p>
              </div>
              <button
                onClick={() => removeNotification(notification.id)}
                aria-label="Закрыть уведомление"
                style={{
                  background: 'none',
                  border: 'none',
                  fontSize: '18px',
                  cursor: 'pointer',
                  padding: '0',
                  width: '24px',
                  height: '24px',
                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'center'
                }}
              >
                ×
              </button>
            </div>
          );
        })}
      </div>

      <style>
        {`
          @keyframes slideIn {
            from {
              transform: translateX(100%);
              opacity: 0;
            }
            to {
              transform: translateX(0);
              opacity: 1;
            }
          }
        `}
      </style>
    </div>
  );
};

// Главный компонент доступности
const AccessibilityExample: React.FC = () => {
  return (
    <div style={{ maxWidth: '900px', margin: '0 auto', padding: '20px' }}>
      <h1>♿ Доступность (a11y) в React</h1>
      <p style={{ fontSize: '1.1rem', color: '#666', marginBottom: '30px' }}>
        Создание инклюзивных веб-приложений для всех пользователей
      </p>
      
      <AccessibleNavigation />
      <AccessibleForm />
      <AccessibleNotifications />

      {/* Руководство по доступности */}
      <div style={{ 
        marginTop: '40px', 
        padding: '25px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h2>📋 Руководство по доступности React</h2>
        
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', gap: '20px', marginTop: '20px' }}>
          <div>
            <h3>🎯 Основные принципы</h3>
            <ul>
              <li><strong>Семантическая HTML разметка</strong> - используйте правильные теги</li>
              <li><strong>ARIA атрибуты</strong> - дополняйте семантику когда нужно</li>
              <li><strong>Клавиатурная навигация</strong> - всё должно быть доступно с клавиатуры</li>
              <li><strong>Цветовой контраст</strong> - достаточная contrast ratio</li>
              <li><strong>Альтернативный текст</strong> - для изображений и иконок</li>
            </ul>
          </div>
          
          <div>
            <h3>🔧 Инструменты</h3>
            <ul>
              <li><strong>ESLint jsx-a11y</strong> - статический анализ кода</li>
              <li><strong>Lighthouse</strong> - аудит доступности</li>
              <li><strong>axe-core</strong> - автоматическое тестирование</li>
              <li><strong>Screen Readers</strong> - NVDA, JAWS, VoiceOver</li>
              <li><strong>Color Contrast Checkers</strong> - проверка контраста</li>
            </ul>
          </div>
        </div>

        {/* ```
Примеры ARIA */}
        <div style={{ marginTop: '30px' }}>
          <h3>🎪 ARIA Роли и атрибуты</h3>
          
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', 
            gap: '15px',
            marginTop: '15px'
          }}>
            <div style={{ padding: '15px', backgroundColor: '#e3f2fd', borderRadius: '4px' }}>
              <h4>🏷️ Роли</h4>
              <ul style={{ margin: 0, fontSize: '0.9rem' }}>
                <li><code>role="button"</code></li>
                <li><code>role="navigation"</code></li>
                <li><code>role="alert"</code></li>
                <li><code>role="dialog"</code></li>
                <li><code>role="tablist"</code></li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '4px' }}>
              <h4>📝 Состояния</h4>
              <ul style={{ margin: 0, fontSize: '0.9rem' }}>
                <li><code>aria-disabled="true"</code></li>
                <li><code>aria-hidden="true"</code></li>
                <li><code>aria-selected="true"</code></li>
                <li><code>aria-expanded="false"</code></li>
                <li><code>aria-checked="mixed"</code></li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#fff3e0', borderRadius: '4px' }}>
              <h4>🔗 Связи</h4>
              <ul style={{ margin: 0, fontSize: '0.9rem' }}>
                <li><code>aria-labelledby</code></li>
                <li><code>aria-describedby</code></li>
                <li><code>aria-controls</code></li>
                <li><code>aria-owns</code></li>
                <li><code>aria-activedescendant</code></li>
              </ul>
            </div>
          </div>
        </div>

        {/* Лучшие практики */}
        <div style={{ marginTop: '30px', padding: '20px', backgroundColor: '#fff', borderRadius: '8px' }}>
          <h3>⭐ Лучшие практики доступности</h3>
          
          <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px', marginTop: '15px' }}>
            <div>
              <h4>✅ Правильно</h4>
              <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`<button onClick={handleClick}>
  Сохранить
</button>

<nav aria-label="Основная навигация">
  <ul>
    <li><a href="/">Главная</a></li>
  </ul>
</nav>

<label htmlFor="email">Email</label>
<input id="email" type="email" />`}
              </pre>
            </div>
            
            <div>
              <h4>❌ Неправильно</h4>
              <pre style={{ backgroundColor: '#333', color: '#fff', padding: '10px', borderRadius: '4px', fontSize: '0.8rem' }}>
{`<div onClick={handleClick}>
  Сохранить
</div>

<div>
  <div><a href="/">Главная</a></div>
</div>

<span>Email</span>
<input type="email" />`}
              </pre>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default AccessibilityExample;
Продолжаем! Следующие части будут включать мобильную оптимизацию, офлайн-работу, продвинутые паттерны и финальные проекты. Хотите, чтобы я продолжил?

да
Отлично! Завершаем нашу коллекцию ```
Примеров продвинутыми темами и финальными проектами:

Часть 25: Мобильная оптимизация и PWA
```
Пример 78: Адаптивный дизайн и Touch события
```jsx
import React, { useState, useEffect, useRef } from 'react';

// Хук для определения типа устройства
const useDeviceType = () => {
  const [deviceType, setDeviceType] = useState<'mobile' | 'tablet' | 'desktop'>('desktop');

  useEffect(() => {
    const checkDevice = () => {
      const width = window.innerWidth;
      if (width < 768) setDeviceType('mobile');
      else if (width < 1024) setDeviceType('tablet');
      else setDeviceType('desktop');
    };

    checkDevice();
    window.addEventListener('resize', checkDevice);
    
    return () => window.removeEventListener('resize', checkDevice);
  }, []);

  return deviceType;
};

// Адаптивный компонент навигации
const ResponsiveNavigation: React.FC = () => {
  const deviceType = useDeviceType();
  const [isMenuOpen, setIsMenuOpen] = useState(false);

  const navItems = [
    { id: 1, label: 'Главная', icon: '🏠' },
    { id: 2, label: 'Каталог', icon: '📚' },
    { id: 3, label: 'Корзина', icon: '🛒' },
    { id: 4, label: 'Профиль', icon: '👤' },
    { id: 5, label: 'Настройки', icon: '⚙️' }
  ];

  return (
    <nav style={{
      backgroundColor: '#2c3e50',
      color: 'white',
      padding: deviceType === 'mobile' ? '10px' : '15px 20px',
      position: 'relative'
    }}>
      {/* Мобильное меню */}
      {deviceType === 'mobile' && (
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
          <button
            onClick={() => setIsMenuOpen(!isMenuOpen)}
            style={{
              background: 'none',
              border: 'none',
              color: 'white',
              fontSize: '24px',
              cursor: 'pointer'
            }}
            aria-label="Открыть меню"
          >
            ☰
          </button>
          
          <h1 style={{ margin: 0, fontSize: '18px' }}>Мой Сайт</h1>
          
          <div style={{ width: '24px' }}></div> {/* Для выравнивания */}
        </div>
      )}

      {/* Десктопное меню */}
      {deviceType !== 'mobile' && (
        <div style={{ 
          display: 'flex', 
          justifyContent: 'space-between', 
          alignItems: 'center' 
        }}>
          <h1 style={{ margin: 0 }}>Мой Сайт</h1>
          <div style={{ display: 'flex', gap: '20px' }}>
            {navItems.map(item => (
              <a
                key={item.id}
                href="#"
                style={{
                  color: 'white',
                  textDecoration: 'none',
                  padding: '8px 12px',
                  borderRadius: '4px',
                  transition: 'background-color 0.3s'
                }}
                onMouseEnter={(e) => {
                  e.currentTarget.style.backgroundColor = 'rgba(255,255,255,0.1)';
                }}
                onMouseLeave={(e) => {
                  e.currentTarget.style.backgroundColor = 'transparent';
                }}
              >
                {deviceType === 'tablet' ? item.icon : item.label}
              </a>
            ))}
          </div>
        </div>
      )}

      {/* Мобильное выпадающее меню */}
      {deviceType === 'mobile' && isMenuOpen && (
        <div style={{
          position: 'absolute',
          top: '100%',
          left: 0,
          right: 0,
          backgroundColor: '#34495e',
          zIndex: 1000
        }}>
          {navItems.map(item => (
            <a
              key={item.id}
              href="#"
              style={{
                display: 'block',
                color: 'white',
                textDecoration: 'none',
                padding: '15px 20px',
                borderBottom: '1px solid #46637f'
              }}
              onClick={() => setIsMenuOpen(false)}
            >
              <span style={{ marginRight: '10px' }}>{item.icon}</span>
              {item.label}
            </a>
          ))}
        </div>
      )}
    </nav>
  );
};

// Компонент с touch событиями
const TouchGallery: React.FC = () => {
  const [currentIndex, setCurrentIndex] = useState(0);
  const [startX, setStartX] = useState(0);
  const [isSwiping, setIsSwiping] = useState(false);
  const touchAreaRef = useRef<HTMLDivElement>(null);

  const images = [
    { id: 1, src: '🌄', title: 'Горы' },
    { id: 2, src: '🏖️', title: 'Пляж' },
    { id: 3, src: '🏙️', title: 'Город' },
    { id: 4, src: '🌅', title: 'Закат' },
    { id: 5, src: '🏞️', title: 'Природа' }
  ];

  const handleTouchStart = (e: React.TouchEvent) => {
    setStartX(e.touches[0].clientX);
    setIsSwiping(true);
  };

  const handleTouchMove = (e: React.TouchEvent) => {
    if (!isSwiping) return;
    
    const currentX = e.touches[0].clientX;
    const diff = startX - currentX;

    // Добавляем визуальную обратную связь при свайпе
    if (touchAreaRef.current) {
      touchAreaRef.current.style.transform = `translateX(-${diff * 0.1}px)`;
    }
  };

  const handleTouchEnd = (e: React.TouchEvent) => {
    if (!isSwiping) return;
    
    const endX = e.changedTouches[0].clientX;
    const diff = startX - endX;
    const swipeThreshold = 50;

    // Сброс трансформации
    if (touchAreaRef.current) {
      touchAreaRef.current.style.transform = 'translateX(0)';
    }

    if (Math.abs(diff) > swipeThreshold) {
      if (diff > 0 && currentIndex < images.length - 1) {
        // Свайп влево - следующий слайд
        setCurrentIndex(prev => prev + 1);
      } else if (diff < 0 && currentIndex > 0) {
        // Свайп вправо - предыдущий слайд
        setCurrentIndex(prev => prev - 1);
      }
    }

    setIsSwiping(false);
  };

  const nextSlide = () => {
    setCurrentIndex(prev => (prev + 1) % images.length);
  };

  const prevSlide = () => {
    setCurrentIndex(prev => (prev - 1 + images.length) % images.length);
  };

  return (
    <div style={{ 
      padding: '20px',
      maxWidth: '500px',
      margin: '0 auto'
    }}>
      <h3>📱 Touch Gallery</h3>
      
      <div
        ref={touchAreaRef}
        onTouchStart={handleTouchStart}
        onTouchMove={handleTouchMove}
        onTouchEnd={handleTouchEnd}
        style={{
          position: 'relative',
          height: '300px',
          backgroundColor: '#f0f0f0',
          borderRadius: '12px',
          display: 'flex',
          alignItems: 'center',
          justifyContent: 'center',
          fontSize: '100px',
          cursor: 'grab',
          userSelect: 'none',
          transition: isSwiping ? 'none' : 'transform 0.3s ease'
        }}
      >
        {images[currentIndex].src}
        
        {/* Индикаторы */}
        <div style={{
          position: 'absolute',
          bottom: '15px',
          left: '50%',
          transform: 'translateX(-50%)',
          display: 'flex',
          gap: '8px'
        }}>
          {images.map((_, index) => (
            <div
              key={index}
              style={{
                width: '8px',
                height: '8px',
                borderRadius: '50%',
                backgroundColor: index === currentIndex ? '#3498db' : '#bdc3c7',
                transition: 'background-color 0.3s'
              }}
            />
          ))}
        </div>
      </div>

      <div style={{ 
        display: 'flex', 
        justifyContent: 'space-between', 
        marginTop: '15px' 
      }}>
        <button onClick={prevSlide} disabled={currentIndex === 0}>
          ⬅️ Назад
        </button>
        
        <span style={{ 
          alignSelf: 'center',
          fontWeight: 'bold'
        }}>
          {images[currentIndex].title} ({currentIndex + 1}/{images.length})
        </span>
        
        <button onClick={nextSlide} disabled={currentIndex === images.length - 1}>
          Вперед ➡️
        </button>
      </div>

      <div style={{ 
        marginTop: '15px', 
        padding: '10px', 
        backgroundColor: '#ecf0f1',
        borderRadius: '6px',
        fontSize: '14px'
      }}>
        <strong>💡 Подсказка:</strong> Используйте свайпы на мобильном устройстве для навигации
      </div>
    </div>
  );
};

// Адаптивная сетка продуктов
const ResponsiveProductGrid: React.FC = () => {
  const deviceType = useDeviceType();

  const products = [
    { id: 1, name: 'Смартфон', price: '29999 ₽', emoji: '📱' },
    { id: 2, name: 'Ноутбук', price: '59999 ₽', emoji: '💻' },
    { id: 3, name: 'Наушники', price: '7999 ₽', emoji: '🎧' },
    { id: 4, name: 'Часы', price: '14999 ₽', emoji: '⌚' },
    { id: 5, name: 'Планшет', price: '24999 ₽', emoji: '📟' },
    { id: 6, name: 'Камера', price: '39999 ₽', emoji: '📷' }
  ];

  const getGridColumns = () => {
    switch (deviceType) {
      case 'mobile': return 2;
      case 'tablet': return 3;
      case 'desktop': return 4;
      default: return 3;
    }
  };

  return (
    <div style={{ padding: '20px' }}>
      <h3>🛍️ Адаптивная сетка товаров</h3>
      
      <div style={{
        display: 'grid',
        gridTemplateColumns: `repeat(${getGridColumns()}, 1fr)`,
        gap: '15px',
        marginTop: '20px'
      }}>
        {products.map(product => (
          <div
            key={product.id}
            style={{
              backgroundColor: 'white',
              border: '1px solid #ddd',
              borderRadius: '8px',
              padding: '15px',
              textAlign: 'center',
              transition: 'transform 0.2s, box-shadow 0.2s',
              cursor: 'pointer'
            }}
            onMouseEnter={(e) => {
              e.currentTarget.style.transform = 'translateY(-2px)';
              e.currentTarget.style.boxShadow = '0 4px 8px rgba(0,0,0,0.1)';
            }}
            onMouseLeave={(e) => {
              e.currentTarget.style.transform = 'translateY(0)';
              e.currentTarget.style.boxShadow = 'none';
            }}
          >
            <div style={{ fontSize: '48px', marginBottom: '10px' }}>
              {product.emoji}
            </div>
            <h4 style={{ margin: '0 0 8px 0' }}>{product.name}</h4>
            <p style={{ 
              margin: 0, 
              fontWeight: 'bold', 
              color: '#e74c3c',
              fontSize: deviceType === 'mobile' ? '14px' : '16px'
            }}>
              {product.price}
            </p>
            <button style={{
              marginTop: '10px',
              padding: '8px 16px',
              backgroundColor: '#3498db',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              width: '100%'
            }}>
              В корзину
            </button>
          </div>
        ))}
      </div>

      <div style={{ 
        marginTop: '20px', 
        padding: '15px', 
        backgroundColor: '#f8f9fa',
        borderRadius: '6px',
        fontSize: '14px'
      }}>
        <strong>📐 Адаптивность:</strong> Сетка автоматически подстраивается под размер экрана 
        ({getGridColumns()} колонки на {deviceType} устройстве)
      </div>
    </div>
  );
};

// Главный компонент мобильной оптимизации
const MobileOptimizationExample: React.FC = () => {
  const deviceType = useDeviceType();

  return (
    <div style={{ 
      minHeight: '100vh',
      backgroundColor: '#f8f9fa'
    }}>
      <ResponsiveNavigation />
      
      <main style={{ 
        padding: deviceType === 'mobile' ? '15px' : '30px',
        maxWidth: '1200px',
        margin: '0 auto'
      }}>
        <div style={{
          textAlign: 'center',
          marginBottom: '30px',
          padding: '20px',
          backgroundColor: 'white',
          borderRadius: '12px',
          boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
        }}>
          <h1>📱 Мобильная Оптимизация</h1>
          <p style={{ 
            fontSize: deviceType === 'mobile' ? '16px' : '18px',
            color: '#666'
          }}>
            Адаптивный дизайн и оптимизация для мобильных устройств
          </p>
          <div style={{
            display: 'inline-block',
            padding: '8px 16px',
            backgroundColor: '#3498db',
            color: 'white',
            borderRadius: '20px',
            fontSize: '14px',
            fontWeight: 'bold'
          }}>
            Текущее устройство: {deviceType === 'mobile' ? '📱 Мобильное' : 
                               deviceType === 'tablet' ? '📟 Планшет' : '💻 Десктоп'}
          </div>
        </div>

        <TouchGallery />
        <ResponsiveProductGrid />

        {/* Советы по мобильной оптимизации */}
        <div style={{ 
          marginTop: '40px',
          padding: '25px',
          backgroundColor: 'white',
          borderRadius: '12px',
          boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
        }}>
          <h2>🎯 Лучшие практики мобильной оптимизации</h2>
          
          <div style={{
            display: 'grid',
            gridTemplateColumns: deviceType === 'mobile' ? '1fr' : 'repeat(2, 1fr)',
            gap: '20px',
            marginTop: '20px'
          }}>
            <div style={{ padding: '15px', backgroundColor: '#e8f6f3', borderRadius: '8px' }}>
              <h4>📐 Адаптивный дизайн</h4>
              <ul style={{ margin: 0 }}>
                <li>Используйте CSS Grid и Flexbox</li>
                <li>Медиа-запросы для разных breakpoints</li>
                <li>Относительные единицы (%, rem, em)</li>
                <li>Mobile-first подход</li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#fef9e7', borderRadius: '8px' }}>
              <h4>👆 Touch-оптимизация</h4>
              <ul style={{ margin: 0 }}>
                <li>Минимальный размер тапа 44px</li>
                <li>Поддержка жестов (swipe, pinch)</li>
                <li>Адекватные hit areas</li>
                <li>Визуальная обратная связь</li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#eaf2f8', borderRadius: '8px' }}>
              <h4>⚡ Производительность</h4>
              <ul style={{ margin: 0 }}>
                <li>Оптимизация изображений</li>
                <li>Ленивая загрузка контента</li>
                <li>Минификация ресурсов</li>
                <li>Кэширование</li>
              </ul>
            </div>
            
            <div style={{ padding: '15px', backgroundColor: '#f4ecf7', borderRadius: '8px' }}>
              <h4>🎨 UX/UI для мобильных</h4>
              <ul style={{ margin: 0 }}>
                <li>Простая навигация</li>
                <li>Читабельные шрифты</li>
                <li>Достаточный контраст</li>
                <li>Портретная ориентация</li>
              </ul>
            </div>
          </div>
        </div>

        {/* Технические детали */}
        <div style={{ 
          marginTop: '20px',
          padding: '20px',
          backgroundColor: '#2c3e50',
          color: 'white',
          borderRadius: '12px'
        }}>
          <h3>🔧 Техническая реализация</h3>
          
          <div style={{
            display: 'grid',
            gridTemplateColumns: deviceType === 'mobile' ? '1fr' : 'repeat(2, 1fr)',
            gap: '15px',
            marginTop: '15px'
          }}>
            <div>
              <h4>📱 Определение устройства</h4>
              <pre style={{ 
                backgroundColor: '#34495e', 
                color: '#ecf0f1', 
                padding: '15px', 
                borderRadius: '6px',
                fontSize: '12px',
                overflow: 'auto'
              }}>
{`const useDeviceType = () => {
  const [deviceType, setDeviceType] = useState('desktop');
  
  useEffect(() => {
    const checkDevice = () => {
      const width = window.innerWidth;
      if (width < 768) setDeviceType('mobile');
      else if (width < 1024) setDeviceType('tablet');
      else setDeviceType('desktop');
    };
    
    checkDevice();
    window.addEventListener('resize', checkDevice);
    return () => window.removeEventListener('resize', checkDevice);
  }, []);
  
  return deviceType;
};`}
              </pre>
            </div>
            
            <div>
              <h4>👆 Touch события</h4>
              <pre style={{ 
                backgroundColor: '#34495e', 
                color: '#ecf0f1', 
                padding: '15px', 
                borderRadius: '6px',
                fontSize: '12px',
                overflow: 'auto'
              }}>
{`const handleTouchStart = (e) => {
  setStartX(e.touches[0].clientX);
};

const handleTouchMove = (e) => {
  const diff = startX - e.touches[0].clientX;
  // Визуальная обратная связь
};

const handleTouchEnd = (e) => {
  const diff = startX - e.changedTouches[0].clientX;
  if (Math.abs(diff) > 50) {
    // Обработка свайпа
  }
};`}
              </pre>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
};

export default MobileOptimizationExample;
Часть 26: Финальные проекты
```
Пример 79: Полноценное приложение задач (Todo App)
```jsx
import React, { useState, useEffect, useReducer, useCallback } from 'react';

// Типы
interface Todo {
  id: string;
  text: string;
  completed: boolean;
  category: string;
  priority: 'low' | 'medium' | 'high';
  createdAt: Date;
  dueDate?: Date;
}

interface TodoState {
  todos: Todo[];
  filter: 'all' | 'active' | 'completed';
  searchQuery: string;
  categoryFilter: string;
  sortBy: 'date' | 'priority' | 'text';
}

type TodoAction =
  | { type: 'ADD_TODO'; payload: Omit<Todo, 'id' | 'createdAt'> }
  | { type: 'TOGGLE_TODO'; payload: string }
  | { type: 'DELETE_TODO'; payload: string }
  | { type: 'EDIT_TODO'; payload: { id: string; text: string } }
  | { type: 'SET_FILTER'; payload: 'all' | 'active' | 'completed' }
  | { type: 'SET_SEARCH_QUERY'; payload: string }
  | { type: 'SET_CATEGORY_FILTER'; payload: string }
  | { type: 'SET_SORT_BY'; payload: 'date' | 'priority' | 'text' }
  | { type: 'LOAD_TODOS'; payload: Todo[] };

// Редуктор
const todoReducer = (state: TodoState, action: TodoAction): TodoState => {
  switch (action.type) {
    case 'ADD_TODO':
      const newTodo: Todo = {
        ...action.payload,
        id: Date.now().toString(),
        createdAt: new Date()
      };
      return {
        ...state,
        todos: [newTodo, ...state.todos]
      };

    case 'TOGGLE_TODO':
      return {
        ...state,
        todos: state.todos.map(todo =>
          todo.id === action.payload
            ? { ...todo, completed: !todo.completed }
            : todo
        )
      };

    case 'DELETE_TODO':
      return {
        ...state,
        todos: state.todos.filter(todo => todo.id !== action.payload)
      };

    case 'EDIT_TODO':
      return {
        ...state,
        todos: state.todos.map(todo =>
          todo.id === action.payload.id
            ? { ...todo, text: action.payload.text }
            : todo
        )
      };

    case 'SET_FILTER':
      return {
        ...state,
        filter: action.payload
      };

    case 'SET_SEARCH_QUERY':
      return {
        ...state,
        searchQuery: action.payload
      };

    case 'SET_CATEGORY_FILTER':
      return {
        ...state,
        categoryFilter: action.payload
      };

    case 'SET_SORT_BY':
      return {
        ...state,
        sortBy: action.payload
      };

    case 'LOAD_TODOS':
      return {
        ...state,
        todos: action.payload
      };

    default:
      return state;
  }
};

// Начальное состояние
const initialState: TodoState = {
  todos: [],
  filter: 'all',
  searchQuery: '',
  categoryFilter: 'all',
  sortBy: 'date'
};

// Кастомный хук для управления задачами
const useTodos = () => {
  const [state, dispatch] = useReducer(todoReducer, initialState);

  // Загрузка из localStorage
  useEffect(() => {
    const savedTodos = localStorage.getItem('todos');
    if (savedTodos) {
      try {
        const parsedTodos = JSON.parse(savedTodos).map((todo: any) => ({
          ...todo,
          createdAt: new Date(todo.createdAt),
          dueDate: todo.dueDate ? new Date(todo.dueDate) : undefined
        }));
        dispatch({ type: 'LOAD_TODOS', payload: parsedTodos });
      } catch (error) {
        console.error('Error loading todos:', error);
      }
    }
  }, []);

  // Сохранение в localStorage
  useEffect(() => {
    localStorage.setItem('todos', JSON.stringify(state.todos));
  }, [state.todos]);

  const addTodo = useCallback((todoData: Omit<Todo, 'id' | 'createdAt'>) => {
    dispatch({ type: 'ADD_TODO', payload: todoData });
  }, []);

  const toggleTodo = useCallback((id: string) => {
    dispatch({ type: 'TOGGLE_TODO', payload: id });
  }, []);

  const deleteTodo = useCallback((id: string) => {
    dispatch({ type: 'DELETE_TODO', payload: id });
  }, []);

  const editTodo = useCallback((id: string, text: string) => {
    dispatch({ type: 'EDIT_TODO', payload: { id, text } });
  }, []);

  const setFilter = useCallback((filter: 'all' | 'active' | 'completed') => {
    dispatch({ type: 'SET_FILTER', payload: filter });
  }, []);

  const setSearchQuery = useCallback((query: string) => {
    dispatch({ type: 'SET_SEARCH_QUERY', payload: query });
  }, []);

  const setCategoryFilter = useCallback((category: string) => {
    dispatch({ type: 'SET_CATEGORY_FILTER', payload: category });
  }, []);

  const setSortBy = useCallback((sortBy: 'date' | 'priority' | 'text') => {
    dispatch({ type: 'SET_SORT_BY', payload: sortBy });
  }, []);

  // Фильтрация и сортировка задач
  const filteredAndSortedTodos = useCallback(() => {
    let filtered = state.todos.filter(todo => {
      const matchesFilter =
        state.filter === 'all' ||
        (state.filter === 'active' && !todo.completed) ||
        (state.filter === 'completed' && todo.completed);

      const matchesSearch = todo.text
        .toLowerCase()
        .includes(state.searchQuery.toLowerCase());

      const matchesCategory =
        state.categoryFilter === 'all' || todo.category === state.categoryFilter;

      return matchesFilter && matchesSearch && matchesCategory;
    });

    // Сортировка
    filtered.sort((a, b) => {
      switch (state.sortBy) {
        case 'priority':
          const priorityOrder = { high: 3, medium: 2, low: 1 };
          return priorityOrder[b.priority] - priorityOrder[a.priority];
        case 'text':
          return a.text.localeCompare(b.text);
        case 'date':
        default:
          return b.createdAt.getTime() - a.createdAt.getTime();
      }
    });

    return filtered;
  }, [state.todos, state.filter, state.searchQuery, state.categoryFilter, state.sortBy]);

  // Статистика
  const stats = useCallback(() => {
    const total = state.todos.length;
    const completed = state.todos.filter(todo => todo.completed).length;
    const active = total - completed;
    const categories = [...new Set(state.todos.map(todo => todo.category))];

    return { total, completed, active, categories };
  }, [state.todos]);

  return {
    todos: filteredAndSortedTodos(),
    stats: stats(),
    filters: {
      current: state.filter,
      searchQuery: state.searchQuery,
      categoryFilter: state.categoryFilter,
      sortBy: state.sortBy
    },
    actions: {
      addTodo,
      toggleTodo,
      deleteTodo,
      editTodo,
      setFilter,
      setSearchQuery,
      setCategoryFilter,
      setSortBy
    }
  };
};

// Компонент формы добавления задачи
const TodoForm: React.FC<{ onAddTodo: (todo: Omit<Todo, 'id' | 'createdAt'>) => void }> = ({ onAddTodo }) => {
  const [text, setText] = useState('');
  const [category, setCategory] = useState('Работа');
  const [priority, setPriority] = useState<'low' | 'medium' | 'high'>('medium');
  const [dueDate, setDueDate] = useState('');

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (text.trim()) {
      onAddTodo({
        text: text.trim(),
        category,
        priority,
        completed: false,
        dueDate: dueDate ? new Date(dueDate) : undefined
      });
      setText('');
      setCategory('Работа');
      setPriority('medium');
      setDueDate('');
    }
  };

  return (
    <form onSubmit={handleSubmit} style={{
      padding: '20px',
      backgroundColor: 'white',
      borderRadius: '12px',
      boxShadow: '0 2px 10px rgba(0,0,0,0.1)',
      marginBottom: '20px'
    }}>
      <h3 style={{ marginTop: 0 }}>➕ Новая задача</h3>
      
      <div style={{ display: 'grid', gap: '15px' }}>
        <div>
          <input
            type="text"
            value={text}
            onChange={(e) => setText(e.target.value)}
            placeholder="Что нужно сделать?"
            style={{
              width: '100%',
              padding: '12px',
              border: '2px solid #e1e8ed',
              borderRadius: '8px',
              fontSize: '16px'
            }}
          />
        </div>

        <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr 1fr', gap: '10px' }}>
          <select
            value={category}
            onChange={(e) => setCategory(e.target.value)}
            style={{
              padding: '10px',
              border: '2px solid #e1e8ed',
              borderRadius: '8px',
              fontSize: '14px'
            }}
          >
            <option value="Работа">💼 Работа</option>
            <option value="Личное">🏠 Личное</option>
            <option value="Здоровье">💪 Здоровье</option>
            <option value="Обучение">📚 Обучение</option>
            <option value="Другое">🔮 Другое</option>
          </select>

          <select
            value={priority}
            onChange={(e) => setPriority(e.target.value as 'low' | 'medium' | 'high')}
            style={{
              padding: '10px',
              border: '2px solid #e1e8ed',
              borderRadius: '8px',
              fontSize: '14px'
            }}
          >
            <option value="low">🟢 Низкий</option>
            <option value="medium">🟡 Средний</option>
            <option value="high">🔴 Высокий</option>
          </select>

          <input
            type="date"
            value={dueDate}
            onChange={(e) => setDueDate(e.target.value)}
            style={{
              padding: '10px',
              border: '2px solid #e1e8ed',
              borderRadius: '8px',
              fontSize: '14px'
            }}
          />
        </div>

        <button
          type="submit"
          disabled={!text.trim()}
          style={{
            padding: '12px 24px',
            backgroundColor: '#3498db',
            color: 'white',
            border: 'none',
            borderRadius: '8px',
            fontSize: '16px',
            cursor: text.trim() ? 'pointer' : 'not-allowed',
            opacity: text.trim() ? 1 : 0.6
          }}
        >
          Добавить задачу
        </button>
      </div>
    </form>
  );
};

// Компонент задачи
const TodoItem: React.FC<{
  todo: Todo;
  onToggle: (id: string) => void;
  onDelete: (id: string) => void;
  onEdit: (id: string, text: string) => void;
}> = ({ todo, onToggle, onDelete, onEdit }) => {
  const [isEditing, setIsEditing] = useState(false);
  const [editText, setEditText] = useState(todo.text);

  const handleEdit = () => {
    if (editText.trim() && editText !== todo.text) {
      onEdit(todo.id, editText.trim());
    }
    setIsEditing(false);
  };

  const getPriorityColor = (priority: string) => {
    switch (priority) {
      case 'high': return '#e74c3c';
      case 'medium': return '#f39c12';
      case 'low': return '#27ae60';
      default: return '#95a5a6';
    }
  };

  const getCategoryEmoji = (category: string) => {
    switch (category) {
      case 'Работа': return '💼';
      case 'Личное': return '🏠';
      case 'Здоровье': return '💪';
      case 'Обучение': return '📚';
      default: return '🔮';
    }
  };

  return (
    <div style={{
      padding: '15px',
      backgroundColor: 'white',
      border: `2px solid ${getPriorityColor(todo.priority)}`,
      borderRadius: '8px',
      marginBottom: '10px',
      opacity: todo.completed ? 0.7 : 1,
      transition: 'all 0.3s ease'
    }}>
      <div style={{ display: 'flex', alignItems: 'flex-start', gap: '12px' }}>
        <input
          type="checkbox"
          checked={todo.completed}
          onChange={() => onToggle(todo.id)}
          style={{
            width: '20px',
            height: '20px',
            marginTop: '2px'
          }}
        />
        
        <div style={{ flex: 1 }}>
          {isEditing ? (
            <input
              type="text"
              value={editText}
              onChange={(e) => setEditText(e.target.value)}
              onBlur={handleEdit}
              onKeyDown={(e) => {
                if (e.key === 'Enter') handleEdit();
                if (e.key === 'Escape') {
                  setEditText(todo.text);
                  setIsEditing(false);
                }
              }}
              autoFocus
              style={{
                width: '100%',
                padding: '8px',
                border: '1px solid #3498db',
                borderRadius: '4px',
                fontSize: '16px'
              }}
            />
          ) : (
            <div
              style={{
                textDecoration: todo.completed ? 'line-through' : 'none',
                color: todo.completed ? '#7f8c8d' : '#2c3e50',
                fontSize: '16px',
                cursor: 'pointer'
              }}
              onDoubleClick={() => setIsEditing(true)}
            >
              {todo.text}
            </div>
          )}
          
          <div style={{ 
            display: 'flex', 
            gap: '15px', 
            marginTop: '8px',
            fontSize: '12px',
            color: '#7f8c8d'
          }}>
            <span>{getCategoryEmoji(todo.category)} {todo.category}</span>
            <span>📅 {todo.createdAt.toLocaleDateString()}</span>
            {todo.dueDate && (
              <span>⏰ {todo.dueDate.toLocaleDateString()}</span>
            )}
          </div>
        </div>

        <div style={{ display: 'flex', gap: '8px' }}>
          <button
            onClick={() => setIsEditing(!isEditing)}
            style={{
              padding: '6px 12px',
              backgroundColor: '#3498db',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              fontSize: '12px'
            }}
          >
            ✏️
          </button>
          <button
            onClick={() => onDelete(todo.id)}
            style={{
              padding: '6px 12px',
              backgroundColor: '#e74c3c',
              color: 'white',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              fontSize: '12px'
            }}
          >
            🗑️
          </button>
        </div>
      </div>
    </div>
  );
};

// Компонент фильтров и статистики
const TodoFilters: React.FC<{
  stats: { total: number; completed: number; active: number; categories: string[] };
  filters: any;
  onFilterChange: (filter: 'all' | 'active' | 'completed') => void;
  onSearchChange: (query: string) => void;
  onCategoryChange: (category: string) => void;
  onSortChange: (sortBy: 'date' | 'priority' | 'text') => void;
}> = ({ stats, filters, onFilterChange, onSearchChange, onCategoryChange, onSortChange }) => {
  return (
    <div style={{
      padding: '20px',
      backgroundColor: 'white',
      borderRadius: '12px',
      boxShadow: '0 2px 10px rgba(0,0,0,0.1)',
      marginBottom: '20px'
    }}>
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px', marginBottom: '20px' }}>
        {/* Статистика */}
        <div>
          <h4 style={{ marginTop: 0 }}>📊 Статистика</h4>
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: '10px' }}>
            <div style={{ textAlign: 'center', padding: '10px', backgroundColor: '#e3f2fd', borderRadius: '6px' }}>
              <div style={{ fontSize: '24px', fontWeight: 'bold' }}>{stats.total}</div>
              <div style={{ fontSize: '12px' }}>Всего</div>
            </div>
            <div style={{ textAlign: 'center', padding: '10px', backgroundColor: '#e8f5e8', borderRadius: '6px' }}>
              <div style={{ fontSize: '24px', fontWeight: 'bold' }}>{stats.active}</div>
              <div style={{ fontSize: '12px' }}>Активные</div>
            </div>
            <div style={{ textAlign: 'center', padding: '10px', backgroundColor: '#ffebee', borderRadius: '6px' }}>
              <div style={{ fontSize: '24px', fontWeight: 'bold' }}>{stats.completed}</div>
              <div style={{ fontSize: '12px' }}>Выполнено</div>
            </div>
          </div>
        </div>

        {/* Фильтры */}
        <div>
          <h4 style={{ marginTop: 0 }}>🔍 Фильтры</h4>
          <div style={{ display: 'flex', gap: '10px', flexWrap: 'wrap' }}>
            <button
              onClick={() => onFilterChange('all')}
              style={{
                padding: '8px 12px',
                backgroundColor: filters.current === 'all' ? '#3498db' : '#ecf0f1',
                color: filters.current === 'all' ? 'white' : '#2c3e50',
                border: 'none',
                borderRadius: '6px',
                cursor: 'pointer'
              }}
            >
              Все
            </button>
            <button
              onClick={() => onFilterChange('active')}
              style={{
                padding: '8px 12px',
                backgroundColor: filters.current === 'active' ? '#3498db' : '#ecf0f1',
                color: filters.current === 'active' ? 'white' : '#2c3e50',
                border: 'none',
                borderRadius: '6px',
                cursor: 'pointer'
              }}
            >
              Активные
            </button>
            <button
              onClick={() => onFilterChange('completed')}
              style={{
                padding: '8px 12px',
                backgroundColor: filters.current === 'completed' ? '#3498db' : '#ecf0f1',
                color: filters.current === 'completed' ? 'white' : '#2c3e50',
                border: 'none',
                borderRadius: '6px',
                cursor: 'pointer'
              }}
            >
              Выполненные
            </button>
          </div>
        </div>
      </div>

      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr 1fr', gap: '15px' }}>
        {/* Поиск */}
        <div>
          <label style={{ display: 'block', marginBottom: '5px', fontSize: '14px', fontWeight: 'bold' }}>
            Поиск:
          </label>
          <input
            type="text"
            value={filters.searchQuery}
            onChange={(e) => onSearchChange(e.target.value)}
            placeholder="Поиск задач..."
            style={{
              width: '100%',
              padding: '8px',
              border: '1px solid #ddd',
              borderRadius: '4px',
              fontSize: '14px'
            }}
          />
        </div>

        {/* Категории */}
        <div>
          <label style={{ display: 'block', marginBottom: '5px', fontSize: '14px', fontWeight: 'bold' }}>
            Категория:
          </label>
          <select
            value={filters.categoryFilter}
            onChange={(e) => onCategoryChange(e.target.value)}
            style={{
              width: '100%',
              padding: '8px',
              border: '1px solid #ddd',
              borderRadius: '4px',
              fontSize: '14px'
            }}
          >
            <option value="all">Все категории</option>
            {stats.categories.map(category => (
              <option key={category} value={category}>{category}</option>
            ))}
          </select>
        </div>

        {/* Сортировка */}
        <div>
          <label style={{ display: 'block', marginBottom: '5px', fontSize: '14px', fontWeight: 'bold' }}>
            Сортировка:
          </label>
          <select
            value={filters.sortBy}
            onChange={(e) => onSortChange(e.target.value as 'date' | 'priority' | 'text')}
            style={{
              width: '100%',
              padding: '8px',
              border: '1px solid #ddd',
              borderRadius: '4px',
              fontSize: '14px'
            }}
          >
            <option value="date">По дате</option>
            <option value="priority">По приоритету</option>
            <option value="text">По названию</option>
          </select>
        </div>
      </div>
    </div>
  );
};

// Главный компонент приложения
const AdvancedTodoApp: React.FC = () => {
  const { todos, stats, filters, actions } = useTodos();

  return (
    <div style={{
      minHeight: '100vh',
      backgroundColor: '#f8f9fa',
      padding: '20px'
    }}>
      <div style={{
        maxWidth: '800px',
        margin: '0 auto'
      }}>
        <header style={{ textAlign: 'center', marginBottom: '30px' }}>
          <h1 style={{ 
            color: '#2c3e50', 
            marginBottom: '10px',
            fontSize: '2.5rem'
          }}>
            ✅ Advanced Todo App
          </h1>
          <p style={{ 
            color: '#7f8c8d', 
            fontSize: '1.1rem',
            margin: 0
          }}>
            Умное управление задачами с фильтрами, категориями и приоритетами
          </p>
        </header>

        <TodoForm onAddTodo={actions.addTodo} />
        <TodoFilters
          stats={stats}
          filters={filters}
          onFilterChange={actions.setFilter}
          onSearchChange={actions.setSearchQuery}
          onCategoryChange={actions.setCategoryFilter}
          onSortChange={actions.setSortBy}
        />

        <div style={{
          backgroundColor: 'white',
          borderRadius: '12px',
          boxShadow: '0 2px 10px rgba(0,0,0,0.1)',
          padding: '20px'
        }}>
          <h3 style={{ marginTop: 0, marginBottom: '20px' }}>
            📝 Задачи ({todos.length})
          </h3>

          {todos.length === 0 ? (
            <div style={{
              textAlign: 'center',
              padding: '40px',
              color: '#7f8c8d'
            }}>
              <div style={{ fontSize: '48px', marginBottom: '10px' }}>📭</div>
              <p>Задачи не найдены</p>
              <p style={{ fontSize: '14px' }}>
                {filters.searchQuery || filters.categoryFilter !== 'all' || filters.current !== 'all'
                  ? 'Попробуйте изменить фильтры'
                  : 'Добавьте первую задачу!'}
              </p>
            </div>
          ) : (
            <div>
              {todos.map(todo => (
                <TodoItem
                  key={todo.id}
                  todo={todo}
                  onToggle={actions.toggleTodo}
                  onDelete={actions.deleteTodo}
                  onEdit={actions.editTodo}
                />
              ))}
            </div>
          )}
        </div>

        {/* Информация о функциях */}
        <div style={{
          marginTop: '30px',
          padding: '20px',
          backgroundColor: '#2c3e50',
          color: 'white',
          borderRadius: '12px'
        }}>
          <h3 style={{ marginTop: 0, color: 'white' }}>🚀 Возможности приложения</h3>
          <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', gap: '15px' }}>
            <div>
              <h4>💾 Сохранение данных</h4>
              <p>Автоматическое сохранение в localStorage</p>
            </div>
            <div>
              <h4>🔍 Умные фильтры</h4>
              <p>Поиск, категории, статус, приоритет</p>
            </div>
            <div>
              <h4>⚡ Производительность</h4>
              <p>useReducer, useCallback, memoization</p>
            </div>
            <div>
              <h4>📱 Адаптивность</h4>
              <p>Оптимизировано для всех устройств</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default AdvancedTodoApp;
```
Пример 80: Финал - Сводка всех концепций
```jsx
import React, { useState, useEffect, useMemo, useCallback, useRef, createContext, useContext, useReducer } from 'react';

// Контекст для темы
const ThemeContext = createContext<{
  theme: 'light' | 'dark';
  toggleTheme: () => void;
}>({
  theme: 'light',
  toggleTheme: () => {}
});

// Кастомный хук для анимаций
const useAnimation = (duration: number = 300) => {
  const [isAnimating, setIsAnimating] = useState(false);

  const animate = useCallback(() => {
    setIsAnimating(true);
    const timer = setTimeout(() => setIsAnimating(false), duration);
    return () => clearTimeout(timer);
  }, [duration]);

  return { isAnimating, animate };
};

// Компонент с всеми концепциями React
const ReactConceptsDemo: React.FC = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);
  const [count, setCount] = useState(0);
  const [inputValue, setInputValue] = useState('');
  const [items, setItems] = useState<string[]>([]);
  const inputRef = useRef<HTMLInputElement>(null);
  const { isAnimating, animate } = useAnimation(500);

  // useMemo для дорогих вычислений
  const computedValue = useMemo(() => {
    console.log('Вычисление...');
    return count * 2 + items.length;
  }, [count, items.length]);

  // useCallback для стабильных функций
  const addItem = useCallback(() => {
    if (inputValue.trim()) {
      setItems(prev => [...prev, inputValue.trim()]);
      setInputValue('');
      animate();
    }
  }, [inputValue, animate]);

  // useEffect для side effects
  useEffect(() => {
    if (inputRef.current) {
      inputRef.current.focus();
    }
  }, []);

  const handleKeyPress = (e: React.KeyboardEvent) => {
    if (e.key === 'Enter') {
      addItem();
    }
  };

  return (
    <div style={{
      padding: '20px',
      backgroundColor: theme === 'light' ? '#ffffff' : '#1a1a1a',
      color: theme === 'light' ? '#000000' : '#ffffff',
      borderRadius: '12px',
      marginBottom: '20px',
      transition: 'all 0.3s ease'
    }}>
      <h3>⚛️ Все концепции React в одном компоненте</h3>
      
      <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px' }}>
        {/* useState и useRef */}
        <div>
          <h4>🔄 useState & useRef</h4>
          <div style={{ display: 'flex', gap: '10px', alignItems: 'center', marginBottom: '15px' }}>
            <button onClick={() => setCount(prev => prev - 1)}>-</button>
            <span style={{ 
              fontSize: '24px', 
              fontWeight: 'bold',
              color: theme === 'light' ? '#3498db' : '#3498db'
            }}>
              {count}
            </span>
            <button onClick={() => setCount(prev => prev + 1)}>+</button>
          </div>

          <div style={{ display: 'flex', gap: '10px', marginBottom: '15px' }}>
            <input
              ref={inputRef}
              value={inputValue}
              onChange={(e) => setInputValue(e.target.value)}
              onKeyPress={handleKeyPress}
              placeholder="Введите текст..."
              style={{
                flex: 1,
                padding: '8px',
                border: `1px solid ${theme === 'light' ? '#ddd' : '#555'}`,
                borderRadius: '4px',
                backgroundColor: theme === 'light' ? 'white' : '#333',
                color: theme === 'light' ? 'black' : 'white'
              }}
            />
            <button onClick={addItem}>Добавить</button>
          </div>
        </div>

        {/* useMemo и useEffect */}
        <div>
          <h4>💾 useMemo & useEffect</h4>
          <p>Вычисленное значение: <strong>{computedValue}</strong></p>
          <p>Количество элементов: {items.length}</p>
          <div style={{ 
            padding: '10px', 
            backgroundColor: theme === 'light' ? '#f8f9fa' : '#2a2a2a',
            borderRadius: '6px',
            fontSize: '14px'
          }}>
            useMemo предотвращает повторные вычисления, useEffect управляет side effects
          </div>
        </div>
      </div>

      {/* Список элементов с анимацией */}
      <div style={{ marginTop: '20px' }}>
        <h4>📝 Список элементов</h4>
        <div style={{
          display: 'grid',
          gap: '8px',
          maxHeight: '200px',
          overflowY: 'auto'
        }}>
          {items.map((item, index) => (
            <div
              key={index}
              style={{
                padding: '10px',
                backgroundColor: theme === 'light' ? '#e3f2fd' : '#2c3e50',
                borderRadius: '6px',
                transform: isAnimating ? 'scale(1.05)' : 'scale(1)',
                transition: 'transform 0.3s ease'
              }}
            >
              {item}
            </div>
          ))}
        </div>
      </div>
    </div>
  );
};

// Главный компонент финального ```
Примера
const ReactMasterclass: React.FC = () => {
  const [theme, setTheme] = useState<'light' | 'dark'>('light');

  const toggleTheme = useCallback(() => {
    setTheme(prev => prev === 'light' ? 'dark' : 'light');
  }, []);

  const themeContextValue = useMemo(() => ({
    theme,
    toggleTheme
  }), [theme, toggleTheme]);

  return (
    <ThemeContext.Provider value={themeContextValue}>
      <div style={{
        minHeight: '100vh',
        backgroundColor: theme === 'light' ? '#f8f9fa' : '#121212',
        color: theme === 'light' ? '#000000' : '#ffffff',
        transition: 'all 0.3s ease'
      }}>
        <div style={{
          maxWidth: '1000px',
          margin: '0 auto',
          padding: '20px'
        }}>
          <header style={{
            textAlign: 'center',
            marginBottom: '40px',
            padding: '30px',
            backgroundColor: theme === 'light' ? 'white' : '#1a1a1a',
            borderRadius: '16px',
            boxShadow: '0 4px 20px rgba(0,0,0,0.1)'
          }}>
            <h1 style={{ 
              fontSize: '3rem', 
              marginBottom: '10px',
              background: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
              WebkitBackgroundClip: 'text',
              WebkitTextFillColor: 'transparent'
            }}>
              🚀 React Мастерство
            </h1>
            <p style={{ 
              fontSize: '1.2rem',
              color: theme === 'light' ? '#666' : '#ccc',
              marginBottom: '20px'
            }}>
              200+ ```
Примеров от основ до продвинутых концепций
            </p>
            <button
              onClick={toggleTheme}
              style={{
                padding: '12px 24px',
                backgroundColor: theme === 'light' ? '#2c3e50' : '#f39c12',
                color: 'white',
                border: 'none',
                borderRadius: '8px',
                cursor: 'pointer',
                fontSize: '16px',
                fontWeight: 'bold'
              }}
            >
              {theme === 'light' ? '🌙 Тёмная тема' : '☀️ Светлая тема'}
            </button>
          </header>

          <ReactConceptsDemo />

          {/* Итог изученного */}
          <div style={{
            display: 'grid',
            gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))',
            gap: '20px',
            marginBottom: '40px'
          }}>
            <div style={{
              padding: '25px',
              backgroundColor: theme === 'light' ? 'white' : '#1a1a1a',
              borderRadius: '12px',
              boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
            }}>
              <h3>✅ Основы React</h3>
              <ul>
                <li>Компоненты и JSX</li>
                <li>Props и State</li>
                <li>Обработка событий</li>
                <li>Условный рендеринг</li>
                <li>Списки и ключи</li>
              </ul>
            </div>

            <div style={{
              padding: '25px',
              backgroundColor: theme === 'light' ? 'white' : '#1a1a1a',
              borderRadius: '12px',
              boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
            }}>
              <h3>🎯 Хуки</h3>
              <ul>
                <li>useState, useEffect</li>
                <li>useContext, useReducer</li>
                <li>useMemo, useCallback</li>
                <li>useRef, useImperativeHandle</li>
                <li>Кастомные хуки</li>
              </ul>
            </div>

            <div style={{
              padding: '25px',
              backgroundColor: theme === 'light' ? 'white' : '#1a1a1a',
              borderRadius: '12px',
              boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
            }}>
              <h3>⚡ Продвинутые темы</h3>
              <ul>
                <li>Оптимизация производительности</li>
                <li>Тестирование компонентов</li>
                <li>TypeScript с React</li>
                <li>SSR и Next.js</li>
                <li>PWA и офлайн-работа</li>
              </ul>
            </div>
          </div>

          {/* Заключение */}
          <div style={{
            padding: '30px',
            backgroundColor: theme === 'light' ? '#e8f5e8' : '#1b5e20',
            borderRadius: '12px',
            textAlign: 'center'
          }}>
            <h2>🎉 Поздравляем с завершением!</h2>
            <p style={{ fontSize: '1.1rem', marginBottom: '20px' }}>
              Вы изучили 200+ ```
Примеров React и теперь готовы создавать современные, 
              производительные веб-приложения любой сложности.
            </p>
            <div style={{
              display: 'inline-grid',
              gridTemplateColumns: 'repeat(3, 1fr)',
              gap: '15px',
              marginTop: '20px'
            }}>
              <div style={{ textAlign: 'center' }}>
                <div style={{ fontSize: '2rem' }}>⚛️</div>
                <div>React Fundamentals</div>
              </div>
              <div style={{ textAlign: 'center' }}>
                <div style={{ fontSize: '2rem' }}>🚀</div>
                <div>Advanced Patterns</div>
              </div>
              <div style={{ textAlign: 'center' }}>
                <div style={{ fontSize: '2rem' }}>🎯</div>
                <div>Production Ready</div>
              </div>
            </div>
          </div>

          {/* Следующие шаги */}
          <div style={{
            marginTop: '40px',
            padding: '25px',
            backgroundColor: theme === 'light' ? '#e3f2fd' : '#0d47a1',
            borderRadius: '12px'
          }}>
            <h3>🛣️ Следующие шаги в изучении React</h3>
            <div style={{
              display: 'grid',
              gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))',
              gap: '15px',
              marginTop: '15px'
            }}>
              <div>
                <h4>📚 State Management</h4>
                <ul>
                  <li>Redux Toolkit</li>
                  <li>Zustand</li>
                  <li>Recoil</li>
                  <li>Jotai</li>
                </ul>
              </div>
              <div>
                <h4>🎨 UI Libraries</h4>
                <ul>
                  <li>Material-UI</li>
                  <li>Ant Design</li>
                  <li>Chakra UI</li>
                  <li>Tailwind CSS</li>
                </ul>
              </div>
              <div>
                <h4>🔧 Frameworks</h4>
                <ul>
                  <li>Next.js</li>
                  <li>Remix</li>
                  <li>Gatsby</li>
                  <li>React Native</li>
                </ul>
              </div>
              <div>
                <h4>🚀 Advanced</h4>
                <ul>
                  <li>React 18 Features</li>
                  <li>Concurrent Mode</li>
                  <li>Suspense</li>
                  <li>Server Components</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </ThemeContext.Provider>
  );
};

export default ReactMasterclass;
🎯 Итог пройденного материала:
📚 200+ ```
Примеров охватывают:
Основы React - компоненты, JSX, пропсы, состояние

Хуки - все встроенные хуки и кастомные

Управление состоянием - useState, useReducer, Context API

Работа с API - fetch, WebSocket, обработка ошибок

Оптимизация - memo, useMemo, useCallback, виртуализация

Роутинг - клиентский и серверный (Next.js)

Тестирование - Jest, React Testing Library

TypeScript - типизация компонентов и хуков

PWA - сервис-воркеры, офлайн-режим, уведомления

Доступность - ARIA, семантическая разметка

Мобильная оптимизация - адаптивный дизайн, touch события

Продвинутые паттерны - HOC, Render Props, Compound Components

🚀 Готовые проекты:
✅ Advanced Todo App с фильтрами и категориями

✅ Интерактивная галерея с touch-событиями

✅ PWA с офлайн-режимом

✅ Приложение с серверным рендерингом

✅ Компонентная библиотека с TypeScript

Теперь вы обладаете полным набором знаний для создания профессиональных React-приложений! 🎉

продолжай
Продолжаем с дополнительными продвинутыми ```
Примерами и реальными кейсами:

Часть 27: Продвинутые паттерны и архитектура
```
Пример 81: Compound Components Pattern
```jsx
import React, { createContext, useContext, useState, ReactNode } from 'react';

// Контекст для Accordion
interface AccordionContextType {
  openIndex: number | null;
  toggleItem: (index: number) => void;
}

const AccordionContext = createContext<AccordionContextType | undefined>(undefined);

// Главный компонент Accordion
interface AccordionProps {
  children: ReactNode;
  defaultOpenIndex?: number;
}

const Accordion: React.FC<AccordionProps> = ({ children, defaultOpenIndex = null }) => {
  const [openIndex, setOpenIndex] = useState<number | null>(defaultOpenIndex);

  const toggleItem = (index: number) => {
    setOpenIndex(prev => prev === index ? null : index);
  };

  return (
    <AccordionContext.Provider value={{ openIndex, toggleItem }}>
      <div style={{ 
        border: '1px solid #e1e8ed', 
        borderRadius: '8px',
        overflow: 'hidden'
      }}>
        {children}
      </div>
    </AccordionContext.Provider>
  );
};

// Хук для использования контекста
const useAccordion = () => {
  const context = useContext(AccordionContext);
  if (!context) {
    throw new Error('Accordion components must be used within Accordion');
  }
  return context;
};

// Компонент элемента Accordion
interface AccordionItemProps {
  index: number;
  children: ReactNode;
}

const AccordionItem: React.FC<AccordionItemProps> = ({ index, children }) => {
  const { openIndex } = useAccordion();
  const isOpen = openIndex === index;

  return (
    <div style={{ 
      borderBottom: '1px solid #e1e8ed',
      backgroundColor: isOpen ? '#f8f9fa' : 'white'
    }}>
      {children}
    </div>
  );
};

// Компонент заголовка Accordion
interface AccordionHeaderProps {
  index: number;
  children: ReactNode;
}

const AccordionHeader: React.FC<AccordionHeaderProps> = ({ index, children }) => {
  const { openIndex, toggleItem } = useAccordion();
  const isOpen = openIndex === index;

  return (
    <button
      onClick={() => toggleItem(index)}
      style={{
        width: '100%',
        padding: '16px 20px',
        backgroundColor: 'transparent',
        border: 'none',
        textAlign: 'left',
        cursor: 'pointer',
        display: 'flex',
        justifyContent: 'space-between',
        alignItems: 'center',
        fontSize: '16px',
        fontWeight: 'bold',
        transition: 'background-color 0.2s'
      }}
      onMouseEnter={(e) => {
        e.currentTarget.style.backgroundColor = '#f8f9fa';
      }}
      onMouseLeave={(e) => {
        e.currentTarget.style.backgroundColor = 'transparent';
      }}
    >
      <span>{children}</span>
      <span style={{ 
        transform: isOpen ? 'rotate(180deg)' : 'rotate(0deg)',
        transition: 'transform 0.3s ease'
      }}>
        ▼
      </span>
    </button>
  );
};

// Компонент содержимого Accordion
interface AccordionContentProps {
  index: number;
  children: ReactNode;
}

const AccordionContent: React.FC<AccordionContentProps> = ({ index, children }) => {
  const { openIndex } = useAccordion();
  const isOpen = openIndex === index;

  if (!isOpen) return null;

  return (
    <div style={{ 
      padding: '20px',
      backgroundColor: 'white',
      borderTop: '1px solid #e1e8ed'
    }}>
      {children}
    </div>
  );
};

// Демонстрационный компонент
const CompoundComponentsExample: React.FC = () => {
  return (
    <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
      <h2>🧩 Compound Components Pattern</h2>
      
      <Accordion defaultOpenIndex={0}>
        <AccordionItem index={0}>
          <AccordionHeader index={0}>
            📚 Что такое Compound Components?
          </AccordionHeader>
          <AccordionContent index={0}>
            <p>
              <strong>Compound Components</strong> - это паттерн, где компоненты работают вместе, 
              разделяя состояние и логику через контекст. Это позволяет создавать гибкие и 
              переиспользуемые UI компоненты.
            </p>
            <ul>
              <li>Компоненты связаны неявно через контекст</li>
              <li>Гибкая композиция компонентов</li>
              <li>Разделение ответственности</li>
              <li>Упрощенный API для пользователей</li>
            </ul>
          </AccordionContent>
        </AccordionItem>

        <AccordionItem index={1}>
          <AccordionHeader index={1}>
            🎯 Преимущества паттерна
          </AccordionHeader>
          <AccordionContent index={1}>
            <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '15px' }}>
              <div style={{ padding: '15px', backgroundColor: '#e8f5e8', borderRadius: '6px' }}>
                <h4>✅ Гибкость</h4>
                <p>Можно легко переставлять и кастомизировать компоненты</p>
              </div>
              <div style={{ padding: '15px', backgroundColor: '#e3f2fd', borderRadius: '6px' }}>
                <h4>🎨 Контроль</h4>
                <p>Полный контроль над рендерингом и поведением</p>
              </div>
              <div style={{ padding: '15px', backgroundColor: '#fff3e0', borderRadius: '6px' }}>
                <h4>🔧 Переиспользуемость</h4>
                <p>Компоненты можно использовать в разных комбинациях</p>
              </div>
              <div style={{ padding: '15px', backgroundColor: '#fce4ec', borderRadius: '6px' }}>
                <h4>📝 Читаемость</h4>
                <p>Код становится более декларативным и понятным</p>
              </div>
            </div>
          </AccordionContent>
        </AccordionItem>

        <AccordionItem index={2}>
          <AccordionHeader index={2}>
            💡 ```
Примеры использования
          </AccordionHeader>
          <AccordionContent index={2}>
            <p>Compound Components отлично подходят для:</p>
            <ul>
              <li><strong>Select/Dropdown</strong> - Select, Option, OptionGroup</li>
              <li><strong>Table</strong> - Table, Thead, Tbody, Tr, Td</li>
              <li><strong>Form</strong> - Form, Field, Label, Error</li>
              <li><strong>Navigation</strong> - Nav, NavItem, NavLink</li>
              <li><strong>Modal</strong> - Modal, Header, Body, Footer</li>
            </ul>
          </AccordionContent>
        </AccordionItem>

        <AccordionItem index={3}>
          <AccordionHeader index={3}>
            🔧 Техническая реализация
          </AccordionHeader>
          <AccordionContent index={3}>
            <pre style={{ 
              backgroundColor: '#2c3e50', 
              color: '#ecf0f1', 
              padding: '15px', 
              borderRadius: '6px',
              fontSize: '14px',
              overflow: 'auto'
            }}>
{`// 1. Создаем контекст
const AccordionContext = createContext();

// 2. Главный компонент предоставляет контекст
const Accordion = ({ children }) => {
  const [state, setState] = useState();
  return (
    <AccordionContext.Provider value={{ state, setState }}>
      {children}
    </AccordionContext.Provider>
  );
};

// 3. Дочерние компоненты используют контекст
const AccordionItem = ({ children }) => {
  const { state } = useContext(AccordionContext);
  // Рендерим с учетом состояния
};

// 4. Использование
<Accordion>
  <AccordionItem>...</AccordionItem>
  <AccordionItem>...</AccordionItem>
</Accordion>`}
            </pre>
          </AccordionContent>
        </AccordionItem>
      </Accordion>

      {/* Дополнительные ```
Примеры Compound Components */}
      <div style={{ marginTop: '40px' }}>
        <h3>🎪 Другие ```
Примеры Compound Components</h3>
        
        <div style={{ 
          display: 'grid', 
          gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', 
          gap: '20px',
          marginTop: '20px'
        }}>
          <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
            <h4>📊 Data Table</h4>
            <pre style={{ fontSize: '12px', backgroundColor: '#e9ecef', padding: '10px', borderRadius: '4px' }}>
{`<Table data={users}>
  <Table.Column accessor="name" header="Name" />
  <Table.Column accessor="email" header="Email" />
  <Table.Column accessor="role" header="Role" />
</Table>`}
            </pre>
          </div>
          
          <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
            <h4>📝 Form Builder</h4>
            <pre style={{ fontSize: '12px', backgroundColor: '#e9ecef', padding: '10px', borderRadius: '4px' }}>
{`<Form onSubmit={handleSubmit}>
  <Form.Field name="email">
    <Form.Label>Email</Form.Label>
    <Form.Input type="email" />
    <Form.Error />
  </Form.Field>
</Form>`}
            </pre>
          </div>
          
          <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
            <h4>🎨 Modal Dialog</h4>
            <pre style={{ fontSize: '12px', backgroundColor: '#e9ecef', padding: '10px', borderRadius: '4px' }}>
{`<Modal isOpen={isOpen}>
  <Modal.Header>
    <Modal.Title>Заголовок</Modal.Title>
  </Modal.Header>
  <Modal.Body>Содержимое модалки</Modal.Body>
  <Modal.Footer>
    <Button>Закрыть</Button>
  </Modal.Footer>
</Modal>`}
            </pre>
          </div>
        </div>
      </div>
    </div>
  );
};

export default CompoundComponentsExample;
```
Пример 82: Render Props Pattern
```jsx
import React, { useState, useEffect } from 'react';

// Компонент с Render Prop для загрузки данных
interface DataFetcherProps<T> {
  url: string;
  children: (props: {
    data: T | null;
    loading: boolean;
    error: string | null;
    refetch: () => void;
  }) => React.ReactNode;
}

const DataFetcher = <T,>({ url, children }: DataFetcherProps<T>): React.ReactElement => {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  const fetchData = async () => {
    setLoading(true);
    setError(null);
    
    try {
      // Имитация API запроса
      setTimeout(() => {
        const mockData = {
          users: [
            { id: 1, name: 'John Doe', email: 'john@example.com' },
            { id: 2, name: 'Jane Smith', email: 'jane@example.com' },
          ],
          posts: [
            { id: 1, title: 'Post 1', content: 'Content 1' },
            { id: 2, title: 'Post 2', content: 'Content 2' },
          ]
        } as T;
        
        setData(mockData);
        setLoading(false);
      }, 1000);
    } catch (err) {
      setError('Failed to fetch data');
      setLoading(false);
    }
  };

  useEffect(() => {
    fetchData();
  }, [url]);

  return (
    <>
      {children({ data, loading, error, refetch: fetchData })}
    </>
  );
};

// Компонент с Render Prop для управления состоянием формы
interface FormManagerProps {
  initialValues?: Record<string, any>;
  children: (props: {
    values: Record<string, any>;
    errors: Record<string, string>;
    handleChange: (name: string, value: any) => void;
    handleSubmit: (onSubmit: (values: Record<string, any>) => void) => void;
    reset: () => void;
  }) => React.ReactNode;
}

const FormManager: React.FC<FormManagerProps> = ({ 
  initialValues = {}, 
  children 
}) => {
  const [values, setValues] = useState<Record<string, any>>(initialValues);
  const [errors, setErrors] = useState<Record<string, string>>({});

  const handleChange = (name: string, value: any) => {
    setValues(prev => ({ ...prev, [name]: value }));
    
    // Очищаем ошибку при изменении поля
    if (errors[name]) {
      setErrors(prev => ({ ...prev, [name]: '' }));
    }
  };

  const validate = (): boolean => {
    const newErrors: Record<string, string> = {};
    
    if (!values.name) newErrors.name = 'Name is required';
    if (!values.email) newErrors.email = 'Email is required';
    else if (!/\S+@\S+\.\S+/.test(values.email)) {
      newErrors.email = 'Email is invalid';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = (onSubmit: (values: Record<string, any>) => void) => {
    if (validate()) {
      onSubmit(values);
    }
  };

  const reset = () => {
    setValues(initialValues);
    setErrors({});
  };

  return (
    <>
      {children({ values, errors, handleChange, handleSubmit, reset })}
    </>
  );
};

// Компонент с Render Prop для пагинации
interface PaginationProps {
  totalItems: number;
  itemsPerPage: number;
  children: (props: {
    currentPage: number;
    totalPages: number;
    startIndex: number;
    endIndex: number;
    goToPage: (page: number) => void;
    nextPage: () => void;
    prevPage: () => void;
  }) => React.ReactNode;
}

const Pagination: React.FC<PaginationProps> = ({ 
  totalItems, 
  itemsPerPage, 
  children 
}) => {
  const [currentPage, setCurrentPage] = useState(1);
  const totalPages = Math.ceil(totalItems / itemsPerPage);

  const goToPage = (page: number) => {
    if (page >= 1 && page <= totalPages) {
      setCurrentPage(page);
    }
  };

  const nextPage = () => {
    if (currentPage < totalPages) {
      setCurrentPage(prev => prev + 1);
    }
  };

  const prevPage = () => {
    if (currentPage > 1) {
      setCurrentPage(prev => prev - 1);
    }
  };

  const startIndex = (currentPage - 1) * itemsPerPage;
  const endIndex = Math.min(startIndex + itemsPerPage, totalItems);

  return (
    <>
      {children({
        currentPage,
        totalPages,
        startIndex,
        endIndex,
        goToPage,
        nextPage,
        prevPage
      })}
    </>
  );
};

// Демонстрационный компонент
const RenderPropsExample: React.FC = () => {
  const [activeTab, setActiveTab] = useState('data');

  return (
    <div style={{ maxWidth: '1000px', margin: '0 auto', padding: '20px' }}>
      <h2>🎨 Render Props Pattern</h2>
      <p style={{ color: '#666', marginBottom: '30px' }}>
        Render Props - это паттерн, где компонент принимает функцию как пропс и использует её для рендера содержимого.
      </p>

      {/* Навигация */}
      <div style={{ 
        display: 'flex', 
        gap: '10px', 
        marginBottom: '30px',
        borderBottom: '1px solid #e1e8ed'
      }}>
        <button
          onClick={() => setActiveTab('data')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeTab === 'data' ? '#3498db' : 'transparent',
            color: activeTab === 'data' ? 'white' : '#3498db',
            border: 'none',
            borderBottom: activeTab === 'data' ? '2px solid #3498db' : 'none',
            cursor: 'pointer'
          }}
        >
          📡 Data Fetching
        </button>
        <button
          onClick={() => setActiveTab('form')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeTab === 'form' ? '#3498db' : 'transparent',
            color: activeTab === 'form' ? 'white' : '#3498db',
            border: 'none',
            borderBottom: activeTab === 'form' ? '2px solid #3498db' : 'none',
            cursor: 'pointer'
          }}
        >
          📝 Form Management
        </button>
        <button
          onClick={() => setActiveTab('pagination')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeTab === 'pagination' ? '#3498db' : 'transparent',
            color: activeTab === 'pagination' ? 'white' : '#3498db',
            border: 'none',
            borderBottom: activeTab === 'pagination' ? '2px solid #3498db' : 'none',
            cursor: 'pointer'
          }}
        >
          📄 Pagination
        </button>
      </div>

      {/* Data Fetching Example */}
      {activeTab === 'data' && (
        <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
          <h3>📡 Data Fetching with Render Props</h3>
          <DataFetcher url="/api/data">
            {({ data, loading, error, refetch }) => (
              <div>
                {loading && (
                  <div style={{ textAlign: 'center', padding: '20px' }}>
                    <div style={{ fontSize: '24px', marginBottom: '10px' }}>⏳</div>
                    Loading data...
                  </div>
                )}
                
                {error && (
                  <div style={{ 
                    padding: '15px', 
                    backgroundColor: '#ffebee', 
                    border: '1px solid #f44336',
                    borderRadius: '4px',
                    marginBottom: '15px'
                  }}>
                    ❌ {error}
                    <button 
                      onClick={refetch}
                      style={{ marginLeft: '10px' }}
                    >
                      Retry
                    </button>
                  </div>
                )}
                
                {data && (
                  <div>
                    <div style={{ 
                      display: 'flex', 
                      justifyContent: 'space-between', 
                      alignItems: 'center',
                      marginBottom: '15px'
                    }}>
                      <h4>📊 Data Loaded Successfully!</h4>
                      <button onClick={refetch}>🔄 Refresh</button>
                    </div>
                    
                    <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px' }}>
                      <div style={{ padding: '15px', backgroundColor: 'white', borderRadius: '6px' }}>
                        <h5>👥 Users</h5>
                        <pre style={{ fontSize: '12px' }}>
                          {JSON.stringify((data as any).users, null, 2)}
                        </pre>
                      </div>
                      <div style={{ padding: '15px', backgroundColor: 'white', borderRadius: '6px' }}>
                        <h5>📝 Posts</h5>
                        <pre style={{ fontSize: '12px' }}>
                          {JSON.stringify((data as any).posts, null, 2)}
                        </pre>
                      </div>
                    </div>
                  </div>
                )}
              </div>
            )}
          </DataFetcher>
        </div>
      )}

      {/* Form Management Example */}
      {activeTab === 'form' && (
        <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
          <h3>📝 Form Management with Render Props</h3>
          <FormManager initialValues={{ name: '', email: '', message: '' }}>
            {({ values, errors, handleChange, handleSubmit, reset }) => (
              <form
                onSubmit={(e) => {
                  e.preventDefault();
                  handleSubmit((formValues) => {
                    alert(`Form submitted: ${JSON.stringify(formValues, null, 2)}`);
                  });
                }}
                style={{ maxWidth: '500px' }}
              >
                <div style={{ marginBottom: '15px' }}>
                  <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
                    Name:
                  </label>
                  <input
                    type="text"
                    value={values.name || ''}
                    onChange={(e) => handleChange('name', e.target.value)}
                    style={{
                      width: '100%',
                      padding: '10px',
                      border: `1px solid ${errors.name ? '#f44336' : '#ddd'}`,
                      borderRadius: '4px'
                    }}
                  />
                  {errors.name && (
                    <span style={{ color: '#f44336', fontSize: '14px' }}>{errors.name}</span>
                  )}
                </div>

                <div style={{ marginBottom: '15px' }}>
                  <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
                    Email:
                  </label>
                  <input
                    type="email"
                    value={values.email || ''}
                    onChange={(e) => handleChange('email', e.target.value)}
                    style={{
                      width: '100%',
                      padding: '10px',
                      border: `1px solid ${errors.email ? '#f44336' : '#ddd'}`,
                      borderRadius: '4px'
                    }}
                  />
                  {errors.email && (
                    <span style={{ color: '#f44336', fontSize: '14px' }}>{errors.email}</span>
                  )}
                </div>

                <div style={{ marginBottom: '20px' }}>
                  <label style={{ display: 'block', marginBottom: '5px', fontWeight: 'bold' }}>
                    Message:
                  </label>
                  <textarea
                    value={values.message || ''}
                    onChange={(e) => handleChange('message', e.target.value)}
                    rows={4}
                    style={{
                      width: '100%',
                      padding: '10px',
                      border: '1px solid #ddd',
                      borderRadius: '4px',
                      resize: 'vertical'
                    }}
                  />
                </div>

                <div style={{ display: 'flex', gap: '10px' }}>
                  <button
                    type="submit"
                    style={{
                      padding: '10px 20px',
                      backgroundColor: '#3498db',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: 'pointer'
                    }}
                  >
                    Submit
                  </button>
                  <button
                    type="button"
                    onClick={reset}
                    style={{
                      padding: '10px 20px',
                      backgroundColor: '#95a5a6',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: 'pointer'
                    }}
                  >
                    Reset
                  </button>
                </div>

                {/* Form Values Preview */}
                <div style={{ 
                  marginTop: '20px', 
                  padding: '15px', 
                  backgroundColor: '#e3f2fd',
                  borderRadius: '4px'
                }}>
                  <h5>Form Values:</h5>
                  <pre style={{ fontSize: '12px', margin: 0 }}>
                    {JSON.stringify(values, null, 2)}
                  </pre>
                </div>
              </form>
            )}
          </FormManager>
        </div>
      )}

      {/* Pagination Example */}
      {activeTab === 'pagination' && (
        <div style={{ padding: '20px', backgroundColor: '#f8f9fa', borderRadius: '8px' }}>
          <h3>📄 Pagination with Render Props</h3>
          
          <Pagination totalItems={50} itemsPerPage={5}>
            {({ 
              currentPage, 
              totalPages, 
              startIndex, 
              endIndex, 
              goToPage, 
              nextPage, 
              prevPage 
            }) => (
              <div>
                {/* Информация о странице */}
                <div style={{ 
                  padding: '15px', 
                  backgroundColor: 'white', 
                  borderRadius: '6px',
                  marginBottom: '15px'
                }}>
                  <p>
                    Showing items <strong>{startIndex + 1}-{endIndex}</strong> of <strong>50</strong><br />
                    Page <strong>{currentPage}</strong> of <strong>{totalPages}</strong>
                  </p>
                </div>

                {/* Элементы страницы */}
                <div style={{ marginBottom: '20px' }}>
                  {Array.from({ length: 5 }, (_, index) => {
                    const itemNumber = startIndex + index + 1;
                    return (
                      <div
                        key={itemNumber}
                        style={{
                          padding: '10px 15px',
                          backgroundColor: 'white',
                          border: '1px solid #e1e8ed',
                          marginBottom: '5px',
                          borderRadius: '4px'
                        }}
                      >
                        📦 Item {itemNumber}
                      </div>
                    );
                  })}
                </div>

                {/* Пагинация */}
                <div style={{ 
                  display: 'flex', 
                  justifyContent: 'space-between', 
                  alignItems: 'center'
                }}>
                  <button
                    onClick={prevPage}
                    disabled={currentPage === 1}
                    style={{
                      padding: '8px 16px',
                      backgroundColor: currentPage === 1 ? '#bdc3c7' : '#3498db',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: currentPage === 1 ? 'not-allowed' : 'pointer'
                    }}
                  >
                    ⬅️ Previous
                  </button>

                  <div style={{ display: 'flex', gap: '5px' }}>
                    {Array.from({ length: totalPages }, (_, index) => (
                      <button
                        key={index + 1}
                        onClick={() => goToPage(index + 1)}
                        style={{
                          padding: '8px 12px',
                          backgroundColor: currentPage === index + 1 ? '#3498db' : '#ecf0f1',
                          color: currentPage === index + 1 ? 'white' : '#2c3e50',
                          border: 'none',
                          borderRadius: '4px',
                          cursor: 'pointer'
                        }}
                      >
                        {index + 1}
                      </button>
                    ))}
                  </div>

                  <button
                    onClick={nextPage}
                    disabled={currentPage === totalPages}
                    style={{
                      padding: '8px 16px',
                      backgroundColor: currentPage === totalPages ? '#bdc3c7' : '#3498db',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: currentPage === totalPages ? 'not-allowed' : 'pointer'
                    }}
                  >
                    Next ➡️
                  </button>
                </div>
              </div>
            )}
          </Pagination>
        </div>
      )}

      {/* Сравнение паттернов */}
      <div style={{ 
        marginTop: '40px', 
        padding: '25px', 
        backgroundColor: '#2c3e50',
        color: 'white',
        borderRadius: '8px'
      }}>
        <h3>🎯 Render Props vs Other Patterns</h3>
        
        <div style={{ 
          display: 'grid', 
          gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', 
          gap: '20px',
          marginTop: '20px'
        }}>
          <div>
            <h4>✅ Преимущества Render Props</h4>
            <ul>
              <li><strong>Гибкость</strong> - полный контроль над рендерингом</li>
              <li><strong>Переиспользуемость</strong> - логика отделена от UI</li>
              <li><strong>Композиция</strong> - легко комбинировать несколько Render Props</li>
              <li><strong>Тестируемость</strong> - логику легко тестировать отдельно</li>
            </ul>
          </div>
          
          <div>
            <h4>❌ Недостатки Render Props</h4>
            <ul>
              <li><strong>Callback Hell</strong> - вложенные функции могут усложнить код</li>
              <li><strong>Производительность</strong> - создание функций при каждом рендере</li>
              <li><strong>Сложность</strong> - может быть сложнее для понимания новичкам</li>
            </ul>
          </div>
        </div>

        {/* Когда использовать */}
        <div style={{ marginTop: '20px', padding: '15px', backgroundColor: '#34495e', borderRadius: '6px' }}>
          <h4>🎪 Когда использовать Render Props?</h4>
          <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '15px', marginTop: '10px' }}>
            <div>
              <strong>✅ Хорошо для:</strong>
              <ul style={{ margin: '10px 0', paddingLeft: '20px' }}>
                <li>Cross-cutting concerns</li>
                <li>Поведенческих компонентов</li>
                <li>Когда нужен полный контроль над UI</li>
                <li>Сложной логики с состоянием</li>
              </ul>
            </div>
            <div>
              <strong>❌ Не для:</strong>
              <ul style={{ margin: '10px 0', paddingLeft: '20px' }}>
                <li>Простых компонентов</li>
                <li>Когда важен performance</li>
                <li>Команд с начинающими разработчиками</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default RenderPropsExample;
Часть 28: Микро-фронтенды и модульная архитектура
```
Пример 83: Module Federation и микросервисная архитектура
```jsx
import React, { useState, lazy, Suspense } from 'react';

// Имитация микро-фронтендов через lazy loading
const MicroFrontend1 = lazy(() => 
  Promise.resolve({
    default: () => (
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#e8f5e8', 
        border: '2px solid #4CAF50',
        borderRadius: '8px'
      }}>
        <h3>🧩 Micro-Frontend 1: User Management</h3>
        <p>Это независимое приложение для управления пользователями</p>
        <div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '10px' }}>
          <div style={{ padding: '10px', backgroundColor: 'white', borderRadius: '4px' }}>
            <strong>👥 Users</strong>
            <p>Total: 1,234</p>
          </div>
          <div style={{ padding: '10px', backgroundColor: 'white', borderRadius: '4px' }}>
            <strong>📊 Activity</strong>
            <p>Active: 892</p>
          </div>
        </div>
      </div>
    )
  })
);

const MicroFrontend2 = lazy(() => 
  Promise.resolve({
    default: () => (
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#e3f2fd', 
        border: '2px solid #2196F3',
        borderRadius: '8px'
      }}>
        <h3>📊 Micro-Frontend 2: Analytics Dashboard</h3>
        <p>Аналитическая панель с графиками и метриками</p>
        <div style={{ display: 'flex', gap: '15px', overflowX: 'auto' }}>
          <div style={{ 
            minWidth: '150px', 
            padding: '15px', 
            backgroundColor: 'white', 
            borderRadius: '6px',
            textAlign: 'center'
          }}>
            <div style={{ fontSize: '24px', fontWeight: 'bold', color: '#4CAF50' }}>42%</div>
            <div>Conversion</div>
          </div>
          <div style={{ 
            minWidth: '150px', 
            padding: '15px', 
            backgroundColor: 'white', 
            borderRadius: '6px',
            textAlign: 'center'
          }}>
            <div style={{ fontSize: '24px', fontWeight: 'bold', color: '#2196F3' }}>1.2k</div>
            <div>Visitors</div>
          </div>
          <div style={{ 
            minWidth: '150px', 
            padding: '15px', 
            backgroundColor: 'white', 
            borderRadius: '6px',
            textAlign: 'center'
          }}>
            <div style={{ fontSize: '24px', fontWeight: 'bold', color: '#FF9800' }}>$5.6k</div>
            <div>Revenue</div>
          </div>
        </div>
      </div>
    )
  })
);

const MicroFrontend3 = lazy(() => 
  Promise.resolve({
    default: () => (
      <div style={{ 
        padding: '20px', 
        backgroundColor: '#fff3e0', 
        border: '2px solid #FF9800',
        borderRadius: '8px'
      }}>
        <h3>🛒 Micro-Frontend 3: E-commerce</h3>
        <p>Интернет-магазин с корзиной и товарами</p>
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(auto-fit, minmax(120px, 1fr))', gap: '10px' }}>
          {['📱 Phone', '💻 Laptop', '🎧 Headphones', '⌚ Watch'].map((product, index) => (
            <div
              key={index}
              style={{
                padding: '10px',
                backgroundColor: 'white',
                border: '1px solid #ddd',
                borderRadius: '4px',
                textAlign: 'center'
              }}
            >
              {product}
              <br />
              <button style={{ 
                marginTop: '5px', 
                padding: '5px 10px', 
                fontSize: '12px',
                backgroundColor: '#4CAF50',
                color: 'white',
                border: 'none',
                borderRadius: '3px',
                cursor: 'pointer'
              }}>
                Add to Cart
              </button>
            </div>
          ))}
        </div>
      </div>
    )
  })
);

// Компонент Shell Application
const MicroFrontendShell: React.FC = () => {
  const [activeMF, setActiveMF] = useState<string>('all');
  const [loadedMFs, setLoadedMFs] = useState<Set<string>>(new Set());

  const handleMFLoad = (mfName: string) => {
    setLoadedMFs(prev => new Set(prev).add(mfName));
  };

  const renderMicroFrontend = (mf: string, component: React.ReactNode) => (
    <Suspense fallback={
      <div style={{ 
        padding: '40px', 
        textAlign: 'center', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px',
        border: '2px dashed #ddd'
      }}>
        <div style={{ fontSize: '24px', marginBottom: '10px' }}>⏳</div>
        Loading {mf}...
      </div>
    }>
      {React.cloneElement(component as React.ReactElement, { 
        onLoad: () => handleMFLoad(mf)
      })}
    </Suspense>
  );

  return (
    <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '20px' }}>
      <header style={{ 
        padding: '20px', 
        backgroundColor: '#2c3e50', 
        color: 'white',
        borderRadius: '8px',
        marginBottom: '20px',
        textAlign: 'center'
      }}>
        <h1>🏗️ Micro-Frontend Architecture</h1>
        <p>Shell Application - объединяет независимые микро-фронтенды</p>
      </header>

      {/* Навигация */}
      <nav style={{ 
        display: 'flex', 
        gap: '10px', 
        marginBottom: '20px',
        flexWrap: 'wrap'
      }}>
        <button
          onClick={() => setActiveMF('all')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeMF === 'all' ? '#3498db' : '#ecf0f1',
            color: activeMF === 'all' ? 'white' : '#2c3e50',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          🏠 All Micro-Frontends
        </button>
        <button
          onClick={() => setActiveMF('mf1')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeMF === 'mf1' ? '#4CAF50' : '#ecf0f1',
            color: activeMF === 'mf1' ? 'white' : '#2c3e50',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          👥 User Management
        </button>
        <button
          onClick={() => setActiveMF('mf2')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeMF === 'mf2' ? '#2196F3' : '#ecf0f1',
            color: activeMF === 'mf2' ? 'white' : '#2c3e50',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          📊 Analytics
        </button>
        <button
          onClick={() => setActiveMF('mf3')}
          style={{
            padding: '10px 20px',
            backgroundColor: activeMF === 'mf3' ? '#FF9800' : '#ecf0f1',
            color: activeMF === 'mf3' ? 'white' : '#2c3e50',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          🛒 E-commerce
        </button>
      </nav>

      {/* Статус загрузки */}
      <div style={{ 
        padding: '15px', 
        backgroundColor: '#f8f9fa', 
        borderRadius: '6px',
        marginBottom: '20px',
        display: 'flex',
        justifyContent: 'space-between',
        alignItems: 'center'
      }}>
        <div>
          <strong>📦 Loaded Micro-Frontends:</strong>{' '}
          {loadedMFs.size > 0 ? Array.from(loadedMFs).join(', ') : 'None'}
        </div>
        <div style={{ fontSize: '14px', color: '#666' }}>
          Total: {loadedMFs.size}/3
        </div>
      </div>

      {/* Контент */}
      <main>
        {(activeMF === 'all' || activeMF === 'mf1') && (
          <div style={{ marginBottom: '20px' }}>
            {renderMicroFrontend('User Management', <MicroFrontend1 />)}
          </div>
        )}
        
        {(activeMF === 'all' || activeMF === 'mf2') && (
          <div style={{ marginBottom: '20px' }}>
            {renderMicroFrontend('Analytics', <MicroFrontend2 />)}
          </div>
        )}
        
        {(activeMF === 'all' || activeMF === 'mf3') && (
          <div style={{ marginBottom: '20px' }}>
            {renderMicroFrontend('E-commerce', <MicroFrontend3 />)}
          </div>
        )}
      </main>

      {/* Архитектурная информация */}
      <div style={{ 
        marginTop: '40px', 
        padding: '25px', 
        backgroundColor: '#f5f5f5',
        borderRadius: '8px'
      }}>
        <h2>🏗️ Архитектура Micro-Frontends</h2>
        
        <div style={{ 
          display: 'grid', 
          gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))', 
          gap: '20px',
          marginTop: '20px'
        }}>
          <div style={{ padding: '20px', backgroundColor: 'white', borderRadius: '6px' }}>
            <h3>🎯 Преимущества</h3>
            <ul>
              <li><strong>Независимые команды</strong> - каждая команда работает над своим микро-фронтендом</li>
              <li><strong>Технологическая свобода</strong> - разные технологии в разных микро-фронтендах</li>
              <li><strong>Постепенное обновление</strong> - можно обновлять части приложения независимо</li>
              <li><strong>Изоляция ошибок</strong> - ошибка в одном MF не ломает всё приложение</li>
            </ul>
          </div>
          
          <div style={{ padding: '20px', backgroundColor: 'white', borderRadius: '6px' }}>
            <h3>🔧 Техническая реализация</h3>
            <ul>
              <li><strong>Module Federation</strong> - Webpack 5 для загрузки микро-фронтендов</li>
              <li><strong>Single-SPA</strong> - фреймворк для микро-фронтендов</li>
              <li><strong>Iframe</strong> - простой способ изоляции</li>
              <li><strong>Web Components</strong> - нативная браузерная технология</li>
            </ul>
          </div>
        </div>

        {/* Схема архитектуры */}
        <div style={{ 
          marginTop: '30px', 
          padding: '20px', 
          backgroundColor: '#2c3e50',
          color: 'white',
          borderRadius: '6px'
        }}>
          <h3>📐 Архитектурная схема</h3>
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', 
            gap: '15px',
            marginTop: '15px',
            textAlign: 'center'
          }}>
            <div style={{ padding: '15px', backgroundColor: '#34495e', borderRadius: '4px' }}>
              <div style={{ fontSize: '24px' }}>🏠</div>
              <div>Shell App</div>
              <div style={{ fontSize: '12px', color: '#bdc3c7' }}>Router & Layout</div>
            </div>
            <div style={{ padding: '15px', backgroundColor: '#34495e', borderRadius: '4px' }}>
              <div style={{ fontSize: '24px' }}>👥</div>
              <div>MF 1</div>
              <div style={{ fontSize: '12px', color: '#bdc3c7' }}>User Management</div>
            </div>
            <div style={{ padding: '15px', backgroundColor: '#34495e', borderRadius: '4px' }}>
              <div style={{ fontSize: '24px' }}>📊</div>
              <div>MF 2</div>
              <div style={{ fontSize: '12px', color: '#bdc3c7' }}>Analytics</div>
            </div>
            <div style={{ padding: '15px', backgroundColor: '#34495e', borderRadius: '4px' }}>
              <div style={{ fontSize: '24px' }}>🛒</div>
              <div>MF 3</div>
              <div style={{ fontSize: '12px', color: '#bdc3c7' }}>E-commerce</div>
            </div>
          </div>
        </div>

        {/* Реализация с Module Federation */}
        <div style={{ 
          marginTop: '30px', 
          padding: '20px', 
          backgroundColor: '#e8f5e8',
          borderRadius: '6px'
        }}>
          <h3>⚡ Module Federation Configuration</h3>
          
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: '1fr 1fr', 
            gap: '20px',
            marginTop: '15px'
          }}>
            <div>
              <h4>Shell Application (Host)</h4>
              <pre style={{ 
                backgroundColor: '#2c3e50', 
                color: '#ecf0f1', 
                padding: '15px', 
                borderRadius: '4px',
                fontSize: '12px',
                overflow: 'auto'
              }}>
{`// webpack.config.js
module.exports = {
  // ... other config
  plugins: [
    new ModuleFederationPlugin({
      name: 'shell',
      remotes: {
        mf1: 'mf1@http://localhost:3001/remoteEntry.js',
        mf2: 'mf2@http://localhost:3002/remoteEntry.js',
        mf3: 'mf3@http://localhost:3003/remoteEntry.js'
      }
    })
  ]
};`}
              </pre>
            </div>
            
            <div>
              <h4>Micro-Frontend (Remote)</h4>
              <pre style={{ 
                backgroundColor: '#2c3e50', 
                color: '#ecf0f1', 
                padding: '15px', 
                borderRadius: '4px',
                fontSize: '12px',
                overflow: 'auto'
              }}>
{`// webpack.config.js
module.exports = {
  // ... other config
  plugins: [
    new ModuleFederationPlugin({
      name: 'mf1',
      filename: 'remoteEntry.js',
      exposes: {
        './UserApp': './src/UserApp'
      },
      shared: {
        react: { singleton: true },
        'react-dom': { singleton: true }
      }
    })
  ]
};`}
              </pre>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default MicroFrontendShell;
```
Пример 84: State Management с Zustand и паттернами
```jsx
import React, { useEffect } from 'react';
import { create } from 'zustand';
import { persist } from 'zustand/middleware';

// Типы для нашего store
interface User {
  id: string;
  name: string;
  email: string;
  avatar: string;
}

interface Todo {
  id: string;
  text: string;
  completed: boolean;
  createdAt: Date;
}

interface AppState {
  // State
  user: User | null;
  todos: Todo[];
  theme: 'light' | 'dark';
  loading: boolean;
  
  // Actions
  setUser: (user: User | null) => void;
  addTodo: (text: string) => void;
  toggleTodo: (id: string) => void;
  deleteTodo: (id: string) => void;
  setTheme: (theme: 'light' | 'dark') => void;
  setLoading: (loading: boolean) => void;
  
  // Derived state
  completedTodos: number;
  pendingTodos: number;
}

// Создаем store с Zustand
const useAppStore = create<AppState>()(
  persist(
    (set, get) => ({
      // Initial state
      user: null,
      todos: [],
      theme: 'light',
      loading: false,
      
      // Actions
      setUser: (user) => set({ user }),
      
      addTodo: (text) => set((state) => ({
        todos: [
          ...state.todos,
          {
            id: Math.random().toString(36).substr(2, 9),
            text,
            completed: false,
            createdAt: new Date()
          }
        ]
      })),
      
      toggleTodo: (id) => set((state) => ({
        todos: state.todos.map(todo =>
          todo.id === id ? { ...todo, completed: !todo.completed } : todo
        )
      })),
      
      deleteTodo: (id) => set((state) => ({
        todos: state.todos.filter(todo => todo.id !== id)
      })),
      
      setTheme: (theme) => set({ theme }),
      
      setLoading: (loading) => set({ loading }),
      
      // Derived state (computed)
      get completedTodos() {
        return get().todos.filter(todo => todo.completed).length;
      },
      
      get pendingTodos() {
        return get().todos.filter(todo => !todo.completed).length;
      }
    }),
    {
      name: 'app-storage', // localStorage key
      partialize: (state) => ({ 
        todos: state.todos,
        theme: state.theme,
        user: state.user
      }) // Какие поля сохранять
    }
  )
);

// Компонент пользователя
const UserProfile: React.FC = () => {
  const { user, setUser } = useAppStore();
  
  const login = () => {
    setUser({
      id: '1',
      name: 'John Doe',
      email: 'john@example.com',
      avatar: '👤'
    });
  };
  
  const logout = () => {
    setUser(null);
  };
  
  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: 'var(--card-bg)',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>👤 User Profile</h3>
      
      {user ? (
        <div style={{ display: 'flex', alignItems: 'center', gap: '15px' }}>
          <div style={{ fontSize: '40px' }}>{user.avatar}</div>
          <div>
            <h4 style={{ margin: '0 0 5px 0' }}>{user.name}</h4>
            <p style={{ margin: 0, color: 'var(--text-secondary)' }}>{user.email}</p>
          </div>
          <button onClick={logout} style={{ marginLeft: 'auto' }}>
            Logout
          </button>
        </div>
      ) : (
        <div style={{ textAlign: 'center' }}>
          <p>Not logged in</p>
          <button onClick={login}>
            Login as John Doe
          </button>
        </div>
      )}
    </div>
  );
};

// Компонент управления задачами
const TodoManager: React.FC = () => {
  const { todos, addTodo, toggleTodo, deleteTodo, completedTodos, pendingTodos } = useAppStore();
  const [newTodo, setNewTodo] = React.useState('');
  
  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    if (newTodo.trim()) {
      addTodo(newTodo.trim());
      setNewTodo('');
    }
  };
  
  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: 'var(--card-bg)',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>✅ Todo Manager</h3>
      
      {/* Статистика */}
      <div style={{ 
        display: 'grid', 
        gridTemplateColumns: 'repeat(3, 1fr)', 
        gap: '10px',
        marginBottom: '20px'
      }}>
        <div style={{ 
          padding: '15px', 
          backgroundColor: 'var(--bg-secondary)',
          borderRadius: '6px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '24px', fontWeight: 'bold' }}>{todos.length}</div>
          <div>Total</div>
        </div>
        <div style={{ 
          padding: '15px', 
          backgroundColor: 'var(--bg-secondary)',
          borderRadius: '6px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '24px', fontWeight: 'bold', color: '#4CAF50' }}>
            {completedTodos}
          </div>
          <div>Completed</div>
        </div>
        <div style={{ 
          padding: '15px', 
          backgroundColor: 'var(--bg-secondary)',
          borderRadius: '6px',
          textAlign: 'center'
        }}>
          <div style={{ fontSize: '24px', fontWeight: 'bold', color: '#FF9800' }}>
            {pendingTodos}
          </div>
          <div>Pending</div>
        </div>
      </div>
      
      {/* Форма добавления */}
      <form onSubmit={handleSubmit} style={{ marginBottom: '20px' }}>
        <div style={{ display: 'flex', gap: '10px' }}>
          <input
            type="text"
            value={newTodo}
            onChange={(e) => setNewTodo(e.target.value)}
            placeholder="Add a new todo..."
            style={{
              flex: 1,
              padding: '10px',
              border: '1px solid var(--border)',
              borderRadius: '4px',
              backgroundColor: 'var(--bg)',
              color: 'var(--text)'
            }}
          />
          <button type="submit">Add</button>
        </div>
      </form>
      
      {/* Список задач */}
      <div style={{ maxHeight: '300px', overflowY: 'auto' }}>
        {todos.length === 0 ? (
          <div style={{ 
            textAlign: 'center', 
            padding: '20px', 
            color: 'var(--text-secondary)'
          }}>
            No todos yet. Add your first task!
          </div>
        ) : (
          todos.map(todo => (
            <div
              key={todo.id}
              style={{
                display: 'flex',
                alignItems: 'center',
                gap: '10px',
                padding: '10px',
                marginBottom: '8px',
                backgroundColor: 'var(--bg-secondary)',
                borderRadius: '4px',
                textDecoration: todo.completed ? 'line-through' : 'none',
                opacity: todo.completed ? 0.7 : 1
              }}
            >
              <input
                type="checkbox"
                checked={todo.completed}
                onChange={() => toggleTodo(todo.id)}
                style={{ marginRight: '10px' }}
              />
              <span style={{ flex: 1 }}>{todo.text}</span>
              <small style={{ color: 'var(--text-secondary)' }}>
                {todo.createdAt.toLocaleTimeString()}
              </small>
              <button
                onClick={() => deleteTodo(todo.id)}
                style={{
                  padding: '5px 10px',
                  backgroundColor: '#f44336',
                  color: 'white',
                  border: 'none',
                  borderRadius: '3px',
                  cursor: 'pointer',
                  fontSize: '12px'
                }}
              >
                Delete
              </button>
            </div>
          ))
        )}
      </div>
    </div>
  );
};

// Компонент темы
const ThemeSwitcher: React.FC = () => {
  const { theme, setTheme } = useAppStore();
  
  return (
    <div style={{ 
      padding: '20px', 
      backgroundColor: 'var(--card-bg)',
      borderRadius: '8px',
      marginBottom: '20px'
    }}>
      <h3>🎨 Theme Switcher</h3>
      
      <div style={{ display: 'flex', gap: '10px', alignItems: 'center' }}>
        <button
          onClick={() => setTheme('light')}
          style={{
            padding: '10px 20px',
            backgroundColor: theme === 'light' ? '#3498db' : 'transparent',
            color: theme === 'light' ? 'white' : 'var(--text)',
            border: `1px solid ${theme === 'light' ? '#3498db' : 'var(--border)'}`,
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          ☀️ Light
        </button>
        <button
          onClick={() => setTheme('dark')}
          style={{
            padding: '10px 20px',
            backgroundColor: theme === 'dark' ? '#3498db' : 'transparent',
            color: theme === 'dark' ? 'white' : 'var(--text)',
            border: `1px solid ${theme === 'dark' ? '#3498db' : 'var(--border)'}`,
            borderRadius: '6px',
            cursor: 'pointer'
          }}
        >
          🌙 Dark
        </button>
        
        <span style={{ marginLeft: 'auto', color: 'var(--text-secondary)' }}>
          Current: {theme} mode
        </span>
      </div>
    </div>
  );
};

// Главный компонент
const ZustandStateManagement: React.FC = () => {
  const { theme, loading, setLoading } = useAppStore();
  
  // Эффект для симуляции загрузки
  useEffect(() => {
    setLoading(true);
    const timer = setTimeout(() => setLoading(false), 1000);
    return () => clearTimeout(timer);
  }, [setLoading]);
  
  // CSS переменные для темы
  const themeStyles = {
    light: {
      '--bg': '#ffffff',
      '--bg-secondary': '#f8f9fa',
      '--text': '#212529',
      '--text-secondary': '#6c757d',
      '--border': '#dee2e6',
      '--card-bg': '#ffffff'
    },
    dark: {
      '--bg': '#121212',
      '--bg-secondary': '#1e1e1e',
      '--text': '#ffffff',
      '--text-secondary': '#b0b0b0',
      '--border': '#333333',
      '--card-bg': '#1e1e1e'
    }
  };
  
  const currentTheme = themeStyles[theme];
  
  if (loading) {
    return (
      <div style={{ 
        display: 'flex', 
        justifyContent: 'center', 
        alignItems: 'center',
        height: '100vh',
        backgroundColor: currentTheme['--bg'],
        color: currentTheme['--text']
      }}>
        <div style={{ textAlign: 'center' }}>
          <div style={{ fontSize: '48px', marginBottom: '20px' }}>⏳</div>
          <h2>Loading Application...</h2>
        </div>
      </div>
    );
  }
  
  return (
    <div style={{
      minHeight: '100vh',
      backgroundColor: 'var(--bg)',
      color: 'var(--text)',
      transition: 'all 0.3s ease',
      ...currentTheme
    } as React.CSSProperties}>
      <div style={{ maxWidth: '800px', margin: '0 auto', padding: '20px' }}>
        <header style={{ 
          textAlign: 'center', 
          marginBottom: '30px',
          padding: '30px',
          backgroundColor: 'var(--card-bg)',
          borderRadius: '12px',
          border: '1px solid var(--border)'
        }}>
          <h1 style={{ 
            marginBottom: '10px',
            background: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
            WebkitBackgroundClip: 'text',
            WebkitTextFillColor: 'transparent'
          }}>
            ⚡ Zustand State Management
          </h1>
          <p style={{ color: 'var(--text-secondary)', margin: 0 }}>
            Modern state management with Zustand and TypeScript
          </p>
        </header>
        
        <UserProfile />
        <ThemeSwitcher />
        <TodoManager />
        
        {/* Информация о Zustand */}
        <div style={{ 
          marginTop: '40px', 
          padding: '25px', 
          backgroundColor: 'var(--card-bg)',
          borderRadius: '8px',
          border: '1px solid var(--border)'
        }}>
          <h2>🎯 Why Zustand?</h2>
          
          <div style={{ 
            display: 'grid', 
            gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))', 
            gap: '20px',
            marginTop: '20px'
          }}>
            <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
              <h4>🐻 Простота</h4>
              <p>Минимальный API, нет boilerplate кода</p>
            </div>
            <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
              <h4>🎯 TypeScript</h4>
              <p>Превосходная поддержка TypeScript из коробки</p>
            </div>
            <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
              <h4>⚡ Производительность</h4>
              <p>Оптимизирован для производительности</p>
            </div>
            <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
              <h4>🔧 Middleware</h4>
              <p>Поддержка middleware (persist, devtools, etc.)</p>
            </div>
          </div>
          
          {/* Сравнение с другими решениями */}
          <div style={{ marginTop: '30px' }}>
            <h3>📊 Сравнение State Management решений</h3>
            <div style={{ 
              display: 'grid', 
              gridTemplateColumns: 'repeat(auto-fit, minmax(200px, 1fr))', 
              gap: '15px',
              marginTop: '15px'
            }}>
              <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
                <h4>Redux Toolkit</h4>
                <ul style={{ fontSize: '14px', margin: 0 }}>
                  <li>✅ Enterprise-ready</li>
                  <li>✅ DevTools</li>
                  <li>❌ Boilerplate</li>
                  <li>❌ Complexity</li>
                </ul>
              </div>
              <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
                <h4>Zustand</h4>
                <ul style={{ fontSize: '14px', margin: 0 }}>
                  <li>✅ Simple API</li>
                  <li>✅ TypeScript</li>
                  <li>✅ Performance</li>
                  <li>✅ Small bundle</li>
                </ul>
              </div>
              <div style={{ padding: '15px', backgroundColor: 'var(--bg-secondary)', borderRadius: '6px' }}>
                <h4>Context API</h4>
                <ul style={{ fontSize: '14px', margin: 0 }}>
                  <li>✅ Built-in</li>
                  <li>✅ Simple</li>
                  <li>❌ Performance</li>
                  <li>❌ Boilerplate</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default ZustandStateManagement;
Продолжаем с реальными production-кейсами и оптимизациями! Хотите, чтобы я продолжил с ```
Примерами реальных приложений и advanced техниками?

продолжай
Продолжаем с реальными production-кейсами и advanced техниками!

Часть 29: Real-World Production приложения
```
Пример 85: E-commerce приложение с корзиной и избранным
```jsx
import React, { useState, useReducer, useCallback, useMemo, useEffect } from 'react';

// Типы
interface Product {
  id: string;
  name: string;
  price: number;
  image: string;
  description: string;
  category: string;
  rating: number;
  inStock: boolean;
}

interface CartItem {
  product: Product;
  quantity: number;
}

interface User {
  id: string;
  name: string;
  email: string;
}

interface AppState {
  user: User | null;
  cart: CartItem[];
  favorites: string[]; // product IDs
  products: Product[];
  filters: {
    category: string;
    priceRange: [number, number];
    inStock: boolean;
    sortBy: 'name' | 'price' | 'rating';
  };
  searchQuery: string;
}

type AppAction =
  | { type: 'SET_USER'; payload: User | null }
  | { type: 'ADD_TO_CART'; payload: Product }
  | { type: 'REMOVE_FROM_CART'; payload: string }
  | { type: 'UPDATE_QUANTITY'; payload: { productId: string; quantity: number } }
  | { type: 'TOGGLE_FAVORITE'; payload: string }
  | { type: 'SET_FILTERS'; payload: Partial<AppState['filters']> }
  | { type: 'SET_SEARCH_QUERY'; payload: string }
  | { type: 'CLEAR_CART' };

// Моковые данные
const mockProducts: Product[] = [
  {
    id: '1',
    name: 'iPhone 15 Pro',
    price: 999,
    image: '📱',
    description: 'Latest iPhone with advanced camera system',
    category: 'Electronics',
    rating: 4.8,
    inStock: true
  },
  {
    id: '2',
    name: 'MacBook Air',
    price: 1299,
    image: '💻',
    description: 'Lightweight laptop with M2 chip',
    category: 'Electronics',
    rating: 4.7,
    inStock: true
  },
  {
    id: '3',
    name: 'AirPods Pro',
    price: 249,
    image: '🎧',
    description: 'Wireless earbuds with noise cancellation',
    category: 'Electronics',
    rating: 4.6,
    inStock: false
  },
  {
    id: '4',
    name: 'Nike Air Max',
    price: 120,
    image: '👟',
    description: 'Comfortable running shoes',
    category: 'Fashion',
    rating: 4.4,
    inStock: true
  },
  {
    id: '5',
    name: 'Coffee Maker',
    price: 89,
    image: '☕',
    description: 'Automatic coffee machine',
    category: 'Home',
    rating: 4.3,
    inStock: true
  },
  {
    id: '6',
    name: 'Book: React Guide',
    price: 35,
    image: '📚',
    description: 'Complete guide to React development',
    category: 'Books',
    rating: 4.9,
    inStock: true
  }
];

// Редуктор
const appReducer = (state: AppState, action: AppAction): AppState => {
  switch (action.type) {
    case 'SET_USER':
      return { ...state, user: action.payload };

    case 'ADD_TO_CART':
      const existingItem = state.cart.find(item => item.product.id === action.payload.id);
      if (existingItem) {
        return {
          ...state,
          cart: state.cart.map(item =>
            item.product.id === action.payload.id
              ? { ...item, quantity: item.quantity + 1 }
              : item
          )
        };
      }
      return {
        ...state,
        cart: [...state.cart, { product: action.payload, quantity: 1 }]
      };

    case 'REMOVE_FROM_CART':
      return {
        ...state,
        cart: state.cart.filter(item => item.product.id !== action.payload)
      };

    case 'UPDATE_QUANTITY':
      return {
        ...state,
        cart: state.cart.map(item =>
          item.product.id === action.payload.productId
            ? { ...item, quantity: action.payload.quantity }
            : item
        ).filter(item => item.quantity > 0)
      };

    case 'TOGGLE_FAVORITE':
      return {
        ...state,
        favorites: state.favorites.includes(action.payload)
          ? state.favorites.filter(id => id !== action.payload)
          : [...state.favorites, action.payload]
      };

    case 'SET_FILTERS':
      return {
        ...state,
        filters: { ...state.filters, ...action.payload }
      };

    case 'SET_SEARCH_QUERY':
      return {
        ...state,
        searchQuery: action.payload
      };

    case 'CLEAR_CART':
      return {
        ...state,
        cart: []
      };

    default:
      return state;
  }
};

// Хук для использования store
const useAppStore = () => {
  const [state, dispatch] = useReducer(appReducer, {
    user: null,
    cart: [],
    favorites: [],
    products: mockProducts,
    filters: {
      category: 'all',
      priceRange: [0, 2000],
      inStock: false,
      sortBy: 'name'
    },
    searchQuery: ''
  });

  // Сохранение в localStorage
  useEffect(() => {
    localStorage.setItem('ecommerce-cart', JSON.stringify(state.cart));
    localStorage.setItem('ecommerce-favorites', JSON.stringify(state.favorites));
  }, [state.cart, state.favorites]);

  // Загрузка из localStorage
  useEffect(() => {
    const savedCart = localStorage.getItem('ecommerce-cart');
    const savedFavorites = localStorage.getItem('ecommerce-favorites');
    
    if (savedCart) {
      try {
        const cartData = JSON.parse(savedCart);
        // В реальном приложении нужно валидировать данные
        dispatch({ type: 'CLEAR_CART' });
        cartData.forEach((item: CartItem) => {
          for (let i = 0; i < item.quantity; i++) {
            dispatch({ type: 'ADD_TO_CART', payload: item.product });
          }
        });
      } catch (error) {
        console.error('Error loading cart:', error);
      }
    }

    if (savedFavorites) {
      try {
        const favoritesData = JSON.parse(savedFavorites);
        favoritesData.forEach((productId: string) => {
          dispatch({ type: 'TOGGLE_FAVORITE', payload: productId });
        });
      } catch (error) {
        console.error('Error loading favorites:', error);
      }
    }
  }, []);

  const actions = {
    setUser: useCallback((user: User | null) => 
      dispatch({ type: 'SET_USER', payload: user }), []),
    
    addToCart: useCallback((product: Product) => 
      dispatch({ type: 'ADD_TO_CART', payload: product }), []),
    
    removeFromCart: useCallback((productId: string) => 
      dispatch({ type: 'REMOVE_FROM_CART', payload: productId }), []),
    
    updateQuantity: useCallback((productId: string, quantity: number) => 
      dispatch({ type: 'UPDATE_QUANTITY', payload: { productId, quantity } }), []),
    
    toggleFavorite: useCallback((productId: string) => 
      dispatch({ type: 'TOGGLE_FAVORITE', payload: productId }), []),
    
    setFilters: useCallback((filters: Partial<AppState['filters']>) => 
      dispatch({ type: 'SET_FILTERS', payload: filters }), []),
    
    setSearchQuery: useCallback((query: string) => 
      dispatch({ type: 'SET_SEARCH_QUERY', payload: query }), []),
    
    clearCart: useCallback(() => 
      dispatch({ type: 'CLEAR_CART' }), [])
  };

  // Вычисляемые значения
  const cartTotal = useMemo(() => 
    state.cart.reduce((total, item) => total + (item.product.price * item.quantity), 0),
    [state.cart]
  );

  const cartItemsCount = useMemo(() => 
    state.cart.reduce((count, item) => count + item.quantity, 0),
    [state.cart]
  );

  const filteredProducts = useMemo(() => {
    let filtered = state.products.filter(product => {
      const matchesSearch = product.name.toLowerCase().includes(state.searchQuery.toLowerCase()) ||
                           product.description.toLowerCase().includes(state.searchQuery.toLowerCase());
      
      const matchesCategory = state.filters.category === 'all' || 
                             product.category === state.filters.category;
      
      const matchesPrice = product.price >= state.filters.priceRange[0] && 
                          product.price <= state.filters.priceRange[1];
      
      const matchesStock = !state.filters.inStock || product.inStock;
      
      return matchesSearch && matchesCategory && matchesPrice && matchesStock;
    });

    // Сортировка
    filtered.sort((a, b) => {
      switch (state.filters.sortBy) {
        case 'price':
          return a.price - b.price;
        case 'rating':
          return b.rating - a.rating;
        case 'name':
        default:
          return a.name.localeCompare(b.name);
      }
    });

    return filtered;
  }, [state.products, state.searchQuery, state.filters]);

  return {
    state,
    actions,
    computed: {
      cartTotal,
      cartItemsCount,
      filteredProducts
    }
  };
};

// Компонент Header
const Header: React.FC = () => {
  const { state, actions, computed } = useAppStore();
  const [isSearchOpen, setIsSearchOpen] = useState(false);

  return (
    <header style={{
      backgroundColor: '#2c3e50',
      color: 'white',
      padding: '1rem 2rem',
      position: 'sticky',
      top: 0,
      zIndex: 1000,
      boxShadow: '0 2px 10px rgba(0,0,0,0.1)'
    }}>
      <div style={{
        display: 'flex',
        justifyContent: 'space-between',
        alignItems: 'center',
        maxWidth: '1200px',
        margin: '0 auto'
      }}>
        {/* Logo */}
        <div style={{ display: 'flex', alignItems: 'center', gap: '1rem' }}>
          <h1 style={{ margin: 0, fontSize: '1.5rem' }}>🛍️ E-Shop</h1>
        </div>

        {/* Search */}
        <div style={{ flex: 1, maxWidth: '400px', margin: '0 2rem', position: 'relative' }}>
          <input
            type="text"
            placeholder="Search products..."
            value={state.searchQuery}
            onChange={(e) => actions.setSearchQuery(e.target.value)}
            onFocus={() => setIsSearchOpen(true)}
            onBlur={() => setTimeout(() => setIsSearchOpen(false), 200)}
            style={{
              width: '100%',
              padding: '0.5rem 1rem',
              borderRadius: '25px',
              border: 'none',
              outline: 'none',
              fontSize: '1rem'
            }}
          />
        </div>

        {/* Navigation */}
        <nav style={{ display: 'flex', alignItems: 'center', gap: '1.5rem' }}>
          <div style={{ position: 'relative' }}>
            <button style={{
              background: 'none',
              border: 'none',
              color: 'white',
              fontSize: '1.2rem',
              cursor: 'pointer',
              position: 'relative'
            }}>
              ❤️
              {state.favorites.length > 0 && (
                <span style={{
                  position: 'absolute',
                  top: '-8px',
                  right: '-8px',
                  backgroundColor: '#e74c3c',
                  color: 'white',
                  borderRadius: '50%',
                  width: '20px',
                  height: '20px',
                  fontSize: '0.8rem',
                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'center'
                }}>
                  {state.favorites.length}
                </span>
              )}
            </button>
          </div>

          <div style={{ position: 'relative' }}>
            <button style={{
              background: 'none',
              border: 'none',
              color: 'white',
              fontSize: '1.2rem',
              cursor: 'pointer',
              position: 'relative'
            }}>
              🛒
              {computed.cartItemsCount > 0 && (
                <span style={{
                  position: 'absolute',
                  top: '-8px',
                  right: '-8px',
                  backgroundColor: '#3498db',
                  color: 'white',
                  borderRadius: '50%',
                  width: '20px',
                  height: '20px',
                  fontSize: '0.8rem',
                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'center'
                }}>
                  {computed.cartItemsCount}
                </span>
              )}
            </button>
          </div>

          {state.user ? (
            <div style={{ display: 'flex', alignItems: 'center', gap: '0.5rem' }}>
              <span>👤 {state.user.name}</span>
              <button 
                onClick={() => actions.setUser(null)}
                style={{
                  padding: '0.5rem 1rem',
                  backgroundColor: '#e74c3c',
                  color: 'white',
                  border: 'none',
                  borderRadius: '4px',
                  cursor: 'pointer'
                }}
              >
                Logout
              </button>
            </div>
          ) : (
            <button 
              onClick={() => actions.setUser({ id: '1', name: 'John Doe', email: 'john@example.com' })}
              style={{
                padding: '0.5rem 1rem',
                backgroundColor: '#3498db',
                color: 'white',
                border: 'none',
                borderRadius: '4px',
                cursor: 'pointer'
              }}
            >
              Login
            </button>
          )}
        </nav>
      </div>
    </header>
  );
};

// Компонент Product Card
interface ProductCardProps {
  product: Product;
}

const ProductCard: React.FC<ProductCardProps> = ({ product }) => {
  const { state, actions } = useAppStore();
  
  const isFavorite = state.favorites.includes(product.id);
  const cartItem = state.cart.find(item => item.product.id === product.id);

  return (
    <div style={{
      backgroundColor: 'white',
      borderRadius: '12px',
      padding: '1.5rem',
      boxShadow: '0 4px 6px rgba(0,0,0,0.1)',
      transition: 'transform 0.2s, box-shadow 0.2s',
      border: `2px solid ${!product.inStock ? '#ffebee' : 'transparent'}`,
      opacity: !product.inStock ? 0.7 : 1
    }}
    onMouseEnter={(e) => {
      e.currentTarget.style.transform = 'translateY(-4px)';
      e.currentTarget.style.boxShadow = '0 8px 15px rgba(0,0,0,0.15)';
    }}
    onMouseLeave={(e) => {
      e.currentTarget.style.transform = 'translateY(0)';
      e.currentTarget.style.boxShadow = '0 4px 6px rgba(0,0,0,0.1)';
    }}
    >
      {/* Product Image */}
      <div style={{
        fontSize: '4rem',
        textAlign: 'center',
        marginBottom: '1rem'
      }}>
        {product.image}
      </div>

      {/* Product Info */}
      <h3 style={{ margin: '0 0 0.5rem 0', fontSize: '1.2rem' }}>
        {product.name}
      </h3>
      
      <p style={{ 
        color: '#666', 
        fontSize: '0.9rem',
        margin: '0 0 1rem 0',
        height: '40px',
        overflow: 'hidden'
      }}>
        {product.description}
      </p>

      {/* Price and Rating */}
      <div style={{ 
        display: 'flex', 
        justifyContent: 'space-between', 
        alignItems: 'center',
        marginBottom: '1rem'
      }}>
        <span style={{ 
          fontSize: '1.5rem', 
          fontWeight: 'bold',
          color: '#2c3e50'
        }}>
          ${product.price}
        </span>
        <div style={{ display: 'flex', alignItems: 'center', gap: '0.25rem' }}>
          <span style={{ color: '#f39c12' }}>⭐</span>
          <span>{product.rating}</span>
        </div>
      </div>

      {/* Category and Stock */}
      <div style={{ 
        display: 'flex', 
        justifyContent: 'space-between',
        fontSize: '0.8rem',
        color: '#666',
        marginBottom: '1rem'
      }}>
        <span>🏷️ {product.category}</span>
        <span style={{ 
          color: product.inStock ? '#27ae60' : '#e74c3c',
          fontWeight: 'bold'
        }}>
          {product.inStock ? 'In Stock' : 'Out of Stock'}
        </span>
      </div>

      {/* Actions */}
      <div style={{ display: 'flex', gap: '0.5rem' }}>
        <button
          onClick={() => actions.toggleFavorite(product.id)}
          style={{
            flex: 1,
            padding: '0.5rem',
            backgroundColor: isFavorite ? '#e74c3c' : '#ecf0f1',
            color: isFavorite ? 'white' : '#2c3e50',
            border: 'none',
            borderRadius: '6px',
            cursor: 'pointer',
            fontSize: '1.2rem'
          }}
        >
          {isFavorite ? '❤️' : '🤍'}
        </button>
        
        {cartItem ? (
          <div style={{ 
            display: 'flex', 
            alignItems: 'center', 
            gap: '0.5rem',
            flex: 2
          }}>
            <button
              onClick={() => actions.updateQuantity(product.id, cartItem.quantity - 1)}
              style={{
                padding: '0.5rem',
                backgroundColor: '#e74c3c',
                color: 'white',
                border: 'none',
                borderRadius: '6px',
                cursor: 'pointer',
                fontSize: '1rem'
              }}
            >
              -
            </button>
            
            <span style={{ 
              flex: 1, 
              textAlign: 'center',
              fontWeight: 'bold'
            }}>
              {cartItem.quantity}
            </span>
            
            <button
              onClick={() => actions.updateQuantity(product.id, cartItem.quantity + 1)}
              disabled={!product.inStock}
              style={{
                padding: '0.5rem',
                backgroundColor: product.inStock ? '#27ae60' : '#bdc3c7',
                color: 'white',
                border: 'none',
                borderRadius: '6px',
                cursor: product.inStock ? 'pointer' : 'not-allowed',
                fontSize: '1rem'
              }}
            >
              +
            </button>
          </div>
        ) : (
          <button
            onClick={() => actions.addToCart(product)}
            disabled={!product.inStock}
            style={{
              flex: 2,
              padding: '0.5rem',
              backgroundColor: product.inStock ? '#3498db' : '#bdc3c7',
              color: 'white',
              border: 'none',
              borderRadius: '6px',
              cursor: product.inStock ? 'pointer' : 'not-allowed',
              fontSize: '1rem'
            }}
          >
            {product.inStock ? 'Add to Cart' : 'Out of Stock'}
          </button>
        )}
      </div>
    </div>
  );
};

// Компонент Filters
const Filters: React.FC = () => {
  const { state, actions } = useAppStore();
  const categories = ['all', ...new Set(mockProducts.map(p => p.category))];

  return (
    <div style={{
      backgroundColor: 'white',
      padding: '1.5rem',
      borderRadius: '12px',
      boxShadow: '0 4px 6px rgba(0,0,0,0.1)',
      marginBottom: '2rem'
    }}>
      <h3 style={{ margin: '0 0 1rem 0' }}>🔍 Filters</h3>
      
      <div style={{ display: 'grid', gap: '1rem' }}>
        {/* Category Filter */}
        <div>
          <label style={{ display: 'block', marginBottom: '0.5rem', fontWeight: 'bold' }}>
            Category:
          </label>
          <select
            value={state.filters.category}
            onChange={(e) => actions.setFilters({ category: e.target.value })}
            style={{
              width: '100%',
              padding: '0.5rem',
              border: '1px solid #ddd',
              borderRadius: '6px'
            }}
          >
            {categories.map(category => (
              <option key={category} value={category}>
                {category === 'all' ? 'All Categories' : category}
              </option>
            ))}
          </select>
        </div>

        {/* Price Range */}
        <div>
          <label style={{ display: 'block', marginBottom: '0.5rem', fontWeight: 'bold' }}>
            Price Range: ${state.filters.priceRange[0]} - ${state.filters.priceRange[1]}
          </label>
          <input
            type="range"
            min="0"
            max="2000"
            step="50"
            value={state.filters.priceRange[1]}
            onChange={(e) => actions.setFilters({ 
              priceRange: [0, parseInt(e.target.value)] 
            })}
            style={{ width: '100%' }}
          />
        </div>

        {/* Sort By */}
        <div>
          <label style={{ display: 'block', marginBottom: '0.5rem', fontWeight: 'bold' }}>
            Sort By:
          </label>
          <select
            value={state.filters.sortBy}
            onChange={(e) => actions.setFilters({ 
              sortBy: e.target.value as 'name' | 'price' | 'rating' 
            })}
            style={{
              width: '100%',
              padding: '0.5rem',
              border: '1px solid #ddd',
              borderRadius: '6px'
            }}
          >
            <option value="name">Name</option>
            <option value="price">Price</option>
            <option value="rating">Rating</option>
          </select>
        </div>

        {/* In Stock Only */}
        <div>
          <label style={{ display: 'flex', alignItems: 'center', gap: '0.5rem' }}>
            <input
              type="checkbox"
              checked={state.filters.inStock}
              onChange={(e) => actions.setFilters({ inStock: e.target.checked })}
            />
            In Stock Only
          </label>
        </div>
      </div>
    </div>
  );
};

// Компонент Cart
const Cart: React.FC = () => {
  const { state, actions, computed } = useAppStore();
  const [isOpen, setIsOpen] = useState(false);

  if (!isOpen) {
    return (
      <button
        onClick={() => setIsOpen(true)}
        style={{
          position: 'fixed',
          bottom: '2rem',
          right: '2rem',
          backgroundColor: '#3498db',
          color: 'white',
          border: 'none',
          borderRadius: '50%',
          width: '60px',
          height: '60px',
          fontSize: '1.5rem',
          cursor: 'pointer',
          boxShadow: '0 4px 15px rgba(0,0,0,0.2)',
          zIndex: 1000
        }}
      >
        🛒
        {computed.cartItemsCount > 0 && (
          <span style={{
            position: 'absolute',
            top: '-5px',
            right: '-5px',
            backgroundColor: '#e74c3c',
            color: 'white',
            borderRadius: '50%',
            width: '25px',
            height: '25px',
            fontSize: '0.8rem',
            display: 'flex',
            alignItems: 'center',
            justifyContent: 'center'
          }}>
            {computed.cartItemsCount}
          </span>
        )}
      </button>
    );
  }

  return (
    <div style={{
      position: 'fixed',
      top: 0,
      right: 0,
      bottom: 0,
      width: '400px',
      backgroundColor: 'white',
      boxShadow: '-4px 0 15px rgba(0,0,0,0.1)',
      zIndex: 1001,
      display: 'flex',
      flexDirection: 'column'
    }}>
      {/* Cart Header */}
      <div style={{
        padding: '1.5rem',
        borderBottom: '1px solid #eee',
        display: 'flex',
        justifyContent: 'space-between',
        alignItems: 'center'
      }}>
        <h3 style={{ margin: 0 }}>🛒 Your Cart</h3>
        <button
          onClick={() => setIsOpen(false)}
          style={{
            background: 'none',
            border: 'none',
            fontSize: '1.5rem',
            cursor: 'pointer'
          }}
        >
          ✕
        </button>
      </div>

      {/* Cart Items */}
      <div style={{ flex: 1, overflowY: 'auto', padding: '1rem' }}>
        {state.cart.length === 0 ? (
          <div style={{ 
            textAlign: 'center', 
            padding: '2rem',
            color: '#666'
          }}>
            <div style={{ fontSize: '3rem', marginBottom: '1rem' }}>🛒</div>
            <p>Your cart is empty</p>
          </div>
        ) : (
          state.cart.map(item => (
            <div
              key={item.product.id}
              style={{
                display: 'flex',
                gap: '1rem',
                padding: '1rem',
                border: '1px solid #eee',
                borderRadius: '8px',
                marginBottom: '1rem'
              }}
            >
              <div style={{ fontSize: '2rem' }}>{item.product.image}</div>
              
              <div style={{ flex: 1 }}>
                <h4 style={{ margin: '0 0 0.5rem 0' }}>{item.product.name}</h4>
                <p style={{ margin: 0, color: '#666', fontSize: '0.9rem' }}>
                  ${item.product.price} × {item.quantity}
                </p>
                <div style={{ 
                  display: 'flex', 
                  alignItems: 'center', 
                  gap: '0.5rem',
                  marginTop: '0.5rem'
                }}>
                  <button
                    onClick={() => actions.updateQuantity(item.product.id, item.quantity - 1)}
                    style={{
                      padding: '0.25rem 0.5rem',
                      backgroundColor: '#e74c3c',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: 'pointer'
                    }}
                  >
                    -
                  </button>
                  
                  <span style={{ fontWeight: 'bold' }}>{item.quantity}</span>
                  
                  <button
                    onClick={() => actions.updateQuantity(item.product.id, item.quantity + 1)}
                    style={{
                      padding: '0.25rem 0.5rem',
                      backgroundColor: '#27ae60',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: 'pointer'
                    }}
                  >
                    +
                  </button>
                  
                  <button
                    onClick={() => actions.removeFromCart(item.product.id)}
                    style={{
                      marginLeft: 'auto',
                      padding: '0.25rem 0.5rem',
                      backgroundColor: '#95a5a6',
                      color: 'white',
                      border: 'none',
                      borderRadius: '4px',
                      cursor: 'pointer',
                      fontSize: '0.8rem'
                    }}
                  >
                    Remove
                  </button>
                </div>
              </div>
            </div>
          ))
        )}
      </div>

      {/* Cart Footer */}
      {state.cart.length > 0 && (
        <div style={{
          padding: '1.5rem',
          borderTop: '1px solid #eee',
          backgroundColor: '#f8f9fa'
        }}>
          <div style={{ 
            display: 'flex', 
            justifyContent: 'space-between',
            marginBottom: '1rem',
            fontSize: '1.2rem',
            fontWeight: 'bold'
          }}>
            <span>Total:</span>
            <span>${computed.cartTotal.toFixed(2)}</span>
          </div>
          
          <button
            onClick={() => {
              alert('Order placed successfully!');
              actions.clearCart();
              setIsOpen(false);
            }}
            style={{
              width: '100%',
              padding: '1rem',
              backgroundColor: '#27ae60',
              color: 'white',
              border: 'none',
              borderRadius: '8px',
              cursor: 'pointer',
              fontSize: '1.1rem',
              fontWeight: 'bold'
            }}
          >
            Checkout
          </button>
        </div>
      )}
    </div>
  );
};

// Главный компонент E-commerce
const ECommerceApp: React.FC = () => {
  const { computed } = useAppStore();

  return (
    <div style={{ 
      minHeight: '100vh',
      backgroundColor: '#f8f9fa'
    }}>
      <Header />
      
      <main style={{
        maxWidth: '1200px',
        margin: '0 auto',
        padding: '2rem',
        display: 'grid',
        gridTemplateColumns: '300px 1fr',
        gap: '2rem'
      }}>
        {/* Sidebar */}
        <aside>
          <Filters />
        </aside>

        {/* Main Content */}
        <section>
          <div style={{ 
            display: 'flex', 
            justifyContent: 'space-between',
            alignItems: 'center',
            marginBottom: '2rem'
          }}>
            <h2 style={{ margin: 0 }}>Products</h2>
            <span style={{ color: '#666' }}>
              {computed.filteredProducts.length} products found
            </span>
          </div>

          {/* Products Grid */}
          <div style={{
            display: 'grid',
            gridTemplateColumns: 'repeat(auto-fill, minmax(280px, 1fr))',
            gap: '1.5rem'
          }}>
            {computed.filteredProducts.map(product => (
              <ProductCard key={product.id} product={product} />
            ))}
          </div>

          {computed.filteredProducts.length === 0 && (
            <div style={{ 
              textAlign: 'center', 
              padding: '4rem',
              backgroundColor: 'white',
              borderRadius: '12px'
            }}>
              <div style={{ fontSize: '4rem', marginBottom: '1rem' }}>🔍</div>
              <h3>No products found</h3>
              <p style={{ color: '#666' }}>
                Try adjusting your filters or search query
              </p>
            </div>
          )}
        </section>
      </main>

      <Cart />
    </div>
  );
};

export default ECommerceApp;
```
Пример 86: Real-time Dashboard с графиками
```jsx
import React, { useState, useEffect, useMemo, useCallback } from 'react';

// Типы
interface Metric {
  id: string;
  name: string;
  value: number;
  change: number;
  changeType: 'increase' | 'decrease';
  icon: string;
  color: string;
}

interface ChartData {
  labels: string[];
  datasets: {
    label: string;
    data: number[];
    borderColor: string;
    backgroundColor: string;
  }[];
}

interface Notification {
  id: string;
  type: 'info' | 'warning' | 'error' | 'success';
  title: string;
  message: string;
  timestamp: Date;
  read: boolean;
}

// Хук для реального времени (имитация)
const useRealtimeData = () => {
  const [metrics, setMetrics] = useState<Metric[]>([]);
  const [chartData, setChartData] = useState<ChartData>({ labels: [], datasets: [] });
  const [notifications, setNotifications] = useState<Notification[]>([]);
  const [isConnected, setIsConnected] = useState(true);

  // Имитация реального времени
  useEffect(() => {
    // Начальные данные
    const initialMetrics: Metric[] = [
      {
        id: '1',
        name: 'Total Users',
        value: 12480,
        change: 12.5,
        changeType: 'increase',
        icon: '👥',
        color: '#3498db'
      },
      {
        id: '2',
        name: 'Revenue',
        value: 89240,
        change: -2.3,
        changeType: 'decrease',
        icon: '💰',
        color: '#27ae60'
      },
      {
        id: '3',
        name: 'Conversion Rate',
        value: 4.2,
        change: 8.1,
        changeType: 'increase',
        icon: '📊',
        color: '#9b59b6'
      },
      {
        id: '4',
        name: 'Active Sessions',
        value: 892,
        change: 15.7,
        changeType: 'increase',
        icon: '🔗',
        color: '#e74c3c'
      }
    ];

    const initialChartData: ChartData = {
      labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
      datasets: [
        {
          label: 'Revenue',
          data: [65000, 59000, 80000, 81000, 86000, 89240],
          borderColor: '#3498db',
          backgroundColor: 'rgba(52, 152, 219, 0.1)'
        },
        {
          label: 'Users',
          data: [9800, 10200, 11200, 11800, 12100, 12480],
          borderColor: '#27ae60',
          backgroundColor: 'rgba(39, 174, 96, 0.1)'
        }
      ]
    };

    setMetrics(initialMetrics);
    setChartData(initialChartData);

    // Имитация обновлений в реальном времени
    const interval = setInterval(() => {
      setMetrics(prev => prev.map(metric => ({
        ...metric,
        value: metric.value + Math.floor(Math.random() * 10) * (metric.changeType === 'increase' ? 1 : -1),
        change: metric.change + (Math.random() - 0.5)
      })));

      // Добавление уведомлений
      if (Math.random() > 0.7) {
        const types: Notification['type'][] = ['info', 'warning', 'success'];
        const newNotification: Notification = {
          id: Date.now().toString(),
          type: types[Math.floor(Math.random() * types.length)],
          title: ['New user registered', 'System update', 'Payment received'][Math.floor(Math.random() * 3)],
          message: 'This is a real-time notification',
          timestamp: new Date(),
          read: false
        };
        
        setNotifications(prev => [newNotification, ...prev.slice(0, 9)]);
      }
    }, 3000);

    return () => clearInterval(interval);
  }, []);

  const markAsRead = useCallback((id: string) => {
    setNotifications(prev => prev.map(notif => 
      notif.id === id ? { ...notif, read: true } : notif
    ));
  }, []);

  const clearAllNotifications = useCallback(() => {
    setNotifications([]);
  }, []);

  return {
    metrics,
    chartData,
    notifications,
    isConnected,
    actions: {
      markAsRead,
      clearAllNotifications
    }
  };
};

// Компонент метрики
interface MetricCardProps {
  metric: Metric;
}

const MetricCard: React.FC<MetricCardProps> = ({ metric }) => {
  return (
    <div style={{
      backgroundColor: 'white',
      padding: '1.5rem',
      borderRadius: '12px',
      boxShadow: '0 4px 6px rgba(0,0,0,0.1)',
      borderLeft: `4px solid ${metric.color}`,
      transition: 'transform 0.2s'
    }}
    onMouseEnter={(e) => {
      e.currentTarget.style.transform = 'translateY(-2px)';
    }}
    onMouseLeave={(e) => {
      e.currentTarget.style.transform = 'translateY(0)';
    }}
    >
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start' }}>
        <div>
          <p style={{ 
            margin: '0 0 0.5rem 0', 
            color: '#666', 
            fontSize: '0.9rem',
            fontWeight: 'bold'
          }}>
            {metric.name}
          </p>
          <h3 style={{ 
            margin: '0 0 0.5rem 0', 
            fontSize: '2rem',
            fontWeight: 'bold'
          }}>
            {metric.value.toLocaleString()}
          </h3>
          <div style={{ 
            display: 'flex', 
            alignItems: 'center', 
            gap: '0.5rem',
            color: metric.changeType === 'increase' ? '#27ae60' : '#e74c3c'
          }}>
            <span style={{ fontWeight: 'bold' }}>
              {metric.changeType === 'increase' ? '↗' : '↘'} {Math.abs(metric.change).toFixed(1)}%
            </span>
            <span style={{ fontSize: '0.8rem' }}>
              from last period
            </span>
          </div>
        </div>
        
        <div style={{
          fontSize: '2.5rem',
          opacity: 0.8
        }}>
          {metric.icon}
        </div>
      </div>
    </div>
  );
};

// Простой компонент графика (CSS-based)
const SimpleChart: React.FC<{ data: ChartData }> = ({ data }) => {
  const maxValue = useMemo(() => 
    Math.max(...data.datasets.flatMap(dataset => dataset.data)), 
    [data]
  );

  return (
    <div style={{
      backgroundColor: 'white',
      padding: '1.5rem',
      borderRadius: '12px',
      boxShadow: '0 4px 6px rgba(0,0,0,0.1)',
      height: '300px'
    }}>
      <h3 style={{ margin: '0 0 1rem 0' }}>📈 Performance Overview</h3>
      
      <div style={{ 
        display: 'flex', 
        height: '200px', 
        alignItems: 'flex-end',
        gap: '1rem',
        padding: '1rem 0'
      }}>
        {data.labels.map((label, index) => (
          <div key={label} style={{ flex: 1, textAlign: 'center' }}>
            <div style={{ 
              display: 'flex', 
              flexDirection: 'column',
              alignItems: 'center',
              height: '100%',
              justifyContent: 'flex-end'
            }}>
              {data.datasets.map((dataset, datasetIndex) => {
                const value = dataset.data[index];
                const height = (value / maxValue) * 100;
                
                return (
                  <div
                    key={datasetIndex}
                    style={{
                      width: '20px',
                      height: `${height}%`,
                      backgroundColor: dataset.backgroundColor,
                      border: `2px solid ${dataset.borderColor}`,
                      borderRadius: '4px',
                      margin: '2px 0',
                      transition: 'height 0.3s ease'
                    }}
                    title={`${dataset.label}: ${value}`}
                  />
                );
              })}
            </div>
            <div style={{ 
              marginTop: '0.5rem',
              fontSize: '0.8rem',
              color: '#666',
              fontWeight: 'bold'
            }}>
              {label}
            </div>
          </div>
        ))}
      </div>

      {/* Легенда */}
      <div style={{ 
        display: 'flex', 
        justifyContent: 'center', 
        gap: '2rem',
        marginTop: '1rem'
      }}>
        {data.datasets.map((dataset, index) => (
          <div key={index} style={{ display: 'flex', alignItems: 'center', gap: '0.5rem' }}>
            <div style={{
              width: '12px',
              height: '12px',
              backgroundColor: dataset.borderColor,
              borderRadius: '2px'
            }} />
            <span style={{ fontSize: '0.8rem', color: '#666' }}>
              {dataset.label}
            </span>
          </div>
        ))}
      </div>
    </div>
  );
};

// Компонент уведомлений
const NotificationsPanel: React.FC<{
  notifications: Notification[];
  onMarkAsRead: (id: string) => void;
  onClearAll: () => void;
}> = ({ notifications, onMarkAsRead, onClearAll }) => {
  const [isOpen, setIsOpen] = useState(false);
  const unreadCount = notifications.filter(n => !n.read).length;

  const getNotificationIcon = (type: Notification['type']) => {
    switch (type) {
      case 'info': return 'ℹ️';
      case 'warning': return '⚠️';
      case 'error': return '❌';
      case 'success': return '✅';
      default: return '📢';
    }
  };

  const getNotificationColor = (type: Notification['type']) => {
    switch (type) {
      case 'info': return '#3498db';
      case 'warning': return '#f39c12';
      case 'error': return '#e74c3c';
      case 'success': return '#27ae60';
      default: return '#95a5a6';
    }
  };

  return (
    <div style={{ position: 'relative' }}>
      {/* Кнопка уведомлений */}
      <button
        onClick={() => setIsOpen(!isOpen)}
        style={{
          position: 'relative',
          background: 'none',
          border: 'none',
          fontSize: '1.5rem',
          cursor: 'pointer',
          padding: '0.5rem'
        }}
      >
        🔔
        {unreadCount > 0 && (
          <span style={{
            position: 'absolute',
            top: '0',
            right: '0',
            backgroundColor: '#e74c3c',
            color: 'white',
            borderRadius: '50%',
            width: '20px',
            height: '20px',
            fontSize: '0.8rem',
            display: 'flex',
            alignItems: 'center',
            justifyContent: 'center'
          }}>
            {unreadCount}
          </span>
        )}
      </button>

      {/* Панель уведомлений */}
      {isOpen && (
        <div style={{
          position: 'absolute',
          top: '100%',
          right: 0,
          width: '400px',
          backgroundColor: 'white',
          boxShadow: '0 10px 30px rgba(0,0,0,0.2)',
          borderRadius: '12px',
          zIndex: 1000,
          maxHeight: '500px',
          overflow: 'hidden'
        }}>
          {/* Заголовок */}
          <div style={{
            padding: '1.5rem',
            borderBottom: '1px solid #eee',
            display: 'flex',
            justifyContent: 'space-between',
            alignItems: 'center'
          }}>
            <h4 style={{ margin: 0 }}>Notifications</h4>
            <div style={{ display: 'flex', gap: '0.5rem' }}>
              {unreadCount > 0 && (
                <button
                  onClick={onClearAll}
                  style={{
                    padding: '0.5rem 1rem',
                    backgroundColor: '#95a5a6',
                    color: 'white',
                    border: 'none',
                    borderRadius: '6px',
                    cursor: 'pointer',
                    fontSize: '0.8rem'
                  }}
                >
                  Clear All
                </button>
              )}
              <button
                onClick={() => setIsOpen(false)}
                style={{
                  background: 'none',
                  border: 'none',
                  fontSize: '1.2rem',
                  cursor: 'pointer'
                }}
              >
                ✕
              </button>
            </div>
          </div>

          {/* Список уведомлений */}
          <div style={{ maxHeight: '400px', overflowY: 'auto' }}>
            {notifications.length === 0 ? (
              <div style={{ 
                padding: '2rem', 
                textAlign: 'center',
                color: '#666'
              }}>
                <div style={{ fontSize: '3rem', marginBottom: '1rem' }}>🔔</div>
                <p>No notifications</p>
              </div>
            ) : (
              notifications.map(notification => (
                <div
                  key={notification.id}
                  style={{
                    padding: '1rem 1.5rem',
                    borderBottom: '1px solid #f8f9fa',
                    backgroundColor: notification.read ? 'white' : '#f8f9fa',
                    cursor: 'pointer',
                    transition: 'background-color 0.2s'
                  }}
                  onClick={() => onMarkAsRead(notification.id)}
                  onMouseEnter={(e) => {
                    e.currentTarget.style.backgroundColor = '#f8f9fa';
                  }}
                  onMouseLeave={(e) => {
                    e.currentTarget.style.backgroundColor = notification.read ? 'white' : '#f8f9fa';
                  }}
                >
                  <div style={{ display: 'flex', gap: '1rem', alignItems: 'flex-start' }}>
                    <div style={{
                      fontSize: '1.2rem',
                      color: getNotificationColor(notification.type)
                    }}>
                      {getNotificationIcon(notification.type)}
                    </div>
                    
                    <div style={{ flex: 1 }}>
                      <div style={{ 
                        display: 'flex', 
                        justifyContent: 'space-between',
                        alignItems: 'flex-start',
                        marginBottom: '0.25rem'
                      }}>
                        <h5 style={{ 
                          margin: 0,
                          color: getNotificationColor(notification.type)
                        }}>
                          {notification.title}
                        </h5>
                        <span style={{ 
                          fontSize: '0.7rem',
                          color: '#666'
                        }}>
                          {notification.timestamp.toLocaleTimeString()}
                        </span>
                      </div>
                      <p style={{ 
                        margin: 0,
                        fontSize: '0.9rem',
                        color: '#666'
                      }}>
                        {notification.message}
                      </p>
                    </div>
                  </div>
                </div>
              ))
            )}
          </div>
        </div>
      )}
    </div>
  );
};

// Компонент статуса реального времени
const RealtimeStatus: React.FC<{ isConnected: boolean }> = ({ isConnected }) => {
  return (
    <div style={{
      display: 'flex',
      alignItems: 'center',
      gap: '0.5rem',
      padding: '0.5rem 1rem',
      backgroundColor: isConnected ? '#27ae60' : '#e74c3c',
      color: 'white',
      borderRadius: '20px',
      fontSize: '0.8rem',
      fontWeight: 'bold'
    }}>
      <div style={{
        width: '8px',
        height: '8px',
        backgroundColor: 'white',
        borderRadius: '50%',
        animation: isConnected ? 'pulse 2s infinite' : 'none'
      }} />
      {isConnected ? 'Live' : 'Disconnected'}
      
      <style>
        {`
          @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
          }
        `}
      </style>
    </div>
  );
};

// Главный компонент Dashboard
const RealtimeDashboard: React.FC = () => {
  const { metrics, chartData, notifications, isConnected, actions } = useRealtimeData();
  const [activeTab, setActiveTab] = useState<'overview' | 'analytics' | 'reports'>('overview');

  return (
    <div style={{ 
      minHeight: '100vh',
      backgroundColor: '#f8f9fa'
    }}>
      {/* Header */}
      <header style={{
        backgroundColor: 'white',
        padding: '1rem 2rem',
        boxShadow: '0 2px 10px rgba(0,0,0,0.1)',
        position: 'sticky',
        top: 0,
        zIndex: 100
      }}>
        <div style={{
          display: 'flex',
          justifyContent: 'space-between',
          alignItems: 'center',
          maxWidth: '1400px',
          margin: '0 auto'
        }}>
          <div style={{ display: 'flex', alignItems: 'center', gap: '2rem' }}>
            <h1 style={{ margin: 0, fontSize: '1.5rem' }}>📊 Analytics Dashboard</h1>
            
            <nav style={{ display: 'flex', gap: '1rem' }}>
              {['overview', 'analytics', 'reports'].map(tab => (
                <button
                  key={tab}
                  onClick={() => setActiveTab(tab as any)}
                  style={{
                    padding: '0.5rem 1rem',
                    backgroundColor: activeTab === tab ? '#3498db' : 'transparent',
                    color: activeTab === tab ? 'white' : '#666',
                    border: 'none',
                    borderRadius: '6px',
                    cursor: 'pointer',
                    textTransform: 'capitalize'
                  }}
                >
                  {tab}
                </button>
              ))}
            </nav>
          </div>

          <div style={{ display: 'flex', alignItems: 'center', gap: '1rem' }}>
            <RealtimeStatus isConnected={isConnected} />
            <NotificationsPanel
              notifications={notifications}
              onMarkAsRead={actions.markAsRead}
              onClearAll={actions.clearAllNotifications}
            />
          </div>
        </div>
      </header>

      {/* Main Content */}
      <main style={{
        maxWidth: '1400px',
        margin: '0 auto',
        padding: '2rem'
      }}>
        {/* Metrics Grid */}
        <div style={{
          display: 'grid',
          gridTemplateColumns: 'repeat(auto-fit, minmax(250px, 1fr))',
          gap: '1.5rem',
          marginBottom: '2rem'
        }}>
          {metrics.map(metric => (
            <MetricCard key={metric.id} metric={metric} />
          ))}
        </div>

        {/* Charts and Additional Content */}
        <div style={{
          display: 'grid',
          gridTemplateColumns: '2fr 1fr',
          gap: '2rem'
        }}>
          {/* Main Chart */}
          <SimpleChart data={chartData} />

          {/* Quick Stats */}
          <div style={{
            backgroundColor: 'white',
            padding: '1.5rem',
            borderRadius: '12px',
            boxShadow: '0 4px 6px rgba(0,0,0,0.1)'
          }}>
            <h3 style={{ margin: '0 0 1rem 0' }}>🚀 Quick Stats</h3>
            
            <div style={{ display: 'grid', gap: '1rem' }}>
              {[
                { label: 'Page Views', value: '24.8K', change: '+12%' },
                { label: 'Avg. Session', value: '4m 32s', change: '+3%' },
                { label: 'Bounce Rate', value: '42%', change: '-8%' },
                { label: 'New Users', value: '1.2K', change: '+15%' }
              ].map((stat, index) => (
                <div key={index} style={{
                  display: 'flex',
                  justifyContent: 'space-between',
                  alignItems: 'center',
                  padding: '0.75rem',
                  backgroundColor: '#f8f9fa',
                  borderRadius: '8px'
                }}>
                  <span style={{ fontWeight: 'bold' }}>{stat.label}</span>
                  <div style={{ textAlign: 'right' }}>
                    <div style={{ fontWeight: 'bold' }}>{stat.value}</div>
                    <div style={{ 
                      fontSize: '0.8rem',
                      color: stat.change.startsWith('+') ? '#27ae60' : '#e74c3c'
                    }}>
                      {stat.change}
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>
        </div>

        {/* Additional Sections */}
        <div style={{
          display: 'grid',
          gridTemplateColumns: 'repeat(auto-fit, minmax(300px, 1fr))',
          gap: '1.5rem',
          marginTop: '2rem'
        }}>
          {/* Recent Activity */}
          <div style={{
            backgroundColor: 'white',
            padding: '1.5rem',
            borderRadius: '12px',
            boxShadow: '0 4px 6px rgba(0,0,0,0.1)'
          }}>
            <h3 style={{ margin: '0 0 1rem 0' }}>📝 Recent Activity</h3>
            <div style={{ display: 'grid', gap: '1rem' }}>
              {[
                { action: 'User registration', user: 'John Doe', time: '2 min ago' },
                { action: 'Payment processed', user: 'Jane Smith', time: '5 min ago' },
                { action: 'Profile updated', user: 'Mike Johnson', time: '10 min ago' },
                { action: 'Order completed', user: 'Sarah Wilson', time: '15 min ago' }
              ].map((activity, index) => (
                <div key={index} style={{
                  display: 'flex',
                  alignItems: 'center',
                  gap: '1rem',
                  padding: '0.75rem',
                  backgroundColor: '#f8f9fa',
                  borderRadius: '8px'
                }}>
                  <div style={{
                    width: '8px',
                    height: '8px',
                    backgroundColor: '#3498db',
                    borderRadius: '50%'
                  }} />
                  <div style={{ flex: 1 }}>
                    <div style={{ fontWeight: 'bold' }}>{activity.action}</div>
                    <div style={{ fontSize: '0.8rem', color: '#666' }}>
                      by {activity.user} • {activity.time}
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>

          {/* System Status */}
          <div style={{
            backgroundColor: 'white',
            padding: '1.5rem',
            borderRadius: '12px',
            boxShadow: '0 4px 6px rgba(0,0,0,0.1)'
          }}>
            <h3 style={{ margin: '0 0 1rem 0' }}>⚙️ System Status</h3>
            <div style={{ display: 'grid', gap: '1rem' }}>
              {[
                { service: 'Web Server', status: 'operational', latency: '45ms' },
                { service: 'Database', status: 'operational', latency: '12ms' },
                { service: 'Cache', status: 'degraded', latency: '89ms' },
                { service: 'API Gateway', status: 'operational', latency: '23ms' }
              ].map((system, index) => (
                <div key={index} style={{
                  display: 'flex',
                  justifyContent: 'space-between',
                  alignItems: 'center',
                  padding: '0.75rem',
                  backgroundColor: '#f8f9fa',
                  borderRadius: '8px'
                }}>
                  <div>
                    <div style={{ fontWeight: 'bold' }}>{system.service}</div>
                    <div style={{ 
                      fontSize: '0.8rem',
                      color: system.status === 'operational' ? '#27ae60' : '#f39c12'
                    }}>
                      {system.status}
                    </div>
                  </div>
                  <div style={{ 
                    fontSize: '0.9rem',
                    color: '#666'
                  }}>
                    {system.latency}
                  </div>
                </div>
              ))}
            </div>
          </div>
        </div>
      </main>
    </div>
  );
};

export default RealtimeDashboard;
```
```
Примеры демонстрируют реальные production-кейсы:
 Ключевые особенности production-приложений:
E-commerce App:
Сложное управление состоянием с корзиной, избранным, фильтрами
Локальное хранилище для сохранения состояния
Оптимизированные вычисления с useMemo
Респонсивный дизайн с адаптивной сеткой
Интерактивные компоненты с hover-эффектами
Доступность и семантическая разметка
Real-time Dashboard:
Имитация реального времени с интервальными обновлениями
Сложные вычисления и агрегация данных
Уведомления в реальном времени
Визуализация данных с графиками
Статус системы и мониторинг
Оптимизация производительности
Продолжим с advanced техниками и оптимизациями?
```

https://github.com/GO-HTML-CSS-JS-REACT-VITE-PG-SASS-VUE/REACT-VITE/edit/main/README.md#:~:text=2025%20год

