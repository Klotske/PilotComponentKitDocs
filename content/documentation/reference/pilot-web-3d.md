---
title: "PilotWeb3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**PilotWeb3D** -- это пространство имён для взаимодействия верхнего уровня с компонентом Pilot.Web.3D. Используется в первую очередь для инициализации компонента.

## Методы

### Initializer(options, callback)

Статический метод для инициализации компонента Pilot.Web.3D. Все методы работы с компонентом следует использовать после вызова этого метода.

**Параметры**

```js
  options: Object;
```
`options` содержит настройки для инициализации компонента.

```js
  callback: () => void;
```
`callback` -- метод обратного вызова. Вызывается, когда завершится инициализация компонента.

Пример:

```js
let options = {};
var myCallback = function() {
   console.log("initialization complete, creating the viewer...");
};
PilotWeb3D.Initializer(options, myCallback);
```

### CreateViewer(container)

Метод создания просмотрщика BIM-моделей.

**Параметры**

```js
  container: HTMLElement;
```
HTML элемент, в котором необходимо создать 3D просмотрщик.

Пример:
```js
let htmlDiv = document.getElementById('pilotViewer');
let viewer = PilotWeb3D.CreateViewer(htmlDiv);
```