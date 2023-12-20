---
title: "DeleteButtonExtension"
date: 2023-01-01T14:44:03+03:00
draft: false
---

**DeleteButtonExtension** -- расширение для удаления выделенных  на сцене объектов.\
По нажатию на кнопку `Удалить выбранные элементы` в панели инструментов или по нажатию клавиши `Delete` на клавиатуре расширение вызовет [delete](../../reference3d/Model#delete) метод модели со списком выделенных объектов.\
Непосредственным удалением объектов занимаются владельцы данных объектов. 
Для этого им необходимо подписаться на событие удаления [DELETE_OBJECTS_EVENT](../../reference3d/Events#Events3D). 
Также владелец объекта должен передать в модель фильтр для собственных удаляемых объектов - [addDeletionFilter](../../reference3d/Model#addDeletionFilter).\
При выделении объектов на сцене расширение проверяет, что все выбранные объекты соответствуют фильтрам удаления объектов с помощью метода [canDelete](../../reference3d/Model#canDelete) . 
Если соответствуют, то удаление разрешено -- можно удалить объекты нажатием кнопки либо нажатием клавиши `Delete`. 
В противном случае кнопка будет заблокированной, а нажатие клавиши `Delete` проигнорируется.

Расширение имеет имя `PilotWeb3D.DeleteButton`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/DeleteButton/DeleteButton.min.js"></script>
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