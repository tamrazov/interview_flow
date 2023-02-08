# interview_flow

1. Расскажи про свой опыт
2. Написать свой filter
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
    } else {
      return Promise.reject(new Error('Невозможно выполнить заказ'))
    }
  } else {
    return Promise.reject(new Error('Юзер не активен'))
  }
    
  
  return Promise.reject(new Error('Чтото пошло не так'))
}
```