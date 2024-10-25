---
title: "GizmoControl"
draft: false
weight: 9
---

**GizmoEventMap** -- события `GizmoControl`. Расширяют события `ViewObjectEventMap`. Подробнее: [ViewObjectEventMap](../../render/ViewObject).
```js
export interface GizmoEventMap extends ViewObjectEventMap {
  // событие изменения активной оси гизмо
  activeAxisChanged: { isAxisActive: boolean; };
}
```

## GizmoControl {#GizmoControl}
**GizmoControl** -- контроллер, прикрепляемый к 3D-объекту на сцене и управляющий его положением.

Прикрепляемый к объекту контроллер может быть размещён на сцене как независимо, так и быть добавлен как дочерний элемент к 3D-объекту. Подробнее: .[attachTo()](#attachTo).\
По умолчанию `GizmoControl` помещается в начало координат локального пространства объекта привязки. Перемещение, вращение и масштабирование осуществляется относительно положения `GizmoControl`. Задать смещение `GizmoControl` относительно объекта привязки можно с помощью метода .[updateGizmoOffset()](#updateGizmoOffset).

В контроллер [можно добавить](#addAxis) собственные реализации осей. 
Для того, чтобы создать свою ось контроллера, необходимо унаследоваться от класса [GizmoAxis](../GizmoAxis).

Экземпляр можно создать самостоятельно, либо можно получить реализацию по умолчанию с помощью [GizmoBuilder](../GizmoBuilder).

```js
export class GizmoControl extends THREE.Object3D {
  constructor(camera: THREE.Camera, navAgent: INavigationAgent);
  attachTo(object: THREE.Object3D, asChild = false): void;
  detach(): void;
  updateGizmoOffset(position?: THREE.Vector3, quaternion?: THREE.Quaternion): void;
  addAxis(axis: GizmoAxis): void;
  dispose(): void;
}
```

## Конструктор
```js
  constructor(camera: THREE.Camera, navAgent: INavigationAgent);
```
где:\
`camera` - камера, используемая на сцене. Подробнее: [THREE.Camera](https://threejs.org/docs/#api/en/cameras/Camera).\
`navAgent` - агент навигации. Подробнее: [INavigationAgent](../../navigation/INavigationAgent).\
Камеру и агент навигации можно получить из [INavigation](../../navigation/INavigation).

```js
//Пример создания:
const camera = PilotWeb3D.ViewerInstance.navigation.getCamera();
const navAgent = PilotWeb3D.ViewerInstance.navigation.getNavigationAgent();
const gizmoControl = new PilotWeb3D.GizmoControl(camera, navAgent);
```

## Методы

## attachTo() {#attachTo}
Метод прикрепляет `GizmoControl` к 3D-объекту на сцене. Контрол привязывает своё положение к положению объекта, а также, манипуляции над `GizmoControl` начинают влиять на положение связанного объекта.\
Если `GizmoControl` добавляется как дочерний объект, то по умолчанию `GizmoControl` помещается в точку начала координат в локальном пространстве объекта привязки. Для смещения `GizmoControl` относительно объекта привязки используется метод .[updateGizmoOffset()](#updateGizmoOffset).
```js
attachTo(object: THREE.Object3D, asChild = false): void;
```
где:\
`object` -- Объект привязки.\
`asChild` -- Параметр указывает, добавить ли `GizmoControl` дочерним элементом к объекту. Необязательный параметр, по умолчанию: `false`.\
 Если `asChild` равен `true`, то `GizmoControl` не нужно добавлять на сцену вручную. Он будет автоматически размещён на той же сцене что и родительский объект. В противном случае `GizmoControl` нужно вручную добавить на нужную сцену и задать необходимые координаты.

## detach()
Метод открепляет `GizmoControl` от объекта привязки, если привязка существует.
```js
detach(): void;
```

## updateGizmoOffset() {#updateGizmoOffset}
Метод устанавливает смещение и вращение `GizmoControl` относительно объекта привязки.
```js
  updateGizmoOffset(position?: THREE.Vector3, quaternion?: THREE.Quaternion): void;
```
где:\
`position` -- позиция `GizmoControl` в локальных координатах объекта привязки. Необязательный параметр. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).\
`quaternion` -- вращение `GizmoControl` в локальных координатах объекта привязки. Необязательный параметр. Подробнее: [THREE.Quaternion](https://threejs.org/docs/#api/en/math/Quaternion).

## addAxis() {#addAxis}
Метод добавляет новую ось для манипуляции в `GizmoControl`.
```js
  addAxis(axis: GizmoAxis): void;
```
где:\
`axis` -- ось контроллера. Подробнее: [GizmoAxis](../GizmoAxis).

## dispose()
Метод освобождает выделенные контроллеру ресурсы, разрывает привязку, удаляет `GizmoControl` со сцены.
```js
dispose(): void;
```