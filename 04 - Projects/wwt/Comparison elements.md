---
title: Comparison elements
created: 2024-07-02 09:15
last modified: Tuesday 2nd July 2024 09:15:14
aliases: 
tags:
  - winwintravel
---
# Comparison elements

Як у нас працюють тултіпи на comparison page

У нас всього є 2 види та n типів елементів:
- Базові
	- На які не можна натиснути - ціна, кількість гостей
	- На які можна натиснути - назва кімнати
- Фічі
	- На які можна натиснути
	- На які не можна натиснути
	- Без обранної опції


Тултіпи при наведенні на базові елементи відображаються унікально:
- При наведенні на ціну потрібно відобразити `€{priceOneDay} × {nights} nights = €{offerPrice}`
- При наведенні на адресу - потрібно показати `{address} on map`
- При наведенні на кількість гостей - чекаємо на дизайн
- 



Як це повинно працювати:
Користувач клікає на відкриття календаря
Користувач не може клікнути на кнопку Apply поки щось не змінить(зараз може)
Користувач після того як щось змінив повинен та закриває модалку повинен побачити підтвердження чи хочу він примінити нові дати
ДАТИ не повинні змінюватись відразу в useSearchRequest сторі як це відбувається зараз, це повинно відбуватись тільки після підтвердження в вікні підтвердження