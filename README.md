# interview_flow
Привет. как дела? давай начнем с простых важных вопрос, потом будет интереснее, потом порешаем кое что, потом про реакт поговорим.
Можешь гуглить все что угодно, я буду тебе подсказывать, можешь спрашивать что хочешь.

1. Расскажи про свой опыт, что делал, расскажи подробнее про твои задачи. Сложные и интересные задачи.
2. Что происходит когда набираем google.com
2. Расскажи про HTTP? Кто является сервером, а кто клиентом? Коды ответа?
4. Что такое JS? Однопоточный или многопоточный? Можно ли создать еще один тред?
4. JS - ассинхронный или синхронный?
4. что такое чистые функции?
5. Расскажи вкраце про event-loop
6. Написать свой filter
```js
const isEvent = (num) => num % 2 === 0 ? true : false

[1, 2, 3].myFilter(isEven) // [2]
```
3. Сделать ревью кода
```js
interface InterfaceOrder {
  id: string
  title: string
  description: string
  date: string
}

async function createOrder({
  user,
  order
}: {
  user?: { id: string, name?: string }
  order: InterfaceOrder
}) {
  const userName = user ? user.name ? user.name : 'noname' : 'unknown'
  const userActive = user?.id ? true : false

  window.localStorage.setItem('user', `${userName}`)

  if(userActive) {
    const params = {
      id: order.id,
      userId: user?.id || '',
    }

    if(order.id) {
      fetch('api/v1/create_order' + '?' + new URLSearchParams(params), { method: 'GET' })
        .then(() => console.warn('Заказ успешно создан'))
        .catch(console.error)
    } else {
      return Promise.reject(new Error('Невозможно выполнить заказ'))
    }
  } else {
    return Promise.reject(new Error('Юзер не активен'))
  }
    
  
  return Promise.reject(new Error('Чтото пошло не так'))
}
```

Проблемы этого кода:
1. Названия везде
2. Тип юзера можно вынести
3. Тип возвращаего ?
4. сайд-эффект
5. userActive нужен здесь?
6. убрать ифы
7. Промисы и асинки
8. Запрос
9. Исключения
10. Ответственность этой функции


import { useEffect, useRef } from 'react';

/**
 * Custom React hook that calls a function only once.
 *
 * @param {Function} callback - The function to be called.
 */
const useCallOnce = (callback: Function) => {
  const hasCalled = useRef(false);

  useEffect(() => {
    if (!hasCalled.current) {
      callback();
      hasCalled.current = true;
    }
  }, [callback]);
};

7. Расскажи про реакт? виртуал дом? зачем ключи? какие хуки знаешь?

   План собеседования Middle React Frontend Developer:
Основы HTML и CSS:

HTML:

Атрибуты, элементы, структура документа.
Формы, таблицы, семантические теги.
Преимущества приведения атрибутов в нижний регистр.
DOCTYPE, процесс парсинга HTML, событие "DOMContentLoaded".
CSS:

Каскадирование стилей, наследование.
Flexbox и Grid: основы и применение.
Медиа-запросы и адаптивный дизайн.
Critical CSS и его влияние на начальный рендеринг.
Основы JavaScript:

Типы данных, операторы, циклы.
Функции, замыкания, промисы.
DOM и события: манипуляции DOM, делегирование событий.
Асинхронное программирование.
React:

Основы:

Компоненты, JSX.
Состояние и жизненный цикл компонентов.
Работа с формами и событиями.
Управление состоянием:

Context API, Redux.
Нормализация данных в Redux.
Иммутабельность и её роль в управлении состоянием.
Производительность:

Виртуальный DOM и механизм согласования.
React Fiber и его преимущества.
Шаблонизация и маршрутизация:

Использование React Router.
Шаблонизация компонентов и маршрутов.
Тестирование:

Jest, Enzyme.
Тестирование компонентов, снимки (snapshots).
Advanced React:

Хуки (Hooks):

Использование useState, useEffect, useContext и других хуков.
Контекст и порталы:

