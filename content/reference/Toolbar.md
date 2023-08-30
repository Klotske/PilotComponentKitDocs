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

### changeToolbarContentAlignment()
Меняет порядок отображения контента в тулбаре.
```js
changeToolbarContentAlignment(content: ToolbarContentAlignment): void;
```
где:\
`content` -- порядок отображения контента внутри тулбара. Подробнее: [ToolbarContentAlignment](../ViewerConfiguration#ToolbarContentAlignment).

### addControl() {#addControl}
Добавляет элемент в тулбар.
```js
addControl(control: Control, index: number = 0): void;
```
где:\
`control` -- объект типа Control. Подробнее: <a href="../Control/">Control</a>.\
`index` -- индекс.

### addDropdown() {#addDropdown}
Добавляет элемент в тулбар.
```js
addDropdown(id: string, tooltip: string, positionIndex: number = 0, selectedIndex: number, dropdownEmitter: Control, controls: Control [], 
    itemClicked: ({ index, event}: {
    index: number,
    event: Event
  }) => void): void;
```
где:\
`id` -- идентификатор элемента.\
`tooltip` -- всплывающая подсказка на элементе.\
`positionIndex` -- позиция компонента в тулбаре.\
`selectedIndex` -- выбранный в выпадающем меню пункт, если ничего не выбрано передавать -1.\
`dropdownEmitter` -- элемент-триггер для по клику на который откроется выдающее меню.\
`controls` -- пункты меню.\
`itemClicked` -- колбек функция-обработчик клика по пункту меню.\
`index` - номер пункта меню по которому был произведён клик.\
`event` - событие клика.


### removeControl()
Удаляет элемент из тулбара.
```js
removeControl(id: string): void
```
где:\
`id` -- идентификатор элемента.