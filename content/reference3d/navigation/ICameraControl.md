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
  orientateCamera(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void
  zoomToPoint(deltaSign: number, point: THREE.Vector3): void;
  zoomToFit(bb: THREE.Box3, iOrientation?: CameraOrientation, isAnimationEnabled?: boolean): void;

  getNavigationMode(): CameraNavigationMode;
  setNavigationMode(mode: CameraNavigationMode, isEnable: boolean, duration?: number): void;
}
```

## Методы

### getCamera()
Метод позволяет получить камеру.
```js
  getCamera(): THREE.Camera;
```
Возвращает объект камеры. Подробнее смотри <a href="https://threejs.org/docs/#api/en/cameras/Camera">THREE.Camera</a>.

### getCameraParameters()
Метод позволяет получить параметры камеры.
```js
getCameraParameters(): CameraParameters;
```
Возвращает параметры камеры. Подробнее смотри [CameraParameters](../CameraParameters).

### setCameraParameters()
Метод позволяет задать параметры камеры.
```js
  setCameraParameters(iParams: CameraParameters): void;
```
где:
`iParams` -- параметры камеры. Подробнее смотри [CameraParameters](../CameraParameters).

### setAspectRatio()
Метод позволяет задать соотношение сторон камеры.
```js
setAspectRatio(width: number, heigth: number): boolean;
```
где:

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
`startNdcPos` -- начальное положение в нормализованных экранных координатах (NDC).\
`endNdcPos` -- конечное положение в нормализованных экранных координатах (NDC).\
`viewCenter` -- точка, относительно которой осуществляется смещение камеры.

###  spin()
Метод позволяет повернуть камеру вокруг `Up` вектора камеры.
```js
spin(movement: THREE.Vector2): void;
```
где:\
`movement` -- смещение в экранных координатах.

###  orientateCamera()
Метод позволяет ориентировать камеру в пространстве, позиция камеры при этом не изменяется.
```js
orientateCamera(iOrientation: CameraOrientation, isAnimationEnabled?: boolean): void;
```
где:\
`iOrientation` -- конечная ориентация камеры. Подробнее смотри [CameraOrientation](../CameraOrientation).\
`isAnimationEnabled` -- анимация при изменении ориентации, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

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
`boundingBox` -- ограничивающий объем, относительно которого центрируется камера. Подробнее смотри [THREE.Box3](https://threejs.org/docs/#api/en/math/Box3).\
`iOrientation` -- конечная ориентация камеры. По умолчанию сохраняется текущая ориентация камеры. Подробнее смотри [CameraOrientation](../CameraOrientation).\
`isAnimationEnabled` -- анимация при центрировании, `true` -- отключить анимацию, `false` -- включить анимацию. По умолчанию анимация включена.

###  getNavigationMode()
Метод позволяет получить тип навигации, осуществляемой над камерой.
```js
getNavigationMode(): CameraNavigationMode;
```
Возвращает тип навигации камеры. Подробнее смотри [CameraNavigationMode](../CameraNavigationMode).

###  setNavigationMode()
Метод позволяет задать тип навигации камеры в пространстве.
```js
setNavigationMode(mode: CameraNavigationMode, isEnable: boolean, duration?: number): void;
```
где:\
`mode` -- тип навигации камеры. Подробнее смотри [CameraNavigationMode](../CameraNavigationMode).\
`isEnable` -- активность.\
`duration` -- продолжительность навигации в *миллисекундах*, применимо только при `isEnable == true`.\
{{<hint type="note" icon=gdoc_info_outline title="Примечание">}}
  Если `isEnable == true`, и определён `duration`, то по истечении задержки в `duration` *ms* произойдет отключение заданного типа навигации.
  Эквивалентно вызову `setNavigationMode(mode, false)` после задержки в `duration` *ms*.\
  Если во время ожидания происходит вызов `setNavigationMode` с любыми параметрами, то задержка сбрасывается и вызов `setNavigationMode(mode, false)` происходит немедленно, затем применяются новые параметры.
{{< /hint>}}