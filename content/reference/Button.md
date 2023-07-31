---
title: "Button"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**Button** -- это класс для элемента управления **Кнопка**. Класс расширяет возможности базового класса `Control`.
Подробнее: <a href="../Control/">Control</a>.

## Свойства

### caption
Задаёт или получает имя кнопки.
```js
caption: string;
```
### clickAction
Слушает нажатия на кнопку.
```js
clickAction: EventListener;
```

{{< hint type="note" title="Примечание">}}
Метод еще не доработан и может быть изменен в следующих версиях.
{{< /hint >}}

## Методы 

### addClass()
Метод добавляет пользовательский `CSS` стиль к элементу управления.
```js
addClass(cssClass: string): void;
```
где:
`cssClass` -- имя класса `CSS` стиля.

### removeClass()
Метод удаляет пользовательский `CSS` стиль из элемента управления.
```js
removeClass(cssClass: string): void;
```
где:
`cssClass` - имя класса `CSS` стиля.

### setIsChecked()
Метод позволяет установить стиль выбора для кнопки.
```js
setIsChecked(value: boolean): void;
```
где:
`value` - селектирована кнопка или нет.

### setIcon()
Метод позволяет установить иконку для кнопки.
```js
setIcon(iconClassName: string): void;
```
где:
`iconClassName` - имя класса `CSS` стиля, где содержится иконка.

### setFromSvgTemlate()
Метод позволяет установить иконку кнопки в виде svg
```js
setFromSvgTemlate(template: string): void
```
где:
`template` - svg элемент иконки в виде строки.
