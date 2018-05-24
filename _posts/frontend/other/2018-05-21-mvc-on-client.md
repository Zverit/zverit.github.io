---
layout: post
title:  "Паттерн MVC на клиенте"
date: 2018-05-21 22:35:21 +0300
category: Frontend
author: "Artamoshkin Maxim"
image: "/assets/mvc-page-head.jpg"
image_alt: ""
tags: [Frontend, MVC, Pattern]
description: "Краткий обзор MVC паттерна в веб-разработке. Рассмотрены различия его использования сврерной и клиентской частью приложения."
---

MVC - паттерн разделения приложения на 3 основных компонента: модель (*Model*),  представление (*View*), контроллер (*Controller*).

MVC паттерн был впервые описан в 1978 году. Который изначально использовался для построения графических приложений.
Со временем этот паттерн перешел и в веб-приложения. Сначала он пришел на серверную сторону с такими фреймворками как Ruby and Rails и ASP.NET MVC Framework.
В конце концов стал применяться и на клиентской части, для управления сложностью и широтой функциональности.
На данный момент имеется иерархия моделей на базе MVC: MVC, MVP, MVVM.

 <!-- more -->

 {:.center}
![MVC иерархия](https://blog.zverit.com/assets/mvc_family.png)

Основной концепцией MVC являетя разделение обязанностей, то есть модель данных не имеет зависимости от бизнес-логики и логики представления.
На клиенте же происходит разделение данных (*модель*), от логики (*контроллер*), которая работает с этими данными, и HTML кода (*представление*), т.е. представления.

Стоит заметить, что паттерн имеет некоторые различия в применении в клиентском и серверном приложениях.

{:.center}
![MVC шаблон на сервере](https://blog.zverit.com/assets/server-mvc.png)

Как это выглядит для сервера: 
1. Контроллер обрабатывает запрос.
2. Контроллер обращается к модели за данными.
3. Модель получает данные из персистентного хранилища.
4. Модель отдает данные контроллеру.
5. Контроллер получает данные от модели.
6. Контроллер передает данные в представление.
7. Рендеринг представления и ответ на запрос от клиента.

Отличным примером использования шаблона MVC являются SPA приложения. Далее рассмотрим признаки MVC в типичном SPA приложении.

{:.center}
![MVC шаблон клиентского приложения](https://blog.zverit.com/assets/client-mvc.png)

Клиент:
1. Произошло событие от пользователя в окне браузера.
2. Обработка события контроллером.
3. Контроллер обращается к модели.
4. Модель запрашивает у сервера данные.
5. Модель получает данные и передает в контроллер.
6. Контроллер обрабатывает данные и передает в представление
7. Рендеринг и отображение в окне браузера.

Этот вариант реализации MVC подходит для SPA приложений, также существует вариант, с одним отличием, что клиент получает и отображает данные минуя котроллер. 

Опишем подробнее каждый из элементов паттерна.

### Модель (*Model*) ###
Модель содержит в себе данные, с которыми работает пользователь.
Существует два типа моделей:
- Модель предметной области - содержит все данные предметной области, а также операции, API для получения данных и логику работы с этими данными.
- Модель представления - данные которые передаются компонентом шаблону, для формирования представления.

### Контроллер (*Controller*) ###
Контроллер является связующей частью между моделью и представлением. Он содержит логику необходимую для представления модели и операций над ней.

Контроллер должен содержать логику:
- Для подготовки данных для представления
- Для обновления данных на основе взаимодействия с пользователем

Контроллер не должен: 
- Оперировать с DOM
- Долгосрочно хранить данные

### Представление (*View*) ###

View на клиенте отвечает за отображение данных в браузере. Представление содержит в себе разметку и логику для отображения.
Тем не менее оно не должно содержать сложную логику, которая должна быть в контроллерах, и логику манипляций с данными, которая относится к модели.
Содержание логики в шаблонах допустимо, но очень умеренно.

### Заключение ###

Многие предвещали смерть MVC на стороне клиента, но в настоящее время он снова обрел популярность.
Фреймворки Angular и Backbone - яркие его представители, благодаря которым MVC процветает на клиенте.
Останется ли MVC во фронтенде в будущем? Никто не знает, остается лишь только гадать.