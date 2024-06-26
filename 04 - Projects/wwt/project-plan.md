---
title: WinWinTravel MVP
tags:
  - winwintravel
---

# WinWinTravel frontend plan

## Deadline 

Deadline - 06.04.2024

## Goal

Наша цель - создать MVP сайта для букинга отелей.

Нужно что-бы пользователь мог зайти, найти отели по фильтрации/сортировке просмотретреть информацию об отеле и если он ему понравился - лайкнуть его

После лайков пользователь  должен иметь возможность сделать сравнение разных отелей между собой в большой таблице

MVP должен работать правильно на компьютере, то есть он может не иметь адаптива, но при этом быть полностью протестированным

А так-же сайт должен иметь автоматический збор статистики

### Зачем мы это делаем?

Это нам позволит нам собрать отзывы людей и понять на их основании куда двигаться проекту дальше

### Что должно быть

Все страницы должны иметь нужный функционал который описан ниже

Все страницы должны иметь дизайн как в макете

Все страницы должны быть протестрованны

## Основные блоки и задачи 

Фильтрация и сортировка
Получение данных офферов и их отображение
Лайки которые храняться на сервере
Дизлайки которые храняться на сервере
Показ лайкнутых офферов в таблице

Главная страница
Страница сравнения
Страница просмотра оффера
- Таб с информацией о отеле
- Таб с информацией о комнате
- Таб с локацией
- Таб с похожими офферами
- Таб с правилами
Страница просмотра оффера только лайкнутых
Настройка оффера
Возможность запроса персональной скидки

## Блоки приложения

### Statistic

Google statistic

### Global

У нас должны быть базовые иконки для фич

/ QUESTION: ? /
Мы ведь не будем писать капсом название всех груп. Возможно его нужно захардкодить?

### Header

Логотип, при нажатии на который идёт redirect на главную страницу

Share з показом основных ссылок

Notification - добавить feature in dev

Переход на страницу comparison если есть лайки
- Изменить иконку
- Убрать cursor pointer при наведении если нет елементов
- При клике если нет елементов - показывать tooltip сначала лайкните
- При наведении базовом показывать "Переход на страницу сравнения"

Изменение языка - добавить feature in dev
Profile - добавить feature in dev

Мини версия header которая будет так-же само закрепляться при scroll как и MainSearch

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на header
Сделать e2e тесты на header

### Footer

Отображение логотипа как в дизайне
Ссылки на нужные нам ресурсы
All rights reserved

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на footer
Сделать e2e тесты на footer

### Main Search

Возможность выбора destination
Возможность выбора дат
Возможность выбора количества постояльцев
Возможность выбора кастомных фильтров
Возможность выбора быстрых фильтров

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на mainSearch
Сделать e2e тесты на mainSearch

### Home page

Відображення офферів
Підзавантаження додаткових офферів через пагінацію
Данные которые мы отправляем должны так-же дублироваться в URLSearchParams. При обновлении страницы эти данные должны ставиться как данные по умолчанию
Можливість лайкати/дизлайкати оффери локально
Можливість лайкати/дизлайкати оффери через API
Карта на головній сторінці
Виділення оффера при кліці на тег карти
Сортування елементів

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на HomePage
Сделать e2e тесты на HomePage

### Room offer page

На этой странице должны отображаться результаты поиска
Если это первый заход на страницу - должен делаться запрос в API на получение данных
Данные которые мы отправляем должны храниться в URLSearchParams, как и на home page и при первом заходе на страницу мы должны делать запрос по ним

На странице должен быть функционал перемещенния по офферам + дополнительные запросы на получение если страница закончилась

На странице должен быть слайдер с картинками
Слайдер с картинками так-же должен иметь разные группы картинок которые он отображает

На странице должна быть краткая информация про оффер

На странице в краткой инфорации должна быть работающая кнопка открытия room offer configuration

На странице в краткой инфорации должна быть работающая кнопка открытия personal discount request

Должна быть кнопочка Reserve на которую нужно добавить in dev

Синхоронизированный дизайн с макетом

TODO:
Поменять таб комнаты и отеля местами 

