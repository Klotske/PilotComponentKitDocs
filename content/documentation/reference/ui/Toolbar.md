---
title: "Toolbar"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Toolbar

Базовый класс управления панелью инструментов компонента. Класс расширяет возможности класс `Control`.

## Методы

#### addControl()
Добавляет кнопку в панель инструментов.
```js
addControl(control: Control): void;
```
где:
`contorl` - экземпляр элемента управления.

#### removeControl()
Добавляет кнопку в панель инструментов.
```js
removeControl(id: string): void;
```
где:
`id` - идентификатор элемента управления.

#### addClass()
Добавляет пользовательский `CSS` стиль к элементу управления.
```js
addClass(cssClass: string): void;
```
где:
`cssClass` - имя класса `CSS` стиля.

#### removeClass()
Удаляет пользовательский `CSS` стиль из элемента управления.
```js
removeClass(cssClass: string): void;
```
где:
`cssClass` - имя класса `CSS` стиля.

