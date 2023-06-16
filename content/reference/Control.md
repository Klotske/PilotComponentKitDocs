---
title: "Control"
date: 2023-05-29T14:44:03+03:00
draft: false
---

**Control** -- это класс для создания контрола панели инструментов

## Свойства

### container
```js
container: HTMLElement;
```
Получает HTML елемент контрола.

## Методы

### addClass()
```js
addClass(cssClass: string): void
```
Добавить класс `css`

### removeClass()
```js
removeClass(cssClass: string): void
```
Удалить класс `css`

### getId()
```js
getId(): string
```
Получить идентификатор контрола.

### setToolTip()
```js
 setToolTip(tooltipText: string): void
```
Задать подсказку для контрола