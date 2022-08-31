---
title: "PilotWeb3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

`PilotWeb3D` -- это пространство имён верхнего уровня для взаимодействия с компонентом **Pilot.Web.3D**.

## Методы

#### Initializer()

Метод для инициализации компонента Pilot.Web.3D. Все методы работы с компонентом следует использовать после вызова этого метода.

```js
type InitializeSuccessCallback = () => void;
function Initializer(options, callback: InitializeSuccessCallback): void;
```
где:
`options` -- содержит настройки для инициализации компонента.
`callback` -- метод обратного вызова. Вызывается, когда завершится инициализация компонента.

Пример:

```js
let options = {};
var myCallback = function() {
   console.log("initialization complete, creating the viewer...");
};
PilotWeb3D.Initializer(options, myCallback);
```

#### CreateViewer()

Создает экземпляр компонента для просмотра документов.

```js
function CreateViewer(container: HTMLElement) : GuiViewer3D;
```
где:
`container` -- HTML элемент, в котором создается компонент.

Пример:
```js
let htmlDiv = document.getElementById('pilotViewer');
let viewer = PilotWeb3D.CreateViewer(htmlDiv);
```