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
  getNavigationAgent(): NavigationAgent;
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

### registerNavigation()
Метод позволяет зарегистрировать обработчик событий навигации.
```js
registerNavigation(navigationTool: INavigationTool): void;
```
где:

`navigationTool` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationTool">INavigationTool</a>.

### unregisterNavigation()
Метод позволяет разрегистрировать обработчик событий навигации.
```js
unregisterNavigation(navigationTool: INavigationTool): void;
```
где:

`navigationTool` -- реализация обработчика событий. Подробнее смотри <a href="../NavigationTool">INavigationTool</a>.

### setActive()
Метод позволяет активировать обработчик событий навигации.
```js
setActive(navigationToolName: string, isActive: boolean): void;
```
где:

`navigationToolName` -- имя обработчика навигации,\
`isActive` -- активность.

{{<hint type="note" icon=gdoc_info_outline title="Примечание">}}
    Активным может быть только один обработчик навигации в каждый момент времени.
{{< /hint>}}

### getActiveNavigation()
Метод позволяет получить текущий обработчик навигации.
```js
getActiveNavigation(): INavigationTool | null;
```
Возвращает объект <a href="../INavigationTool">INavigationTool</a>.

### getNavigationAgent()
Метод позволяет получить <a href="../NavigationAgent">NavigationAgent</a> - предоставляющий источники событий навигации.
```js
getNavigationAgent(): NavigationAgent;
```
Возвращает объект <a href="../NavigationAgent">NavigationAgent</a>.

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
Возвращает объект камеры. Подробнее: <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.


### fitToView() {#fitToView}
Метод позволяет спозиционировать заданные элементы в центре экрана.
```js
fitToView(elementIds: string[] | string, modelPart: string | ModelPart, immediate?: boolean): void;
```
где:

`elementIds` -- список идентификаторов или один идентификатор элемента сцены,\
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