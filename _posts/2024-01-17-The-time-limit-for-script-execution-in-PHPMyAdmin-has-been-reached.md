---
title: "Достигнут временной лимит выполнения скрипта в PHPMyAdmin"
tags: 
  - phpMyAdmin
---


Сегодня загружал довольно большой дамп в базу MySQL используя PHPMyAdmin.

Так вот, при длительном импорте вывалилась ошибка: Достигнут временной лимит выполнения скрипта.:hankey:
Как выясняется, настройки php.ini тут не причём. В конфиге самого phpMyAdmin-а кроется жёсткое ограничение времени
работы скриптов. Увеличим!:monkey_face:(shown below)

Идем в файл конфигурации: /usr/share/phpMyAdmin/libraries/config.default.php

Следующей командой для Ubuntu 22.04, откроем этот файл:
```
sudo nano /usr/share/phpmyadmin/libraries/config.default.php
```
Находим строку:
```
$cfg[‘ExecTimeLimit’] = 300;
```
Меняем на:
```
$cfg[‘ExecTimeLimit’] = 3600;
```
часа вполне достаточно для выполнения, а если не хватит — phpMyAdmin продолжит импорт с того места, где остановился. :metal: