---
title: "Что такое скаффолдинг в Ruby On Rails?"
category:
 - Ruby
tags:
 - Ruby on Rails
---

Возможно, вы изучаете Rails и считаете, что вам нужно создать «шаблоны» для запуска вашего приложения Rails…

Однаако, есть легкий способ!:hugs:

Вы можете сделать это с помощью команды `rails g scaffold`.

### Но что такое scaffold?

«Scaffold — это временная конструкция, используемая для поддержки рабочей бригады при строительстве, 
обслуживании и ремонте зданий, мостов и всех других искусственных сооружений». - Википедия

А как это в Rails :

Скаффолд — это набор автоматически генерируемых файлов, которые формируют базовую структуру проекта Rails.

Эти файлы включают в себя :

Контроллер
Модель
Представления для каждого стандартного действия контроллера (индекс, редактирование, удаление, создание)
Новый маршрут.

#### И миграции для подготовки вашей базы данных.

Давайте посмотрим пример!

Как использовать команду Rails Scaffold
Пример создания проекта веб-сайта о книгах будет выглядеть так.

```
rails g scaffold books
```
Вы должны увидеть прокручивающийся большой текст, в котором подробно описаны создаваемые файлы.

В этом примере создается :

АBooksController
Модель Book_
В ваш файл resources :booksдобавлен новый маршрут.config/routes.rb
Набор файлов , связанных с тестированием.
Шаблоны app/views/books(всего пять)

:sunglasses: Это много чего.

Если вы хотите удалить этот каркас, сразу после его создания, вы можете использовать следующую команду.
```
rails d scaffold books
```
Где «d» означает «уничтожить».

Имейте в виду, что это приведет к УДАЛЕНИЮ файлов , созданных в процессе создания шаблонов.

Прежде чем вы сможете использовать шаблонный код, вам необходимо выполнить миграцию, чтобы обновить схему
базы данных.

Используйте команду `rails db:migrate`.

Если сообщений об ошибках не появляется, все готово! У вас есть базовая структура для вашего нового приложения
Rails или для новой функции, для которой требуется новая модель, представления и соответствующий контроллер.

Запустите: `rails server`.

Откройте браузер, [localhost:3000/books](localhost:3000/books) и вы увидите результаты!

### Тоже, но с дополнительными полями

Ваша модель получает только поля временных меток, а это означает, что единственная информация,
которую вы можете записать о своих книгах (или о любой модели, с которой вы работаете),
— это время, когда они были созданы или обновлены.

Вот как создать каркас с дополнительными полями :
```
rails g scaffold books title:string author:string publication_year:integer
```
Если вы создадите каркас таким образом, у вас будет 3 поля для работы.

Название, автор и год издания.

Это немного интереснее, чем просто иметь временные метки базы данных.

#### Кстати.

Это тот же синтаксис, который мы используем для создания миграций с помощью rails g migration.

### Генерация конкретных компонентов

Скаффолд создаёт вещи, которые вам, возможно, не нужны или не нужны прямо сейчас.

Вы можете создавать отдельные компоненты, такие как контроллеры, используя команду rails g (g для генерации).

Примеры :
```
rails g controller Fruit
rails g model Fruit name:string color:string(создает модель + миграцию)
rails g migration CreateBook title:string year:integer(создает только миграцию)
```

Одним из больших преимуществ использования команды формирования шаблонов является то, что все файлы создаются
с использованием правильных соглашений об именах, что позволяет избежать странных сообщений об ошибках. 
Это также избавляет вас от необходимости создавать эти файлы вручную.

#### Кстати…

Хорошей практикой считается удаление автоматически созданных файлов, которые вы не планируете использовать. 
Поэтому после использования генератора, такого как «g Controller», просмотрите список созданных файлов и удалите 
те, которые вам не нужны.

Спасибо за прочтение! :wave: