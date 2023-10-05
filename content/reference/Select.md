---
title: "Select"
draft: false,
weight: 13
---

**Select** -- класс для создания списка выбора с полем.

## ISelectItem {#ISelectItem}
**ISelectItem** -- интерфейс, хранящий описание элемента списка. 

```js
export interface ISelectItem {
  // Свойство, хранящее текст элемента списка, который будет отображаться
  text: string;
  // Свойство, хранящее значение элемента списка, которое необходимо для работы списка
  value: string;
}
```

## Свойства

### disabled : boolean
Состояние для отключения списка.
```js
get disabled(): boolean;
set disabled(value: boolean);
```

### selectedIndex : number
Индекс выбранного элемента в списке.
```js
get selectedIndex(): number;
set selectedIndex(value: number);
```

### placeholder : string
Текст-подсказка поля выбора.
```js
get placeholder(): string;
set placeholder(value: string);
```

## Методы

### onChange()
Подписка на событие изменения выбранного в списке значения.
```js
onChange({ index: number, value: string }): void
```
где:\
`index` - индекс выбранного значения.\
`value` - значение элемента списка.

### createComponent()
Метод создает компонет и возвращает его DOM-представление.
```js
createComponent(): Element
```

### update()
Метод обновляет элементы списка.
```js
update(array: ISelectItem [], selectedIndex: number): void
```
где:\
`array` - массив новых элементов. Подробнее: [ISelectItem](#ISelectItem).\
`selectedIndex` - элемент, выбранный в новом списке.
