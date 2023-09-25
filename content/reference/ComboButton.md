---
title: "ComboButton"
draft: false,
weight: 11
---

**ComboButton** -- класс, управляющий кнопкой с выпадающим списком.

## Свойства

### subMenu
Возвращает объект SubMenu. Подробнее: [SubMenu](../SubMenu).
```js
get subMenu(): SubMenu;
```

## Методы

### onClick()
Функция для обработчика клика на кнопку раскрывающегося меню.
```js
onClick = function(event: PointerEvent): void;
```
где:\
`event` -- событие клика на кнопку.

### setText()
Метод позволяет установить текст кнопки.
```js
setText(text: string): void;
```
где:\
`text` - текст, который будет отображать кнопка.

### setFromSvgTemlate()
Метод позволяет установить иконку кнопки в виде svg
```js
setFromSvgTemlate(template: string): void
```
где:\
`template` - svg элемент иконки в виде строки.