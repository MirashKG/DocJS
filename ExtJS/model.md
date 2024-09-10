### Ext JS модель данных

В Ext JS модель данных (Ext.data.Model) — это фундаментальный класс для представления структуры данных в приложении. Он используется для описания и управления данными, которые могут быть получены с сервера или введены пользователем. Модель определяет, как данные будут храниться, какие поля будут в них содержаться, и как данные будут синхронизироваться с хранилищем или сервером.

#### Основные концепции Ext.data.Model

1. **Определение полей модели**: В модели определяются поля, которые описывают структуру данных, и их типы.
2. **Валидация данных**: Модель поддерживает встроенные механизмы для проверки корректности данных.
3. **Связь с хранилищем данных (`Store`)**: Модели работают в связке с хранилищами данных (Ext.data.Store), которые управляют коллекциями экземпляров моделей.


#### Пример создания модели:

```javascript
// Определение модели User
Ext.define('MyApp.model.User', {
    extend: 'Ext.data.Model',  // Наследуем от Ext.data.Model
    
    fields: [  // Описываем поля модели
        { name: 'id', type: 'int' },  // Поле id, тип integer
        { name: 'name', type: 'string' },  // Поле name, тип строка
        { name: 'email', type: 'string' },  // Поле email, тип строка
        { name: 'birthdate', type: 'date', dateFormat: 'Y-m-d' }  // Поле birthdate, тип дата
    ]
});
```

#### Пояснение к коду:

- `extend`: Мы наследуемся от `Ext.data.Model`, чтобы создать свою модель.
- `fields`: Массив полей, определяющий свойства модели и их типы. Мы можем указать типы данных, такие как `string`, `int`, `date` и другие.
- `dateFormat`: Указывает формат данных для полей типа `date`.

#### Пример использования модели:

```javascript
// Создаем экземпляр модели User
let user = Ext.create('MyApp.model.User', {
    id: 1,
    name: 'John Doe',
    email: 'johndoe@example.com',
    birthdate: '1985-09-15'
});

// Доступ к полям модели
console.log(user.get('name'));  // Выведет: 'John Doe'
console.log(user.get('email'));  // Выведет: 'johndoe@example.com'

// Установка значения поля
user.set('email', 'newemail@example.com');
```

### Валидация данных:

Модель поддерживает встроенные механизмы валидации, которые помогают проверять корректность данных перед их сохранением или отправкой на сервер. Для этого нужно использовать свойство `validators` внутри модели.

```javascript
Ext.define('MyApp.model.User', {
    extend: 'Ext.data.Model',
    
    fields: [
        { name: 'id', type: 'int' },
        { name: 'name', type: 'string' },
        { name: 'email', type: 'string' }
    ],
    
    validators: {  // Определяем правила валидации
        name: { type: 'presence', message: 'Имя обязательно для заполнения' },  // Поле name должно быть заполнено
        email: { type: 'email', message: 'Введите корректный email' }  // Поле email должно быть валидным email-адресом
    }
});
```

### Связи между моделями (Associations):

Ext JS поддерживает создание связей между моделями, таких как `hasMany` и `belongsTo`. Это полезно для описания отношений "один ко многим" или "многие к одному".

#### Пример связи "один ко многим":

```javascript
// Модель User
Ext.define('MyApp.model.User', {
    extend: 'Ext.data.Model',
    
    fields: ['id', 'name'],
    
    hasMany: {  // Связь "один ко многим" с моделью Post
        model: 'MyApp.model.Post',
        name: 'posts'
    }
});

// Модель Post
Ext.define('MyApp.model.Post', {
    extend: 'Ext.data.Model',
    
    fields: ['id', 'userId', 'content'],
    
    belongsTo: 'MyApp.model.User'  // Связь "многие к одному" с моделью User
});
```

#### Пример работы с моделями и Store:

```javascript
// Определение хранилища для пользователей
Ext.create('Ext.data.Store', {
    model: 'MyApp.model.User',  // Используем модель User
    data: [
        { id: 1, name: 'John Doe', email: 'john@example.com' },
        { id: 2, name: 'Jane Smith', email: 'jane@example.com' }
    ]
});

// Получение пользователя и его постов
let user = Ext.create('MyApp.model.User', { id: 1, name: 'John Doe' });
user.posts().load();  // Загрузка связанных постов
```

### Заключение:
`Ext.data.Model` — это ключевая часть архитектуры Ext JS для работы с данными. Она позволяет управлять структурами данных, проверять их валидность, синхронизировать с сервером, а также поддерживает создание связей между моделями для описания более сложных структур данных.

## Ссылки на другие файлы

#### 1. [Управление данными](./store.md)
#### 2. [Пример использования компонентов](./components.md)
#### 3. [Работа с событиями](./events.md)