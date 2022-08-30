---
title: "PilotWeb2D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## PilotWeb2D

Это верхний уровень для взаимодействия с компонентом Pilot.Web.2D

## Методы

### Initializer(options, callback)

Статический метод для инициализации 2D компонента. Все методы работы с компонентом следует использовать после вызова этого метода.

#### Параметры

```js
  options: Object;
```
`options` содержит настройки для инициализации компонента.

```js
  callback: () => void;
```
`callback` - метод обратного вызова, вызывается когда завершится инициализация компонента.

Пример:

```js
let options = {};
var myCallback = function() {
   console.log("initialization complete, creating the viewer...");
};
PilotWeb2D.Initializer(options, myCallback);
```

### CreateViewer(container)

Метод создания 2D просмотрщика.

#### Параметры

```js
  container: HTMLElement;
```
HTML элемент, в котором необходимо создать 2D просмотрщик.