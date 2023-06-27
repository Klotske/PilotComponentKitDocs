---
title: "Control"
draft: false
---

**Control** -- базовый класс для создания UI элементов.

## Методы

### addClass()
Добавляет класс к элементу.
```js
addClass(cssClass: string): void;
```
где:
`cssClass` -- строка с названием класса.

### removeClass()
Удаляет класс с элемента.
```js
removeClass(cssClass: string): void;
```
где:
`cssClass` -- строка с названием класса.

### getId()
Возвращает id элемента.
```js
getId(): string;
```

### setToolTip()
Устанавливает текст всплывающей подсказки.
```js
setToolTip(tooltipText: string): void;
```
где:
`tooltipText` -- текст для всплывающей подсказки.