---
title: "Control"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**Control** -- это базовый класс для описания элемента управления.

## Методы

### addClass()
Добавляет пользовательский `CSS` стиль к элементу управления.
```js
addClass(cssClass: string): void;
```
где:\
`cssClass` -- имя класса `CSS` стиля.

### removeClass()
Удаляет пользовательский `CSS` стиль из элемента управления.
```js
removeClass(cssClass: string): void;
```
где:\
`cssClass` -- имя класса `CSS` стиля.