Продвинутое использование Context API.
Порталы для управления DOM за пределами иерархии компонентов.
Анимации:

CSS-анимации и библиотеки, такие как React Spring.
Применение анимаций в интерфейсах React.
Сборка и оптимизация:

Webpack: конфигурация и основные плагины.
Babel: транспиляция кода.
Оптимизация кода и ресурсов для production сборки.
Тестирование:

Unit тестирование:

Написание тестов с использованием Jest и Enzyme.
Тестирование редьюсеров и компонентов.
Интеграционное тестирование:

Cypress или другие инструменты.
Тестирование взаимодействия между компонентами.
Безопасность:

Применение HTTPS и базовые принципы безопасной фронтенд-разработки.
Защита от XSS и CSRF атак.
Оптимизация производительности:

Профилирование и оптимизация кода.
Ленивая загрузка компонентов и ресурсов



// Пример использования
const multiplyByTwo = multiplyBy(2);
const multiplyByFive = multiplyBy(5);

console.log(multiplyByTwo(3)); // Ожидаемый результат: 2 * 3 = 6
console.log(multiplyByFive(4)); // Ожидаемый результат: 5 * 4 = 20
console.log(multiplyByTwo(5)); // Ожидаемый


Напишите обобщенную функцию mergeObjects, которая принимает два объекта и возвращает новый объект, содержащий свойства обоих объектов. Однако, функция должна быть также способной обрабатывать объекты с разными типами свойств.

function mergeObjects<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

// Пример использования
const result1 = mergeObjects({ a: 1, b: 2 }, { c: 3, d: 4 });
console.log(result1); // Ожидаемый результат: { a: 1, b: 2, c: 3, d: 4 }

const result2 = mergeObjects({ name: "John" }, { age: 25 });
console.log(result2); // Ожидаемый результат: { name: "John", age: 25 }


```js
interface InterfaceOrder {
  id: string
  title: string
  description: string
  date: string
}

async function createOrder({
  user,
  order
}: {
  user?: { id: string, name?: string }
  order: InterfaceOrder
}) {
  const userName = user ? (user.name ? user.name : 'noname') : 'unknown';
  const userActive = user?.id ? true : false;

  window.localStorage.setItem('user', `${userName}`);

  if (order.description.length > 20) {
    order.date = new Date().toISOString();
  }

  if (userActive) {
    const params = {
      id: order.id,
      userId: user?.id || '',
    };

    if (order.id) {
      const checkInventoryPromise = fetch('api/v1/check_inventory' + '?' + new URLSearchParams(params), { method: 'GET' });
      const createOrderPromise = fetch('api/v1/create_order' + '?' + new URLSearchParams(params), { method: 'GET' });
    
      checkInventoryPromise
        .then(response => response.json())
        .then(inventoryResult => {
          if (!inventoryResult.available) {
            console.error('Инвентарь недоступен');
            console.error('Произошла ошибка создания заказа: Инвентарь недоступен');
            return Promise.reject(new Error('Unable to place order.'));
          }
          return createOrderPromise;
        })
        .then(response => response.json())
        .then(orderResult => {
          console.warn('Заказ успешно создан', orderResult);
        })
        .catch(error => {
          console.error(error.toString());
          return Promise.reject(new Error('Something went wrong.'));
        });
    } else {
      console.error('Произошла ошибка создания заказа: Отсутствует ID заказа');
      return Promise.reject(new Error('Unable to place order.'));
    }
  } else {
    console.error('Произошла ошибка создания заказа: Пользователь не активен');
    return Promise.reject(new Error('Unable to place order.'));
  }

  console.error('Произошла неизвестная ошибка');
  return Promise.reject(new Error('Something went wrong.'));
}

// Пример вызова функции createOrder для тестирования
createOrder({
  user: { id: '123', name: 'john_doe' },
  order: { id: '456', title: 'New Order', description: 'A long description to trigger mutation error', date: new Date().toISOString() }
})
.catch(error => {
  console.error('Ошибка создания заказа:', error.message);
});

```
