---
title: Calendar
created: 2024-05-14 06:51
last modified: Tuesday 14th May 2024 06:51:44
aliases: 
tags:
  - winwintravel
---
# Calendar

## Загальна інформація

Календар можна поділити на: сам календар, модалку в якій він рендериться та кнопки керування ним

Модалка - звичайна модалка Chakra UI. Просто місце для рендера календаря, не більше

Сам календар надає можливість вибору дат(логіка цього описана нижче), можливість переключення по різним дням та інше

Кнопки керування надають змогу обрати один з трьох режимів роботи:
- `Exact date` - (default) Пошук по саме тим датам, які тут написанні
- `+- days` - (disabled) Пошук по датам, які ввів користувач, але +- кількість днів яку також вказав користувач. Цей функціонал зараз не підтримується backend тому він вимкнений
- `Number of days in the period` - (disabled) Гадки не маю як воно повинно працювати

Важливо розуміти, що календар можна використовувати окремо від кнопок, так само як і кнопки можна використовувати окремо від календаря

### Як працює відправка данних на backend

Для відправки данних, які ми обрали в календарі в `searchRequest`(так ми називаємо данні, які відправляються на backend і по яким відбувається пошук) ми записуємо наступне:

```tsx
{
  ...otherSearchRequestParams,
  stay: {
    defaultStayPeriod: {
      checkIn: "2024-01-10" // First date from calendar
      checkOut: "2024-01-16" // Second date from calendar
    }
  }
}
```

Як ми можемо бачити, тут немає інформації про режим, який обраний через кнопки керування календарем. Тому ці кнопки і вимкненні

## Логіка вибору дат

Коли у нас немає дат:
- Ми обираємо одну

Коли у нас є одна дата(`date1`):
- Якщо користувач обирає дату(`date2`), яка більше `date1` - `date2` стає кінцем діапазону, а `date1` - початком
- Якщо користувач обирає дату(`date2`), яка меньша `date1` - `date2` стає початком діапазону, а `date1` - кінцем

Коли у нас вже є діапазон ми повінні надати людині можливість розширення діапазону
- Якщо користувач обирає дату(`date2`) яка є меньшою ніж дата, яка зараз на початку діапазона(`date-start`), то ми перезаписуємо дату початку діапазону на `date2`
- Якщо користувач обирає дату(`date2`) яка є більшою ніж дата, яка зараз на кінці діапазона(`date-end`), то ми перезаписуємо дату кінця діапазону на `date2`(тобто один раз розширюємо кінень діапазона)

Якщо людина два рази **ПІДРЯД** розширює кінець або початок - ми ставимо тільки одну точку

Коли користувач клікає в середині діапазона тут результат залежить від того, який останній елемент обирав користувач.

Якщо користувач перший раз клікає всередині діапазону:
- Якщо користувач останім обирав дату початку(`start`) то дата, на яку користувач клікнув стає датою кінця діапазону
- Якщо користувач останім обирав дату кінця(`end`) то дата, на яку користувач клікнув стає датою початку діапазону

Якщо користувач n-й раз **підряд** клікає всередині діапазону:
- Якщо користувач попередній раз змінював дату старту, то дата, на яку користувач клікнув стає датою кінця діапазону
- Якщо користувач попередній раз змінював дату кінця, то дата, на яку користувач клікнув стає датою старту діапазону

## Інше

У нас не повинен показуватись попередній місяць від текущого
У нас повинно максимум показуватись 12 місяців від текущого

Дати в поллі вводу повинні оновлюватись тільки, якщо у нас правильний діапазон з двох дат

## Як тестувати це все

Як протестувати календар з нуля:
1. Зайти на сайт production або development
2. Якщо у нас є встановленні данні за замовчуванням - в URLSearchParams потрібно видалити `stay.defaultStayPeriod.checkOut` та `stay.defaultStayPeriod.checkIn` параметри
3. Оновити сторінку
4. Тикати

Приклад:
https://winwin.jstuffs.com/?flagSearch.isSearchWithOfferDynamicData=true&flagSearch.isSearchWithHotelStaticData=true&flagSearch.isSearchWithRoomStaticData=true&pagination.limit=12&pagination.offset=0&sortBy=PRICE_ASC&geolocation.radius=200&geolocation.topLeft.latitude=52.377956&geolocation.topLeft.longitude=4.89707&guestQuantity.adultsQuantity=2&integrationSearch.integrationName=FAKE_INTEGRATION