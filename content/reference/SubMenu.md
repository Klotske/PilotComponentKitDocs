---
title: "SubMenu"
draft: false,
weight: 12
---

**SubMenu** -- класс, создающий и управляющий выпадающим меню.

## Свойства
```js
controls: IControl[];
```
Массив элементов меню. Подробнее: [IControl](../IControl).

### selectedIndex : number
Выбранный элемент в списке.
```js
get selectedIndex(): number;
set selectedIndex(value: number);
```
По умолчанию: `-1`.

## Методы

### addControl()
Функция добавления элемента в список.
```js
addControl(control: IControl, index?: number): void;
```
где:\
`control` -- добавляемый элемент.\
`index` -- позиция в списке куда добавляется элемент, по умолчанию в конец.

### removeControl()
Функция удаления элемента из списка.
```js
removeControl(index?: number): void;
```
где:\
`index` -- позиция в списке откуда удаляется элемент, по умолчанию с конца.

### clearList()
Метод очищает список и массив controls.
```js
clearList(): void;
```

### changeElementByIndex()
Метод меняет указанный в списке элемент.
```js
changeElementByIndex(index: number, item: IControl): void;
```
где:\
`index` -- позиция элемента, который нужно заменить.\
`item` -- новый элемент.

### getListItemByIndex()
Метод возвращает элемент из списка по индексу.
```js
getListItemByIndex(index: number): Element;
```
где:\
`index` -- позиция элемента, который вернётся.

### getCountElements()
Метод возвращает количество элементов в списке.
```js
getCountElements(): number;
```

### fillList()
Метод добавляет элементы в список к уже существующим.
```js
fillList(controls: IControl[]): void;
```
где:\
`controls` -- новые элементы.