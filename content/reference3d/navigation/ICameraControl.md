---
title: "ICameraControl"
draft: false
weight: 9
---


## CameraParameters {#CameraParameters}
```js
export type CameraParameters = { position: THREE.Vector3, eyeDir: THREE.Vector3, angle: number };
```

## ICameraControl {#ICameraControl}
**ICameraControl** -- интерфейс, позволяющий взаимодействовать с контроллером камеры.
```js
export interface ICameraControl {
  getCamera(): THREE.Camera;
  getCameraParameters(): CameraParameters;
  setCameraParameters(iParams: CameraParameters): void;
  setAspectRatio(width: number, heigth: number): boolean;

  rotate(movement: THREE.Vector2, rotationCenter: THREE.Vector3): void;
  translate(prevPosNdc: THREE.Vector2, currPosNdc: THREE.Vector2, viewCenter: THREE.Vector3): void;
  spin(movement: THREE.Vector2): void;
  orientateCamera(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void
  zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
  zoomToFit(bb: THREE.Box3, iOrientation?: CameraOrientation, iAnimationEnabled?: boolean): void;

  /** @deprecated */
  isNavigation(): boolean;
  /** @deprecated */
  isRotationNavigation(): boolean;
  /** @deprecated */
  setNavigationByMouseActive(isActive: boolean, navDuration?: number): void;
  /** @deprecated */
  setNavigationByKeyboardActive(isActive: boolean): void;
  /** @deprecated */
  setRotationNavigationActive(isActive: boolean): void;

  /** @deprecated */
  getMovementVector(): THREE.Vector3;
  /** @deprecated */
  moveByImpulse(elapsed_ms: number, movementVector?: THREE.Vector3, intersection?: THREE.Intersection): boolean;
  /** @deprecated */
  setImpulseDirection(dir: Direction, add: boolean): void;
  /** @deprecated */
  setIncreasedImpulse(isIncreased: boolean): void;
}
```

## Методы

### getCamera()
Метод позволяет получить камеру.
```js
  getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее смотри <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.

### getCameraParameters(): CameraParameters;
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает [параметры](#CameraParameters) камеры.

### setCameraParameters(iParams: CameraParameters): void;
Метод позволяет задать параметры камеры.
```js
  setCameraParameters(iParams: CameraParameters): void;
```
где:

`iParams` -- [параметры](#CameraParameters) камеры.

### setAspectRatio(width: number, heigth: number): boolean;
Метод позволяет задать соотношение сторон камеры.
```js
setAspectRatio(width: number, heigth: number): boolean;
```
где:

`width` -- ширина изображения, может быть в любых величинах.\
`heigth` -- высота изображения, может быть в любых величинах.\
Результирующе соотношение сторон равно `width / heigth`.\
Возвращает `true` если новое соотношение сторон отличается от предыдущего.</a>.

###  rotate(movement: THREE.Vector2, rotationCenter: THREE.Vector3): void;
Метод позволяет повернуть камеру вокруг точки вращения по круговой орбите.
```js
rotate(movement: THREE.Vector2, rotationCenter: THREE.Vector3): void;
```
где:\
`movement` -- смещение в экранных координатах.\
`rotationCenter` -- точка, относительно которой осуществляется вращение камеры.

###  translate(startNdcPos: THREE.Vector2, endNdcPos: THREE.Vector2, viewCenter: THREE.Vector3): void;
Метод позволяет переместить камеру по прямолинейной траектории, относительно заданной точки.
```js
translate(startNdcPos: THREE.Vector2, endNdcPos: THREE.Vector2, viewCenter: THREE.Vector3): void;
```
где:\
`startNdcPos` -- начальное положение в нормализованных экранных координатах (NDC).\
`endNdcPos` -- конечное положение в нормализованных экранных координатах (NDC).\
`viewCenter` -- точка, относительно которой осуществляется смещение камеры.

###  spin(movement: THREE.Vector2): void;
Метод позволяет повернуть камеру вокруг `Up` вектора камеры.
```js
spin(movement: THREE.Vector2): void;
```
где:\
`movement` -- смещение в экранных координатах.

###  orientateCamera(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void
Метод позволяет ориентировать камеру в пространстве, позиция камеры при этом не изменяется.
```js
orientateCamera(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void;
```
где:\
`iOrientation` -- конечная ориентация камеры.\
`isAnimationEnabled` -- анимация при изменении ориентации, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

###  zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
Метод позволяет приблизить, либо отдалить камеру относительно точки.
```js
zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
```
где:\
`deltaSign` -- дистанция приближения.\
`point` -- точка приближения.

###  zoomToFit(boundingBox: THREE.Box3, iOrientation?: CameraOrientation, iAnimationEnabled?: boolean): void;
Метод позволяет центрировать камеру относительно ограничивающего объема в нужной ориентации.
```js
zoomToFit(boundingBox: THREE.Box3, iOrientation?: CameraOrientation, isAnimationEnabled?: boolean): void;
```
где:\
`boundingBox` -- ограничивающий объем, относительно которого центрируется камера. Подробнее: [THREE.Box3](https://threejs.org/docs/#api/en/math/Box3).\
`iOrientation` -- конечная ориентация камеры. По умолчанию сохраняется текущая ориентация камеры.\
`isAnimationEnabled` -- анимация при центрировании, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.