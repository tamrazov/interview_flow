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
      fetch('api/v1/create_order'+ '?' + new URLSearchParams(params), { method: 'GET' })
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
7. Расскажи про реакт? виртуал дом? зачем ключи? какие хуки знаешь?