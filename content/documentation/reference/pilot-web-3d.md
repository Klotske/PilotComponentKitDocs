---
title: "PilotWeb3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## PilotWeb3D

Это верхний уровень для взаимодействия с компонентом Pilot.Web.3D

## Методы

### Initializer(options, callback)

Статический метод для инициализации 3D компонента. Все методы работы с компонентом следует использовать после вызова этого метода.

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
PilotWeb3D.Initializer(options, myCallback);
```

### CreateViewer(container)

Метод создания 3D просмотрщика.

#### Параметры

```js
  container: HTMLElement;
```
HTML элемент, в котором необходимо создать 3D просмотрщик.