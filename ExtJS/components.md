## Компоненты Ext JS

Компоненты являются основными строительными блоками приложений Ext JS. Они включают в себя интерфейсные элементы, такие как кнопки, панели, формы и сетки. Ext JS предоставляет широкий набор готовых к использованию компонентов, каждый из которых имеет свой функционал, внешний вид и набор событий.

## Основные компоненты Ext JS

### 1. Ext.Component

Базовый класс для всех компонентов в Ext JS. Все компоненты наследуются от него.

```javascript
// Создаем базовый компонент с HTML содержимым
Ext.create('Ext.Component', {
    html: '<h1>Hello, Ext JS!</h1>',  // Внутренний HTML компонента
    renderTo: Ext.getBody()  // Указываем место рендеринга компонента (в тело документа)
});
```

### 2. Ext.Button

Кнопка, которая может быть использована для выполнения действий.

```javascript
// Создаем кнопку с обработчиком клика
Ext.create('Ext.Button', {
    text: 'Click Me',  // Текст кнопки
    renderTo: Ext.getBody(),  // Место рендеринга кнопки
    handler: function() {  // Обработчик нажатия на кнопку
        alert('Button clicked!');  // Действие при клике
    }
});
```

### 3. Ext.Panel

Панель для отображения информации, может содержать другие компоненты.

```javascript
// Создаем панель с заголовком и содержимым
Ext.create('Ext.Panel', {
    title: 'My Panel',  // Заголовок панели
    width: 400,  // Ширина панели
    html: '<p>Panel content goes here</p>',  // Содержимое панели
    renderTo: Ext.getBody()  // Место рендеринга панели
});
```

### 4. Ext.form.Panel

Форма для ввода данных с полями и кнопками.

```javascript
// Создаем форму с текстовыми полями и кнопкой отправки
Ext.create('Ext.form.Panel', {
    title: 'Contact Form',  // Заголовок формы
    width: 300,  // Ширина формы
    bodyPadding: 10,  // Внутренние отступы формы
    items: [
        {
            xtype: 'textfield',  // Текстовое поле для ввода имени
            name: 'name',  // Имя поля
            fieldLabel: 'Name'  // Метка поля
        },
        {
            xtype: 'textfield',  // Текстовое поле для ввода email
            name: 'email',  // Имя поля
            fieldLabel: 'Email'  // Метка поля
        }
    ],
    buttons: [
        {
            text: 'Submit',  // Текст кнопки
            handler: function() {  // Обработчик кнопки
                alert('Form submitted');  // Действие при нажатии
            }
        }
    ],
    renderTo: Ext.getBody()  // Место рендеринга формы
});
```

### 5. Ext.grid.Panel

Таблица для отображения данных.

```javascript
// Создаем таблицу с данными о сотрудниках
Ext.create('Ext.grid.Panel', {
    title: 'Employee Data',  // Заголовок таблицы
    store: {
        fields: ['name', 'email'],  // Поля данных
        data: [  // Данные для отображения
            { name: 'John', email: 'john@example.com' },
            { name: 'Jane', email: 'jane@example.com' }
        ]
    },
    columns: [  // Определение колонок таблицы
        { text: 'Name', dataIndex: 'name', flex: 1 },  // Колонка с именем
        { text: 'Email', dataIndex: 'email', flex: 1 }  // Колонка с email
    ],
    height: 200,  // Высота таблицы
    width: 400,  // Ширина таблицы
    renderTo: Ext.getBody()  // Место рендеринга таблицы
});
```

### 6. Ext.tab.Panel

Панель с вкладками (табы).

```javascript
// Создаем панель с двумя вкладками
Ext.create('Ext.tab.Panel', {
    width: 400,  // Ширина панели
    height: 300,  // Высота панели
    items: [
        {
            title: 'Tab 1',  // Заголовок первой вкладки
            html: 'Content for Tab 1'  // Содержимое первой вкладки
        },
        {
            title: 'Tab 2',  // Заголовок второй вкладки
            html: 'Content for Tab 2'  // Содержимое второй вкладки
        }
    ],
    renderTo: Ext.getBody()  // Место рендеринга панели
});
```

### 7. Ext.window.Window

Всплывающее окно.

```javascript
// Создаем всплывающее окно
Ext.create('Ext.window.Window', {
    title: 'My Window',  // Заголовок окна
    height: 200,  // Высота окна
    width: 300,  // Ширина окна
    html: 'Hello! I am a window.',  // Содержимое окна
    renderTo: Ext.getBody()  // Место рендеринга окна
}).show();  // Показываем окно
```

### 8. Ext.form.field.Text

Поле ввода текста.

```javascript
// Создаем текстовое поле для ввода имени
Ext.create('Ext.form.field.Text', {
    fieldLabel: 'Name',  // Метка поля
    name: 'name',  // Имя поля
    renderTo: Ext.getBody()  // Место рендеринга поля
});
```

### 9. Ext.form.field.ComboBox

Выпадающий список для выбора значения.

```javascript
// Создаем ComboBox с локальными данными
Ext.create('Ext.form.field.ComboBox', {
    fieldLabel: 'Выберите опцию',  // Метка для поля
    store: ['Опция 1', 'Опция 2', 'Опция 3'],  // Локальные данные для выпадающего списка
    queryMode: 'local',  // Определяем режим поиска (локальный или удаленный)
    displayField: 'name',  // Поле, которое отображается в списке (здесь строка)
    renderTo: Ext.getBody()  // Указываем место для рендеринга ComboBox
});
```

### 10. Ext.layout.container.VBox/HBox

Контейнеры для размещения компонентов вертикально или горизонтально.

```javascript
// Создаем контейнер с кнопками, выровненными вертикально
Ext.create('Ext.panel.Panel', {
    width: 300,  // Ширина панели
    height: 200,  // Высота панели
    layout: {
        type: 'vbox',  // Тип компоновки - вертикальный
        align: 'stretch'  // Растягиваем компоненты по ширине
    },
    items: [
        { xtype: 'button', text: 'Button 1' },  // Кнопка 1
        { xtype: 'button', text: 'Button 2' }   // Кнопка 2
    ],
    renderTo: Ext.getBody()  // Место рендеринга панели
});
```

## Заключение
Каждый компонент в Ext JS предоставляет обширные возможности для настройки и управления интерфейсом, а использование комментариев в коде помогает лучше понять его структуру и функционал.

#### 1. [Работа с моделями данных](./model.md)
#### 2. [Управление данными](./store.md)
#### 3. [Работа с событиями](./events.md)