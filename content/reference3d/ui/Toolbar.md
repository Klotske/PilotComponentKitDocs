---
title: "Toolbar"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**Toolbar** -- это базовый класс управления панелью инструментов компонента. Класс расширяет возможности класса `Control`.

## Методы

### addControl()
Метод добавляет кнопку в панель инструментов.
```js
addControl(control: Control): void;
```
где:\
`control` -- экземпляр элемента управления.

### removeControl()
Метод добавляет кнопку в панель инструментов.
```js
removeControl(id: string): void;
```
где:\
`id` -- идентификатор элемента управления.

### addClass()
Метод добавляет пользовательский `CSS` стиль к элементу управления.
```js
addClass(cssClass: string): void;
```
где:\
`cssClass` -- имя класса `CSS` стиля.

### removeClass()
Метод удаляет пользовательский `CSS` стиль из элемента управления.
```js
removeClass(cssClass: string): void;
```
где:\
`cssClass` -- имя класса `CSS` стиля.

