---
title: "Control"
date: 2023-05-29T14:44:03+03:00
draft: false
---

**Control** -- это класс для создания контрола панели инструментов.

## Свойства

### container
```js
container: HTMLElement;
```
Получает HTML елемент контрола.

## Методы

### addClass()
Добавляет класс к элементу.
```js
addClass(cssClass: string): void
```
где:
`cssClass` -- имя класса.

### removeClass()
Удаляет класс у элемента.
```js
removeClass(cssClass: string): void
```
где:
`cssClass` -- имя класса.

### getId()
Получить идентификатор контрола.
```js
getId(): string
```

### setToolTip()
Задать подсказку для контрола
```js
 setToolTip(tooltipText: string): void
```
где:
`tooltipText` -- текст для всплывающей подсказки.