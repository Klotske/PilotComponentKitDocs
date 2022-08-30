---
title: "Button"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Button

Класс для элемента управления - кнопка. Класс расширяет возможности базового класс `Control`.

## Свойства

#### caption
Задать или получить имя кнопки.
```js
caption: string;
```
#### clickAction
Слушатель нажатия на кнопку.
```js
clickAction: EventListener;
```

{{< hint type=[note]>}}
Метод еще не доработан и может быть изменен в следующих версиях.
{{< /hint >}}


## Методы 

#### addClass()
Добавляет пользовательский `CSS` стиль к элементу управления.
```js
addClass(cssClass: string): void;
```
где:
`cssClass` - имя класса `CSS` стиля.

#### removeClass()
Удаляет пользовательский `CSS` стиль из элемента управления.
```js
removeClass(cssClass: string): void;
```
где:
`cssClass` - имя класса `CSS` стиля.

#### setIsChecked()
Установить стиль выбора для кнопки.
```js
setIsChecked(value: boolean): void;
```
где:
`value` - селектирована кнопка или нет.


#### setIcon()
Установить иконку для кнопки.
```js
setIcon(iconClassName: string): void;
```
где:
`iconClassName` - имя класса `CSS` стиля, где содержится иконка.
