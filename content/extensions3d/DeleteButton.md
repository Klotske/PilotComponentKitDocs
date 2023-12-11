---
title: "DeleteButtonExtension"
date: 2023-01-01T14:44:03+03:00
draft: false
---

**DeleteButtonExtension** -- расширение для удаления селектированных объектов на сцене.\
По нажатию на кнопку `Удалить выбранные элементы` в тулбаре, или по нажатию клавиши `Delete` на клавиатуре, расширение вызовет [DeleteEvent](#DeleteEvent) со списком селектированных объектов.\
Непосредственным удалением объектов занимаются владельцы данных объектов, для этого им необходимо подписаться на событие удаления с помощью [addDeleteEventListener](#addDeleteEventListener). Также в этом методе владелец объекта должен передать фильтр для собственных удаляемых объектов - расширение вызовет [DeleteEvent](#DeleteEvent) только в том случае, если каждый из выбранных объектов соответствует хотя бы одному фильтру.\
При селектировании объектов на сцене расширение проверяет, что все выбранные объекты соответствуют фильтрам. Если соответствуют, то удаление разрешено - можно удалить объекты по нажатию кнопки либо при нажатии клавиши `Delete`. В противном случае, кнопка заблокирована, а нажатие клавиши `Delete` игнорируется.


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

### addDeleteEventListener() {#addDeleteEventListener}
Добавить подписку на событие удаления объектов со сцены.
```js
  addDeleteEventListener(listener: DeleteEventListener, filter: DeleteEventFilter): void;
```
где:

`listener` -- обработчик события удаления. Подробнее: [DeleteEventListener](#DeleteEventListener).\
`filter` -- фильтр объектов для удаления. Подробнее: [DeleteEventFilter](#DeleteEventFilter).


### removeDeleteEventListener()
Удалить подписку на событие удаления объектов со сцены.
```js
  removeDeleteEventListener(listener: DeleteEventListener): void;
```
где:

`listener` -- обработчик события удаления. Подробнее: [DeleteEventListener](#DeleteEventListener).

## DeleteEvent {#DeleteEvent}
Событие удаления объектов со сцены. 
```js
class DeleteEvent extends Event {
  deletedIds: PilotWeb3D.ModelElementIds[];
}
```
где:
`deletedIds` -- Идентификаторы объектов для удаления. Подробнее: [ModelElementIds](../../reference3d/modelelement/ModelElementIds).


## DeleteEventListener {#DeleteEventListener}
Обработчик события удаления.
```js
interface DeleteEventListener extends EventListener {
  (event: DeleteEvent): void;
}
```
где:

`event` -- событие удаления. Подробнее: [DeleteEvent](#DeleteEvent).

## DeleteEventFilter {#DeleteEventFilter}
Фильтр объектов для удаления. 
```js
interface DeleteEventFilter {
  (modelId: string, entityId: string): boolean;
}
```
где:

`modelId` -- идентификатор модели.\
`entityId` -- идентификатор элемента модели.\
Возвращает `true` для объектов которые можно удалить. В противном случае `false`.
