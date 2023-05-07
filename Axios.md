<div align="center"><h1><img src="https://avatars.githubusercontent.com/u/32372333?s=280&v=4" alt="axios" width="50" height="50"> Axios</h1></div>

[⚙️ Menu](README.md)

### Ссылки:
- GitHub: https://github.com/axios/axios
- Web: https://axios-http.com/

### Что такое Axios?
**Axios** - это HTTP-клиент, основанный на Promise для node.js и браузера. Он изоморфный (= он может работать в браузере и node.js с той же базой кодов). На стороне сервера он использует нативный node.js http-модуль, тогда как на стороне клиента (браузер) он использует XMLHttpRequests.

### Особенности

- Делает XMLHttpRequests запросы из браузера
- Делает http запросы из node.js
- Поддерживает Promise API
- Перехватывает запросы и ответы
- Преобразовывает данные запроса и ответа
- Отменяет запросы
- Автоматическое преобразование для JSON-данных
- Поддержка на стороне клиента для защиты от XSRF

### Установка

Если вы используете Node.js, установите его с помощью npm:
- `npm install axios`

Если вы работаете в браузере, вы можете добавить ссылку на CDN в ваш HTML файл:
- `<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>`

---

### Как использовать Axios:

1. Импортируйте Axios (если используете Node.js):
```js
const axios = require('axios');
```
2. Выполните HTTP-запрос:

GET-запрос:
```js
axios.get('https://api.example.com/data')
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```
POST-запрос:
```js
const data = {
  key1: 'value1',
  key2: 'value2'
};

axios.post('https://api.example.com/data', data)
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```
3. Обрабатывайте ответ сервера внутри функции **.then()** и ошибки с помощью функции **.catch()**.

Axios также предоставляет другие возможности, такие как настройка базового URL, использование промежуточного обработчика (interceptors), отмена запросов, установка таймаутов и т. д.

---

### Пример работы в React:

```js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const ExampleComponent = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await axios.get('https://api.example.com/data');
        setData(response.data);
      } catch (error) {
        console.error('Error:', error);
      }
    };

    fetchData();
  }, []); // Пустой массив зависимостей означает, что запрос будет выполнен только при монтировании компонента

  return (
    <div>
      {data.map(item => (
        <div key={item.id}>
          {/* Отображение данных */}
        </div>
      ))}
    </div>
  );
};

export default ExampleComponent;
```

В этом примере:

1. Мы импортируем React, useState, useEffect и axios.
2. Создаем состояние data для хранения данных, полученных с сервера.
3. Внутри useEffect, объявляем асинхронную функцию fetchData, которая выполняет HTTP-запрос с помощью Axios.
4. Вызываем функцию fetchData для выполнения запроса при монтировании компонента.
5. Обрабатываем полученные данные и ошибки с помощью try и catch.
6. Отображаем данные в пользовательском интерфейсе.

Обратите внимание, что этот пример использует асинхронные функции и await для обработки промисов. Если вы предпочитаете использовать методы .then() и .catch(), вы также можете адаптировать пример для этого стиля.
