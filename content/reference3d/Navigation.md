---
title: "INavigation"
draft: false
weight: 9
---

**INavigation** -- интерфейс, позволяющий взаимодействовать с навигацией на сцене.

```js
export interface INavigation {
  registerEventHandler(navEventHandler: NavigationEventHandler): void;
  unregisterEventHandler(navEventHandler: NavigationEventHandler): void;
  setActive(nvEventHandlerName: string, isActive: boolean): void;
  getActiveNavigation(): NavigationEventHandler;
  setDefaultNavigation(): void;
  setCameraPosition(params: CameraPosition): void;
  getCameraPosition(): CameraPosition;
  getCamera(): THREE.Camera;
  fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean): void;
  setPivotPoint(point: Point3): void;
  getPivotPoint(): Point3;
  resetPivotPoint(): void;
}
```

## Методы

### registerEventHandler()
Метод позволяет зарегистрировать обработчик событий навигации.
```js
registerEventHandler(navEventHandler: NavigationEventHandler): void;
```
где:

`navEventHandler` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### unregisterEventHandler()
Метод позволяет разрегистрировать обработчик событий навигации.
```js
unregisterEventHandler(navEventHandler: NavigationEventHandler): void;
```
где:

`navEventHandler` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### setActive()
Метод позволяет установить обработчик навигации по умолчанию.
```js
setActive(nvEventHandlerName: string, isActive: boolean): void;
```
где:

`nvEventHandlerName` -- имя обработчика навигации,\
`isActive` -- активность.

### getActiveNavigation()
Метод позволяет получить текущий обработчик навигации.
```js
getActiveNavigation(): NavigationEventHandler;
```
Возвращает объект <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### setDefaultNavigation()
Метод позволяет восстановить обработчик навигации по умолчанию.
```js
setDefaultNavigation(): void;
```

### setCameraPosition()
Метод позволяет установить позицию камеры.
```js
setCameraPosition(params: CameraPosition): void;
```
где:

`params` -- параметры <a href="../CameraPosition">позиции камеры</a>.

### getCameraPosition()
Метод позволяет получить позицию камеры.
```js
getCameraPosition(): CameraPosition;
```
Возвращает <a href="../CameraPosition">позицию камеры</a>.


### getCamera()
Метод позволяет получить камеру.
```js
getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее смотри <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.


### fitToView() {#fitToView}
Метод позволяет спозиционировать заданные элементы в центре экрана.
```js
fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean): void;
```
где:

`elementIds` -- список идентификаторов или один идентификатор элемнета сцены,\
`modelPart` -- идентификатор части консолидированной модели или объект части консолидированной модели,\
`immediate` -- анимация при центрировании, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

### setPivotPoint()
Метод позволяет задать положение опорной точки камеры.
```js
setPivotPoint(point: Point3): void;
```
где:

`point` -- <a href="../Point3">точка</a> в пространстве сцены.

### getPivotPoint()
Метод позволяет получить положение опорной точки камеры.
```js
getPivotPoint(): Point3;
```
Возвращает объект типа <a href="../Point3">Point3</a>.


### resetPivotPoint()
Метод позволяет сбросить положение опорной точки камеры.
```js
resetPivotPoint(): void;
```