---
title: "INavigationTool"
draft: false
weight: 9
---

**INavigationTool** -- интерфейс, позволяющий взаимодействовать с навигацией на сцене.\


{{< hint type="note" icon=gdoc_info_outline title="Примечание">}}
Для того, чтобы создать свой обработчик для навигации по сцене, необходимо реализовать интерфейс [PilotWeb3D.INavigationTool](#INavigationTool), либо унаследоваться от класса [PilotWeb3D.NavigationTool](../NavigationTool).

Например, [PilotWeb3D.MobileNavigation](../MobileNavigation) и [PilotWeb3D.DesktopNavigation](../DesktopNavigation) наследуются от [PilotWeb3D.NavigationTool](../NavigationTool), который является реализацией интерфейса `PilotWeb3D.INavigationTool`.
{{< /hint >}}



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

### get name(): string
Метод позволяет получить имя обработчика навигации.
```js
get name(): string;
```
Возвращает имя обработчика навигации.

### init(navAgent: INavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void
Инициализатор обработчика навигации. Вызывается из [INavigation](../INavigation) при регистрации обработчика.
```js
init(navAgent: INavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
```
где:
`navAgent` -- агент навигации. Подробнее смотри [INavigationAgent](../INavigationAgent).\
`cameraControl` -- контроллер камеры. Подробнее смотри [ICameraControl](../ICameraControl).\
`intersectionChecker` -- контроллер камеры. Подробнее смотри [IModelIntersectionChecker](../../IModelIntersectionChecker).

### setActive(isActive: boolean): void
Активатор обработчика навигации. Вызывается из [INavigation](../INavigation) при активации/деактивации обработчика.
```js
setActive(isActive: boolean): void;
```
где:
`isActive` -- активность.

### getPivotPoint(): THREE.Vector3
Метод позволяет получить положение опорной точки камеры.
```js
getPivotPoint(): THREE.Vector3;
```
Возвращает объект типа [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### setPivotPoint(): void
Метод позволяет задать положение опорной точки камеры.
```js
setPivotPoint(pivotPoint: THREE.Vector3): void;
```
где:
`pivotPoint` -- точка в мировом пространстве. Подробнее смотри [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### setCameraParameters(iParams: CameraParameters): void
Метод позволяет задать параметры камеры.
```js
  setCameraParameters(iParams: CameraParameters): void;
```
где:
`iParams` -- параметры камеры. Подробнее смотри [CameraParameters](../CameraParameters).

### getCameraParameters(): CameraParameters
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает параметры камеры. Подробнее смотри [CameraParameters](../CameraParameters).
