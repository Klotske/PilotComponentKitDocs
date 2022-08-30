---
title: "ToolbarBuilder"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## ToolbarBuilder

Класс создателя панели инструментов.

## Методы

#### addButton()
Добавляет кнопку в панель инструментов.

```js
addButton(id: string) : ButtonBuilder;
```
где:
`id` - идентификатор нового элемента управления.
`ButtonBuilder` - конструктор для кнопки.

#### removeItem()
Удаляет элемент управления из панели инструментов.
```js
removeItem(id: string): void;
```
где:
`id` - идентификатор элемента управления.
