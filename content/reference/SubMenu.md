---
title: "SubMenu"
draft: false,
weight: 12
---

**SubMenu** -- класс, создающий и управляющий выпадающим меню.

## Свойства
```js
readonly controls: IControl[];
```
Массив элементов меню. Подробнее: [IControl](../IControl).

### selectedIndex : number
Индекс выбранного элемента.
```js
get selectedIndex(): number;
set selectedIndex(value: number);
```
По умолчанию: `-1`.

## Методы

### addControl()
Функция добавляет элемент управления.
```js
addControl(control: IControl, index?: number): void;
```
где:\
`control` -- добавляемый элемент управления.\
`index` -- позиция в списке куда добавляется элемент, по умолчанию в конец.

### removeControl()
Функция удаляет элемент управления из списка.
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

### changeControl()
Метод меняет указанный в списке элемент управления.
```js
changeControl(control: IControl, index: number): void;
```
где:\
`index` -- позиция элемента, который нужно заменить.\
`control` -- новый элемент управления.

### getControlsCount()
Метод возвращает количество элементов управления в списке.
```js
getControlsCount(): number;
```