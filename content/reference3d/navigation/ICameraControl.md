---
title: "ICameraControl"
draft: false
weight: 9
---

## ICameraControl {#ICameraControl}
**ICameraControl** -- интерфейс, позволяющий взаимодействовать с контроллером камеры.
```js
export interface ICameraControl {
  getCamera(): THREE.Camera;
  getCameraParameters(): CameraParameters;
  setCameraParameters(iParams: CameraParameters): void;
  setAspectRatio(width: number, heigth: number): boolean;

  rotate(movement: THREE.Vector2, rotationCenter: THREE.Vector3): void;
  translate(startNdcPos: THREE.Vector2, endNdcPos: THREE.Vector2, viewCenter: THREE.Vector3): void;
  spin(movement: THREE.Vector2): void;
  getCameraOrientation(): CameraOrientation;
  setCameraOrientation(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void;
  setViewCenter(viewCenter: THREE.Vector3): void;
  getViewCenter(): THREE.Vector3;
  zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
  zoomToFit(bb: THREE.Box3, iOrientation?: CameraOrientation, isAnimationEnabled?: boolean): void;

  getNavigationMode(): CameraNavigationMode;
  setNavigationMode(mode: CameraNavigationMode, isEnable: boolean, duration?: number): void;

  getCameraMode(): CameraMode;
  setCameraMode(mode: CameraMode): boolean;
}
```

## Методы

### getCamera()
Метод позволяет получить камеру.
```js
  getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее: <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.

### getCameraParameters()
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает параметры камеры. Подробнее: [CameraParameters](../CameraParameters).

### setCameraParameters()
Метод позволяет задать параметры камеры.
```js
  setCameraParameters(iParams: CameraParameters): void;
```
где:\
`iParams` -- параметры камеры. Подробнее: [CameraParameters](../CameraParameters).

### setAspectRatio()
Метод позволяет задать соотношение сторон камеры.
```js
setAspectRatio(width: number, heigth: number): boolean;
```
где:\
`width` -- ширина изображения, может быть в любых величинах.\
`heigth` -- высота изображения, может быть в любых величинах.\
Результирующе соотношение сторон равно `width / heigth`.\
Возвращает `true`, если новое соотношение сторон отличается от предыдущего.</a>.

###  rotate()
Метод позволяет повернуть камеру вокруг точки вращения по круговой орбите.
```js
rotate(movement: THREE.Vector2, rotationCenter: THREE.Vector3): void;
```
где:\
`movement` -- смещение в экранных координатах.\
`rotationCenter` -- точка, относительно которой осуществляется вращение камеры.

###  translate()
Метод позволяет переместить камеру по прямолинейной траектории относительно заданной точки.
```js
translate(startNdcPos: THREE.Vector2, endNdcPos: THREE.Vector2, viewCenter: THREE.Vector3): void;
```
где:\
`startNdcPos` -- начальное положение в Normalized Device Coordinates (NDC пространство).\
`endNdcPos` -- конечное положение в Normalized Device Coordinates (NDC пространство).\
`viewCenter` -- точка, относительно которой осуществляется смещение камеры.

###  spin()
Метод позволяет повернуть камеру вокруг `Up` вектора камеры.
```js
spin(movement: THREE.Vector2): void;
```
где:\
`movement` -- смещение в экранных координатах.

###  getCameraOrientation()
Метод позволяет получить ориентацию камеры в пространстве. Подробнее: [CameraOrientation](../CameraOrientation).
```js
getCameraOrientation(): CameraOrientation;
```

###  setCameraOrientation()
Метод позволяет ориентировать камеру в пространстве, позиция камеры при этом не изменяется.
```js
setCameraOrientation(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void;
```
где:\
`iOrientation` -- конечная ориентация камеры. Подробнее: [CameraOrientation](../CameraOrientation).\
`isAnimationEnabled` -- анимация при изменении ориентации, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

###  getViewCenter() {#getViewCenter}
Метод позволяет получить положение точки взгляда. Подробнее: [ViewCenter](../CameraParameters/#viewCenter).
```js
getViewCenter(): THREE.Vector3;
```

###  setViewCenter()
Метод позволяет задать положение точки взгляда. Подробнее: [ViewCenter](../CameraParameters/#viewCenter).
```js
setViewCenter(viewCenter: THREE.Vector3): void;
```
где:\
`viewCenter` -- положение точки взгляда в мировом пространстве.

###  zoomToPoint()
Метод позволяет приблизить либо отдалить камеру относительно точки.
```js
zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
```
где:\
`deltaSign` -- дистанция приближения.\
`point` -- точка приближения.

###  zoomToFit()
Метод позволяет центрировать камеру относительно ограничивающего объема в нужной ориентации.
```js
zoomToFit(boundingBox: THREE.Box3, iOrientation?: CameraOrientation, isAnimationEnabled?: boolean): void;
```
где:\
`boundingBox` -- ограничивающий объем, относительно которого центрируется камера. Подробнее: [THREE.Box3](https://threejs.org/docs/#api/en/math/Box3).\
`iOrientation` -- конечная ориентация камеры. По умолчанию сохраняется текущая ориентация камеры. Подробнее: [CameraOrientation](../CameraOrientation).\
`isAnimationEnabled` -- анимация при центрировании, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

###  getNavigationMode()
Метод позволяет получить тип навигации, осуществляемой над камерой.
```js
getNavigationMode(): CameraNavigationMode;
```
Возвращает тип навигации камеры. Подробнее: [CameraNavigationMode](../CameraNavigationMode).

###  setNavigationMode()
Метод позволяет задать тип навигации камеры в пространстве.
```js
setNavigationMode(mode: CameraNavigationMode, isEnable: boolean, duration?: number): void;
```
где:\
`mode` -- тип навигации камеры. Подробнее: [CameraNavigationMode](../CameraNavigationMode).\
`isEnable` -- активность.\
`duration` -- продолжительность навигации в миллисекундах. Параметр применяется только если `isEnable == true`.

  Если `isEnable == true`, и определён `duration`, то по истечении задержки `duration` произойдет отключение заданного типа навигации.
  Эквивалентно вызову `setNavigationMode(mode, false)` после задержки `duration`.

  Если во время ожидания происходит вызов `setNavigationMode` с любыми параметрами, то задержка сбрасывается и вызов `setNavigationMode(mode, false)` происходит немедленно, затем применяются новые параметры.

###  getCameraMode()
Метод позволяет получить тип проекции камеры, используемый для отображения объектов на сцене.
```js
  getCameraMode(): CameraMode;
```
Возвращает тип проекции камеры. Подробнее: [CameraMode](../CameraNavigationMode#CameraMode).

###  setCameraMode()
Метод позволяет задать тип проекции камеры, используемый для отображения объектов на сцене.
```js
  setCameraMode(mode: CameraMode): boolean;
```
где:\
`mode` --  тип проекции. Подробнее: [CameraMode](../CameraNavigationMode#CameraMode).