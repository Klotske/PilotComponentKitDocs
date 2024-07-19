---
title: "PilotWeb2D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

`PilotWeb2D` -- это пространство имён верхнего уровня для взаимодействия с компонентом **PilotWeb2D**.

## Методы

#### Initializer()

Метод для инициализации компонента **PilotWeb2D**. Все методы работы с компонентом следует использовать после вызова этого метода.

```js
type InitializeSuccessCallback = () => void;
function Initializer(options, callback: InitializeSuccessCallback): void;
```
где:\
`options` -- содержит настройки для инициализации компонента.
`callback` -- метод обратного вызова. Вызывается, когда завершится инициализация компонента.

Пример:

```js
let options = {};
let myCallback = function() {
   console.log("initialization complete, creating the viewer...");
};
PilotWeb2D.Initializer(options, myCallback);
```

#### CreateViewer()

Создает экземпляр компонента для просмотра документов.

```js
function CreateViewer(container: HTMLElement) : GuiViewer2D;
```
где:\
`container` -- HTML элемент, в котором создается компонент.

Пример:
```js
let htmlDiv = document.getElementById('pilotViewer');
let viewer = PilotWeb2D.CreateViewer(htmlDiv);
```