Сделать тест-кейсы на страницу оффера
Сделать e2e тесты на страницу оффера

#### Таб комнаты

Отображание названия отеля и краткой информации о нём
Отображение фич комнаты сгрупированных по групам

Подсветка некоторых фич которая означает, что по ним можно клацнуть и откроется room offer configuration где это можно будет настраивать

Должна быть кнопочка Reserve на которую нужно добавить in dev

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на таб
Сделать e2e тесты на таб
#### Таб отеля

Отображение звёзд отеля
Отображение названия отеля
Отображение отзывов x/10 отеля
Краткое описание

Included фичи в виде текста

/ QUESTION: ? /
Отображение фич комнаты сгрупированных по групам

Маленькая карта с отображение позиции отеля

Должна быть кнопочка Reserve на которую нужно добавить in dev

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на таб
Сделать e2e тесты на таб

#### Таб локации

Отображение большой карты с местом нахождения отеля

Отображение фич которые имею группу LOCATION

Должна быть кнопочка Reserve на которую нужно добавить in dev

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на таб
Сделать e2e тесты на таб

#### Таб других комнат

Отображение похожих комнат на эту через дополнительный search запрос

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на таб
Сделать e2e тесты на таб

#### Таб правил

Отображение фич которые имею группу RULES_POLICIES_PAYMENT

Должна быть кнопочка Reserve на которую нужно добавить in dev

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на таб
Сделать e2e тесты на таб

### Room offer configuration

Он должен быть и открываться при клике на кнопку на room-offer
// TODO

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на room offer configuration
Сделать e2e тесты на room offer configuration

### Comparison table

Страница стравнения должна быть
В таблице должна отображаться информация о лайкнутых офферах взятых локально
В таблице должна отображаться информация о лайкнутых офферах взятых из сервера
Фичи должны быть отсортрованны
Должна быть сортировка внутри строки по option
Должна быть модалка для выключения/выключения фич которые должны отображаться
При горизонтальном скролле должны быть показанны иконки
- Отображение сортировок с иконками?
При клике на удаление оффера с таблицы у оффера должен сниматься лайк локально
При клике на удаление оффера с таблицы у оффера должен сниматься лайк на сервере
На странице должна быть возможность открыть карту
На странице должна быть карта
При клике на тег карты нужный столбец должен подсвечиваться

При клике на название отеля или комнаты - перессылка на страницу Room offer page где будут отображаться только лайкнутые

На большую выпадашку в comparison header добавить in dev
На кнопку в comparison добавить in dev

other:
- Некоторые фичи будут подсвечиваться
- При наведении на эти фичи будет показываться большой tooltip
- При клике - открывается room configuration где можно настраивать фичи

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на comparison table
Сделать e2e тесты на comparison table

### Request personal discount

Он должен быть и открываться при клике на кнопку на room-offer
// TODO

Синхоронизированный дизайн с макетом

Сделать тест-кейсы на request personal discount
Сделать e2e тесты на request personal discount

## Что нам нужно для MVP

Нам для релиза нужен approve от дизайнеров что всё красиво и чётко
А так-же нам нужен полностью протестированный базовый функционал

## Тестирование

Нам нужно иметь тест-кейсы на весь базовый функционал приложения

Документация что такое test case и примеры - link // IN DEV

Для e2e тестов мы будем использовать playwright

## Деплой

В чём проблема того, что есть сейчас? Проблема в том что учитывая скорость разработки деплои нужно сделать каждый день - два

Сейчас что-бы сделать деплой нужно закинуть ручками docker image на dockerhub и написать в be. Если я буду каждый день писать в be о том, что нужно передеплоить рано или поздно это всем надоест

Варианты решения:
1. Самый простой вариант. Можно это хостить на vercel, как я делал демки, обновляя каждый день - два
2. Сделать ci/cd. При каждом пуше в dev пересобираеться проект и делается deploy в какой-то dev-winwinjs.jstuffs.com или что-то такое
3. Сделать ci/cd не на dev, а на staged и обновлять ветку staged каждый день - 2, но ну такое
4. Подключить vercel напрямую?