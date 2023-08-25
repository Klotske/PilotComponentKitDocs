---
title: "Toolbar"
draft: false
---

**Toolbar** -- Класс, описывающий панель инструментов.

## Методы

### changeToolbarPosition()
Меняет позицию тулбара с текущей на предоставленную.
```js
changeToolbarPosition(direction: string): void;
```

### changeToolbarContent()
Меняет порядок отображения контента в тулбаре.
```js
changeToolbarContent(content: string): void;
```

### addControl()
Добавляет элемент в тулбар.
```js
addControl(control: Control): void;
```
где:\
`control` -- объект типа Control.
Подробнее: <a href="../Control/">Control</a>.

### removeControl()
Удаляет элемент из тулбара.
```js
removeControl(id: string): void
```
где:\
`id` -- идентификатор элемента.