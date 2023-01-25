
## Estimated time

`*Docs` - Write docs for project and read documentation

### Good

- Docs: 2h
- Backend 6h
- Frontend 15h
- Summ 23h

### Bad

- Docs: 4h
- Backend 15h
- Frontend 31h
- Summ 50h

### Current

- Docs: 3h 42 m (48m write docs for project)
- Backend 
- Frontend 
- Summ 

## Home page

- Большой input в который можно вводить только числа
- Под инпутом поле для коментария
- Справа от input select для выбора категорий
- Внизу кнопка, по которой будет происходить добавление
- При нажатии на Enter - submit
- Категория по умолчанию - которую выберет пользователь или самая первая

## Categories page

Табличка с категориями:

- Название категории
- Описание категории
- Цвет категории
- При наведении на строку - справа показать кнопки перемещения и удаления
- Редактирование осуществляется нажатием на ячейку таблицы и изменение значения
- Работающий ctrl + z
- При нажатии на цвет показывать вспывашку в которой можно выбрать нужный цвет

<mark style="background: #BBFABBA6;">(NEXT)</mark> Возможность делать подкатегории

## Statistic page

<mark style="background: #ADCCFFA6;">NOTE</mark> Данная секция может меняться, по скольку ещё не известен инструмент для работы с графиками и не известно какие у него будут возможности

### График

Отображение данных в тотечном виде с связкой точек

Возможность отображение данных в графике:
	- За день(по времени сколько бы ни было подходов)
	- За неделю (сумма за каждый день)
	- За месяц
	- <mark style="background: #BBFABBA6;">(NEXT)</mark> Возможность выбора периода времени

Возможность выбора режима отображения:
	- "Сколько раз" - Показывать сколько раз было сделанно за подход
	- "Сумирование" - Показывать следующий подход с додаванием предыдущего

Возможность выбора какие именно категории показывать

### Таблица статистики

Таблица содержит:
- Дата
- Количество
- Коментарий
- Категория
- Сумма текущий + предыдущий этой же категории

Сортировки в таблице:
- По дате
- По количеству
- По категории

Фильтрации в таблице:

- По дате
- По количеству
- По категории

## Techical moments

### DataBase models

#### User

```json
{
	_id: ObjectID,
	name: string,
	picture: string | undefined,
	hd: string,
	email: string,
	email_verified: boolean,
	given_name: string, 
	family_name: string,
	key: string,
}
```

#### Category

```json
{
	_id: ObjectID,
	user: User._id,
	name: string,
	comment: string,
	color: Colors._id,
	order: number
}
```

#### Color

```json
{
	_id: ObjectID,
	name: string,
	colorHEX: string
}
```

#### Statistic

```json
{
	_id: ObjectID,
	user: User._id,
	date: Date,
	count: number,
	comment: string,
	category: Category._id,
	summ: number
}
```

### API Requests

#### User

<mark style="background: #ADCCFFA6;">GET</mark> : 
- Get user by `_id` 
- Get all users <mark style="background: #CACFD9A6;">ADMIN</mark>  <mark style="background: #BBFABBA6;">(NEXT)</mark>

<mark style="background: #BBFABBA6;">POST</mark> : Add new user
<mark style="background: #FF5582A6;">DELETE</mark> : Delete user
<mark style="background: #FFB86CA6;">PUT</mark> : Update user info

#### Category 

<mark style="background: #ADCCFFA6;">GET</mark> : 
- Get all by `user._id` (populate colors)

<mark style="background: #BBFABBA6;">POST</mark> : Add new category
<mark style="background: #FF5582A6;">DELETE</mark> : Delete category
<mark style="background: #FFB86CA6;">PUT</mark> : Update category

#### Color

<mark style="background: #ADCCFFA6;">GET</mark> : Get all

<mark style="background: #BBFABBA6;">POST</mark> : <mark style="background: #CACFD9A6;">ADMIN</mark>  <mark style="background: #BBFABBA6;">(NEXT)</mark>
<mark style="background: #FF5582A6;">DELETE</mark> : <mark style="background: #CACFD9A6;">ADMIN</mark>  <mark style="background: #BBFABBA6;">(NEXT)</mark>
<mark style="background: #FFB86CA6;">PUT</mark> : <mark style="background: #CACFD9A6;">ADMIN</mark>  <mark style="background: #BBFABBA6;">(NEXT)</mark>

#### Statistic

<mark style="background: #ADCCFFA6;">GET</mark> : 
- Get all by `user._id` (populate category) with search and filtration
<mark style="background: #BBFABBA6;">POST</mark> : Add new record
<mark style="background: #FF5582A6;">DELETE</mark> : Delete record <mark style="background: #BBFABBA6;">(NEXT)</mark>
<mark style="background: #FFB86CA6;">PUT</mark> : Update record info <mark style="background: #BBFABBA6;">(NEXT)</mark>
