---
title: "GizmoControl"
draft: false
weight: 9
---

## GizmoControl {#GizmoControl}
**GizmoControl** -- контроллер, помещаемый на сцену, позволяющий изменять положение объектов на сцене.\
Экземпляр можно создать самостоятельно, либо можно получить реализацию по умолчанию, с помощью [GizmoBuilder](../GizmoBuilder).

В контроллер [можно добавить](#addAxis) собственные реализации осей. 
Для того, чтобы создать свою ось контроллера, необходимо унаследоваться от класса [GizmoAxis](../GizmoAxis).

```js
export class GizmoControl extends THREE.Object3D {
  constructor(camera: THREE.Camera, navAgent: INavigationAgent);
  attachTo(object: THREE.Object3D, asChild = false): void;
  detach(): void;
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

## attachTo()
Метод связывает `GizmoControl` и объект на сцене. Контрол привязывает своё положение к положению объекта, а также, манипуляции над `GizmoControl` начинают влиять на положение связанного объекта.
```js
attachTo(object: THREE.Object3D, asChild = false): void;
```
где:\
`object` -- Объект привязки.\
`asChild` -- Параметр указывает, добавить ли `GizmoControl` дочерним элементом к объекту. Не обязательный параметр, по умолчанию `false`.\
 Если `asChild` равен `true`, то `GizmoControl` не нужно добавлять на сцену вручную, он появится на той же сцене, где находится родительский объект. В противном случае `GizmoControl` нужно вручную добавить на сцену.

## detach()
Метод открепляет `GizmoControl` от объекта привязки, если привязка существует.
```js
detach(): void;
```

## addAxis() {#addAxis}
Метод добавляет новую ось для манипуляции в `GizmoControl`.
```js
  addAxis(axis: GizmoAxis): void;
```
где:\
`axis` -- ось контроллера. Подробнее: [GizmoAxis](../GizmoAxis).

## dispose()
Метод освобождает ресурсы, выделенные контроллеру, разрывает привязку, удаляет `GizmoControl` со сцены.
```js
dispose(): void;
```