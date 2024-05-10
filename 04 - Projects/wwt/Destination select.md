---
title: Destination select
created: 2024-05-09 14:28
last modified: Thursday 9th May 2024 14:28:23
aliases: 
tags:
  - wwt
---
# Destination select

Ця документація пояснює як повинен працювати вибірору напрямку

## Основні поняття

- `Destination` - Це зона, в якій ми хочемо шукати готелі, кімнати та інше

## Данні, з якими працює сервер

Також можна переглянути в swagger: `GeolocationDto`

Backend приймає наступні поля:
- `radius` - Radius of circle in kilometers. Used to search offer in circle. maximum: 200; minimum: 0
- `topLeft` - required. This point used to search by dot or rectangle.
	- `latitude` - required. Number. Latitude coordinate for geolocation search.
	- `longitude` - required. Number. Longitude coordinate for geolocation search.
- `bottomRight` - required. This point used to search by rectangle.
	- `latitude` - required. Number. Latitude coordinate for geolocation search.
	- `longitude` - required. Number. Longitude coordinate for geolocation search.

Хоч у нас і три поля, але `backend` може приймати два варіанти destination:
1. По точці з радіусом - через `radius` та `topLeft` в якості точки
2. Через прямокутник - через `topLeft` та `bottomRight`

**В цій документації розглядається тільки варіант з точкою та радіусом**

## Два поля для вибору destination

На сайті у користувача є два поля вибору destination(далі вони будуть називатись `destination select`): в `Main Search` та на карті

**Ці елементи повинні бути синхронізовані**. Тобто, коли користувач обирає щось в одному елементі - в другому це такод повинно показатись

## Як повинен працювати вибір через точку

Розглянемо деякі приклади роботи `destination select`

### Через destination select на main search

Коли користувач обирає через `main search` `destination select` якесь місто:
- В `topLeft` записуються його координати
- Радіус залишається таким, яким він був до зміни `topLeft`
- В `main search` `destination select` показується `destination`, який обрав користувач

А також якщо карта відкрита:
- `destination select` на карті повинен показувати той самий `destination`, який вибрав користувач
- На карті показується точка(координати `topLeft`) з кругом(`radius`) по якому буде йти пошук

У нас немає механізму зміни радіусу на `main search`

### Через destination select на карті

Коли користувач через карту обирає `destination select` якесь місто:
- В `topLeft` записуються його координати
- Радіус залишається таким, яким він був до зміни `topLeft`
- `destination select` на `main search` повинен показувати той самий `destination`, який вибрав користувач на карті
- На карті показується точка(координати `topLeft`) з кругом(`radius`) по якому буде йти пошук

### Зміна radius

Припустимо, користувач обрав `destination`, але тепер його не влаштовує радіус

**Радіус можна змінити на карті**

При зміні радіуса також повинен змінюватись круг, який візуально відображає цей радіус на карті

### Через точку на карті

Користувач може захотіти також поставити точку на карті

Координати цієї точки запишуться в `topLeft`

**А в обидвох `destination select` повинен показатись приблизний destination до цієї точки**

## Як повинен працювати вибір через прямокутник

Поки-що ніяк)