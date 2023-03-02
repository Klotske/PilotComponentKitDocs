---
title: "INavigation"
draft: false
weight: 9
---

**INavigation** -- интерфейс позволяющий взаимодействовать с навигацией на сцене.

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
Зарегистрировать обработчика событий навигации.

```js
registerEventHandler(navEventHandler: NavigationEventHandler): void;
```
где:

`navEventHandler` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### unregisterEventHandler()
Разрегистрировать обработчика событий навигации.

```js
unregisterEventHandler(navEventHandler: NavigationEventHandler): void;
```
где:

`navEventHandler` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### setActive()
Установить обработчик навигации по умолчанию.

```js
setActive(nvEventHandlerName: string, isActive: boolean): void;
```
где:

`nvEventHandlerName` -- имя обработчика навигации.\
`isActive` -- активность.

### getActiveNavigation()
Получить текущий обработчик навигации

```js
getActiveNavigation(): NavigationEventHandler;
```
Возвращает объект <a href="../NavigationEventHandler">NavigationEventHandler</a>.

### setDefaultNavigation()
Восстановить обработчик навигации по умолчанию.

```js
setDefaultNavigation(): void;
```

### setCameraPosition()
Установить позицию камеры.

```js
setCameraPosition(params: CameraPosition): void;
```
где:

`params` -- параметры <a href="../CameraPosition">позиции камеры</a>.

### getCameraPosition()
Получить позицию камеры.

```js
getCameraPosition(): CameraPosition;
```
Возвращает <a href="../CameraPosition">позицию камеры</a>.


### getCamera()
Получить камеру.

```js
getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее смотри <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.


### fitToView()
Спозиционировать заданные элементы в центре экрана.

```js
fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean): void;
```
где:

`elementIds` -- список идентификаторов или один идентификатор элемнета сцены.\
`modelPart` -- идентификатор части консолидированной модели или объект части консолидированной модели.\
`immediate` -- анимация при центрировании. `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

### setPivotPoint()
Задать положение опорной точки взгляда камеры.

```js
setPivotPoint(point: Point3): void;
```
где:

`point` -- <a href="../Point3">точка</a> в пространстве сцены.

### setPivotPoint()
Получить положение опорной точки взгляда камеры.

```js
getPivotPoint(): Point3;
```
Возвращает объект типа <a href="../Point3">Point3</a>.


### resetPivotPoint()
Сбросить положение опорной точки взгляда камеры.

```js
resetPivotPoint(): void;
```