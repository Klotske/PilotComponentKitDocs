---
title: "ModelPartGizmo"
draft: false
weight: 1
---

**ModelPartGizmo** -- расширение, которое позволяет изменять положение частей модели с помощью гизмо на сцене.
При включении редактирования - [setEditMode](#setEditMode), расширение блокирует взаимодействие со всеми частями модели, кроме редактируемой. Задать редактируемую часть модели можно методом [setEditModelPartId](#setEditModelPartId). При клике по элементу модели на сцене, в точке клика появится гизмо, с помощью которого можно изменить положение части модели. Событие изменения положения части модели и событие изменения режима редактирования можно отслеживать с помощью диспетчера событий расширения [events](#events).

Расширение имеет имя `PilotWeb3D.ModelPartGizmo`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/ModelPartGizmo/ModelPartGizmo.min.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
await viewer.extensionsLoader.loadExtension("PilotWeb3D.ModelPartGizmo");
```

## Поля
## events {#events}
Диспетчер событий расширения.
Список типов событий расширения: [ModelPartGizmoEventMap](#ModelPartGizmoEventMap).
```js
readonly events: IEventsDispatcher;
```
Подробнее: [IEventsDispatcher](../../reference/EventsDispatcher).

## Методы

### activate()
Метод включает расширение.
```js
activate(): void;
```

### deactivate()
Метод выключает расширение.
```js
deactivate(): void;
```

### isEdited()
Метод возвращает состояние редактирования: `true` если в данный момент редактирование активно, в противном случае `false`.
```js
isEdited(): void;
```

### setEditMode() {#setEditMode}
Метод задает состояние редактирования.
```js
setEditMode(value: boolean): void;
```
где:\
`value` - значение требуемого состояния: `true` чтобы включить редактирование, `false` чтобы выключить.

### getEditModelPartId() {#getEditModelPartId}
Метод возвращает идентификатор редактируемой части модели.
```js
getEditModelPartId(): string | undefined;
```

### setEditModelPartId() {#setEditModelPartId}
Метод задает идентификатор редактируемой части модели. Если переданный идентификатор части модели не совпадает с идентификатором редактируемой в данный момент части модели, то редактирование сбрасывается и применяется новый идентификатор.
```js
setEditModelPartId(value: string): void;
```
где:\
`value` - идентификатор части модели.

## ModelPartGizmoEventMap {#ModelPartGizmoEventMap}
События расширения.
```js
interface ModelPartGizmoEventMap {
  'EditModelPartChanged' : Event,
  'ModelPartPositionChanged' : PositionChangedEvent,
}
```
### EditModelPartChanged {#EditModelPartChanged}
```js
  'EditModelPartChanged' : Event;
```
Событие возникает при изменении состояния редактирования и (или) изменении идентификатора редактируемой части модели.

### ModelPartPositionChanged
```js
  'ModelPartPositionChanged' : PositionChangedEvent; 
```
Событие возникает при изменении положения части модели - при отпускании оси гизмо после перетаскивания. 
 

```js
class PositionChangedEvent extends Event {
  modelPartId: string;  // идентификатор части модели
  placement: THREE.Matrix4Tuple | number[]; // новое положение части модели
  // матрица трансформации в глобальном пространстве, 4х4 - row-major order
}
```