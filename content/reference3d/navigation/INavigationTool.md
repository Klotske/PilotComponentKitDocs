---
title: "INavigationTool"
draft: false
weight: 9
---

**INavigationTool** -- интерфейс, позволяющий взаимодействовать с навигацией на сцене.

Для того, чтобы создать свой обработчик для навигации по сцене, необходимо реализовать интерфейс [PilotWeb3D.INavigationTool](#INavigationTool), либо унаследоваться от класса [PilotWeb3D.NavigationTool](../NavigationTool).

Например, [PilotWeb3D.MobileNavigation](../MobileNavigation) и [PilotWeb3D.DesktopNavigation](../DesktopNavigation) наследуются от [PilotWeb3D.NavigationTool](../NavigationTool), который является реализацией интерфейса `PilotWeb3D.INavigationTool`.

## INavigationTool {#INavigationTool}
Обработчик навигации, базовый интерфейс.

```js
export interface INavigationTool {
  get name(): string;
  init(navAgent: INavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
  setActive(isActive: boolean): void;
  getPivotPoint(): THREE.Vector3;
  setPivotPoint(pivotPoint: THREE.Vector3): void;
  setCameraParameters(iParams: CameraParameters): void;
  getCameraParameters(): CameraParameters;
}
```
## Методы

### get name()
Метод позволяет получить имя обработчика навигации.
```js
get name(): string;
```
Возвращает имя обработчика навигации.

### init()
Инициализатор обработчика навигации. Вызывается из [INavigation](../INavigation) при регистрации обработчика.
```js
init(navAgent: INavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
```
где:\
`navAgent` -- агент навигации. Подробнее: [INavigationAgent](../INavigationAgent).\
`cameraControl` -- контроллер камеры. Подробнее: [ICameraControl](../ICameraControl).\
`intersectionChecker` -- обработчик пересечений на сцене. Подробнее: [IModelIntersectionChecker](../../render/IModelIntersectionChecker).

### setActive()
Метод позволяет активировать обработчик событий навигации. Вызывается из [INavigation](../INavigation) при активации/деактивации обработчика.
```js
setActive(isActive: boolean): void;
```
где:\
`isActive` -- активность.

### getPivotPoint()
Метод позволяет получить положение опорной точки камеры.
```js
getPivotPoint(): THREE.Vector3;
```
Возвращает объект типа [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### setPivotPoint() {#setPivotPoint}
Метод позволяет задать положение опорной точки камеры.\
Опорная точка используется при навигации по сцене, вращение камеры осуществляется относительно опорной точки. Если точка не задана, то используется `viewCenter` заданный в `CameraControl`.
Подробнее: [getViewCenter](../ICameraControl/#getViewCenter), [ViewCenter](../CameraParameters/#viewCenter).
```js
setPivotPoint(pivotPoint: THREE.Vector3): void;
```
где:\
`pivotPoint` -- точка в мировом пространстве. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### setCameraParameters()
Метод позволяет задать параметры камеры.
```js
  setCameraParameters(iParams: CameraParameters): void;
```
где:\
`iParams` -- параметры камеры. Подробнее: [CameraParameters](../CameraParameters).

### getCameraParameters()
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает параметры камеры. Подробнее: [CameraParameters](../CameraParameters).
