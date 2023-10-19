---
title: "Checkbox"
draft: false,
weight: 14
---

**Checkbox** -- класс для создания поля проверки.

## Свойства

### checked : boolean
Состояние для снятия/установки галочки.
```js
get checked(): boolean;
set checked(value: boolean);
```

### disabled : boolean
Состояние для отключения поля проверки.
```js
get disabled(): boolean;
set disabled(value: boolean);
```

### label : HTMLElement
HTML представление текста-подсказки.
```js
get label(): HTMLElement;
```

## Методы

### onChange()
Подписка на событие изменения значения.
```js
onChange(value: boolean): void {}
```
где:\
`value` - значение элемента, установлена галочка или нет.

### createElement()
Создает и возвращает HTML представление элемента поля проверки.
```js
createElement(): Element
```