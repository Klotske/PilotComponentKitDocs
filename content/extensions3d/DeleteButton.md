---
title: "DeleteButtonExtension"
date: 2023-01-01T14:44:03+03:00
draft: false
---

**DeleteButtonExtension** -- расширение для удаления селектированных объектов на сцене.\
По нажатию на кнопку `Удалить выбранные элементы` в тулбаре, или по нажатию клавиши `Delete` на клавиатуре, расширение вызовет ивент `RENDER_DELETE_EVENT` со списком селектированных объектов.\
Непосредственным удалением объектов занимаются владельцы данных объектов, для этого им необходимо подписаться на событие `RENDER_DELETE_EVENT` в событиях компонента. 
Подробнее: [EventTypes](../../reference3d/Events/#Events3D), [Viewer3D.events](../../reference3d/Viewer3D/#events).

Расширение имеет имя `PilotWeb3D.DeleteButton`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/23.0.10/extensions/DeleteButton/DeleteButton.min.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.DeleteButton");
```

## Методы

### activate()
Активировать расширение.
```js
activate(): void;
```
### deactivate()
Деактивировать расширение.
```js
deactivate(): void;
```