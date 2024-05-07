# General

Repos:
- Frontend: [link](https://github.com/ltlaitoff/counter-frontend)
- Backend: [link](https://github.com/ltlaitoff/counter-backend)

Techonologies: 
- Frontend: Angular, tailwind
- Backend: Express, mongoose, swagger(<mark style="background: #BBFABBA6;">NEXT</mark>)

# Технічне завдання

Створити застосунок який буде використовуватись для підрахунку чогось, наприклад, підходів чи кількості виконаних вправ на тренувані. 

Основні сторінки:
- Authorization - Авторизація користувача за допомогою google identity
- Home - Додавання нових записів в статистику по категорії та коментару
- Categories - Додавання, зміна(в тому числі порядку) та видалення категорій
- Statistic - Додавання, зміна та видалення записів статистики. Перегляд статисики в виді графіку з можливістю вибору різних режимів, фільтрацій і сортувань 

Основною метою створення цього застосування є 
1. Мотивування людей до більш продуктивних занять(наприклад, спортом)
2. Надання користувачам можливості відстежувати прогрес переглядаючи статистику їх тренувань.

# Pages details

## Home page

- Великий input в який можливо вводити тільки числа
- Під інпутом поле для коментаря
- Справа от input select для вибору категорій
- Внизу кнопка, по кліку на яку буде відбуватись додавання
- При натискані на Enter - submit
- Категорія за змовчуванням - яку вибере користувач(store | Broadcast<mark style="background: #FFB86CA6;">(?)</mark> ) або ж сама перша 

## Categories page

Табличка с категоріями:

- Назва категорії
- Опис категорії
- Колір категорії
- При наведені на рядок - показати кнопки переміщення та видалення
- Редагування відбувається натисканням на ячейку 
- Пряцюючий ctrl + z <mark style="background: #FF5582A6;">(!)</mark>
- При натискані на колір показувати select

<mark style="background: #BBFABBA6;">(NEXT)</mark> Можливість створювати підкатегорії

## Statistic page

<mark style="background: #ADCCFFA6;">NOTE</mark> Дана секція може змінюватися, оскільки ще не відомий інструмент для роботи з графіками і не відомо які у нього будуть можливості

### Графік

Відображення даних у точковому вигляді із зв'язкою точок

Можливість відображення даних у графіку:
- За день (за часом скільки б не було підходів)
- за тиждень (сума за кожен день)
- За місяць
- <mark style="background: #BBFABBA6;">(NEXT)</mark> Можливість вибору періоду часу

Можливість вибору режиму відображення:
- "Скільки разів" - Показувати скільки разів було зроблено за підхід
- "Сумування" - Показувати наступний підхід з додаванням попереднього

Можливість вибору які саме категорії показувати

### Таблиця

Таблиця містить:
- Дата
- Кількість
- Коментар
- Категорія
- сума поточний + попередній цієї категорії

Сортування у таблиці:
- По даті
- За кількістю
- За категорією

Фільтрації у таблиці:

- По даті
- За кількістю
- За категорією

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
