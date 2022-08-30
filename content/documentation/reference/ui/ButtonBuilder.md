---
title: "ButtonBuilder"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## ButtonBuilder

Класс строителя элемента управлени - кнопки.

## Методы

#### withCaption()
Задает подпись для кнопки.

```js
withCaption(caption: string) : ButtonBuilder
```
где:
`caption` - подпись кнопки.
`return ButtonBuilder` - возвращает класс строителя кнопки.

#### withIcon()
Задает иконку для кнопки.

```js
withIcon(icon: string): ButtonBuilder
```
где:
`icon` - имя класс `CSS` с иконкой.
`return ButtonBuilder` - возвращает класс строителя кнопки.

#### withClickAction()
Задает колбэк для обработки события нажатия на кнопку.

```js
withClickAction(action: EventListener) : ButtonBuilder;
```
где:
`action` - обработчик события нажатия кнопки.
`return ButtonBuilder` - возвращает класс строителя кнопки.

{{< hint type=[note]>}}
Метод еще не доработан и может быть изменен в следующих версиях.
{{< /hint >}}

#### withIsChecked()
Задает стиль для нажатой кнопки.

```js
withIsChecked(value: boolean): ButtonBuilder;
```
где:
`value` - обработчик события нажатия кнопки.
`return ButtonBuilder` - возвращает класс строителя кнопки.