---
title: "INavigation"
draft: false
weight: 9
---

**INavigation** -- интерфейс, позволяющий взаимодействовать с навигацией на сцене.

```js
export interface INavigation {
  registerNavigation(navigationTool: INavigationTool): void;
  unregisterNavigation(navigationTool: INavigationTool): void;
  setActive(navigationToolName: string, isActive: boolean): void;
  getActiveNavigation(): INavigationTool | null;
  getNavigationAgent(): INavigationAgent;
  getNavigationArea(): DOMRect;
  setCameraParameters(params: CameraParameters): void;
  getCameraParameters(): CameraParameters;
  getCameraControl(): ICameraControl;
  getCamera(): THREE.Camera;
  fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean, cameraOrientation?: CameraOrientation): void;
  setPivotPoint(point: Point3): void;
  getPivotPoint(): Point3;
  resetPivotPoint(): void;
}
```

## Методы

### registerNavigation()
Метод позволяет зарегистрировать обработчик событий навигации.
```js
registerNavigation(navigationTool: INavigationTool): void;
```
где:\
`navigationTool` -- реализация обработчика событий. Подробнее: <a href="../NavigationTool">INavigationTool</a>.

### unregisterNavigation()
Метод позволяет разрегистрировать обработчик событий навигации.
```js
unregisterNavigation(navigationTool: INavigationTool): void;
```
где:\
`navigationTool` -- реализация обработчика событий. Подробнее: <a href="../NavigationTool">INavigationTool</a>.

### setActive()
Метод позволяет активировать обработчик событий навигации.
Активным может быть только один обработчик навигации в каждый момент времени.
```js
setActive(navigationToolName: string, isActive: boolean): void;
```
где:\
`navigationToolName` -- имя обработчика навигации,\
`isActive` -- активность.

### getActiveNavigation()
Метод позволяет получить текущий обработчик навигации.
```js
getActiveNavigation(): INavigationTool | null;
```
Возвращает объект <a href="../INavigationTool">INavigationTool</a>.

### getNavigationAgent()
Метод позволяет получить <a href="../INavigationAgent">INavigationAgent</a> - предоставляющий источники событий навигации.
```js
getNavigationAgent(): INavigationAgent;
```
Возвращает объект <a href="../INavigationAgent">INavigationAgent</a>.

### getNavigationArea()
Метод позволяет получить прямоугольник области навигации.
```js
  getNavigationArea(): DOMRect;
```
Возвращает объект <a href="https://developer.mozilla.org/en-US/docs/Web/API/DOMRect">DOMRect</a>.

### setCameraParameters()
Метод позволяет установить параметры камеры.
```js
setCameraParameters(params: CameraParameters): void;
```
где:\
`params` -- параметры камеры. Подробнее: [CameraParameters](../CameraParameters). 

### getCameraParameters()
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает параметры камеры. Подробнее: [CameraParameters](../CameraParameters).

### getCameraControl()
Метод позволяет получить контроллер камеры.
```js
  getCameraControl(): ICameraControl;
```
Возвращает контроллер камеры. Подробнее: [ICameraControl](../ICameraControl).

### getCamera()
Метод позволяет получить камеру.
```js
getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее: <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.

### fitToView() {#fitToView}
Метод позволяет спозиционировать заданные элементы в центре экрана.
```js
fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean, cameraOrientation?: CameraOrientation): void;
```
где:\
`elementIds` -- список идентификаторов или один идентификатор элемента сцены,\
`modelPart` -- идентификатор части консолидированной модели или объект части консолидированной модели,\
`immediate` -- анимация при центрировании, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.\
`cameraOrientation` -- конечная ориентация камеры. По умолчанию сохраняется текущая ориентация камеры. Подробнее: [CameraOrientation](../CameraOrientation).

### setPivotPoint()
Метод позволяет задать положение опорной точки камеры.
```js
setPivotPoint(point: Point3): void;
```
где:\
`point` -- точка в пространстве сцены. Подробнее: [Point3](../Point3).

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