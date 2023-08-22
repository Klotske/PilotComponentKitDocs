---
title: "GizmoAxis"
draft: false
weight: 9
---

## GizmoAxis {#GizmoAxis}
**GizmoAxis** -- абстрактный класс, базовый для всех осей [GizmoControl](../GizmoControl).\
Каждая ось описывает свой тип манипуляций над контролом.
 
Примеры реализаций: [GizmoTranslationAxis](../GizmoTranslationAxis), [GizmoRotationAxis](../GizmoRotationAxis), [GizmoScaleAxis](../GizmoScaleAxis).

```js
export class GizmoAxis extends THREE.Object3D implements IGizmoObject {
  protected _isHovered: boolean;
  protected _isActive: boolean;
  protected _plane: THREE.Plane;
  protected _axisDir: THREE.Vector3;
  protected _raycaster: THREE.Raycaster;

  protected _worldPositionStart: THREE.Vector3;
  protected _worldQuaternionStart: THREE.Quaternion;
  protected _worldAxisDir: THREE.Vector3;

  protected _startPoint: THREE.Vector3;
  protected _endPoint: THREE.Vector3;

  constructor(axisDir: THREE.Vector3, readonly handle: IGizmoObject, readonly picker?: IGizmoObject, readonly helper?: IGizmoObject);

  getActive(): boolean;
  setActive(value: boolean): void;
  getHovered(): boolean;
  setHovered(value: boolean): void;
  dispose(): void;
  abstract moveByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Matrix4;
  protected abstract updateGizmoPlane(camera: THREE.Camera): void;
  protected setStartPt(ndcPos: THREE.Vector2, camera: THREE.Camera): void;
}
```

## Поля

## handle: IGizmoObject {#handle}
 Поле хранит геометрию оси, рисуемую на сцене. Если [picker](#picker) не задан, то используется для проверки пересечений. Подробнее: [IGizmoObject](../IGizmoObject).
```js
readonly handle: IGizmoObject;
```

## picker: IGizmoObject {#picker}
 Поле хранит геометрию оси, используемую для проверки пересечений. Подробнее: [IGizmoObject](../IGizmoObject).
```js
readonly picker: IGizmoObject;
```

## helper: IGizmoObject {#helper}
 Поле хранит вспомогательную геометрию оси. Подробнее: [IGizmoObject](../IGizmoObject).
```js
readonly helper: IGizmoObject;
```

## _isHovered: boolean
Поле хранит значение ховера для оси.
```js
protected _isHovered: boolean;
```

## _isActive: boolean
Поле хранит значение активности оси.
```js
protected _isActive: boolean;
```

## _plane: THREE.Plane {#AxisPlane}
Поле хранит плоскость, используемую для расчётов смещения курсора, при манипуляциях с осью. Подробнее: [THREE.Plane](https://threejs.org/docs/#api/en/math/Plane).
```js
protected _plane: THREE.Plane;
```
## _axisDir: THREE.Vector3 {#axisDir}
Поле хранит вектор направления оси в локальных координатах. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).
```js
protected _axisDir: THREE.Vector3;
```

## _raycaster: THREE.Raycaster
Поле хранит объект [THREE.Raycaster](https://threejs.org/docs/#api/en/core/Raycaster), используемый для расчётов смещения, при манипуляциях с осью.
```js
protected _raycaster: THREE.Raycaster;
```

## _worldPositionStart: THREE.Vector3 {#worldPositionStart}
Поле хранит значение положения оси в мировых координатах, в момент активации оси.\
При [setActive](#setActive)(`true`) в данный вектор сохраняется значение положения оси. Используется для расчета смещения оси относительно начального положения во время манипуляций над осью.
Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).
```js
protected _worldPositionStart: THREE.Vector3;
```

## _worldQuaternionStart: THREE.Quaternion {#worldQuaternionStart}
Поле хранит значение кватерниона оси, в момент активации оси.\
При [setActive](#setActive)(`true`) в данный кватернион сохраняется значение поворота оси. Используется для расчета поворота оси относительно начального положения, во время манипуляций над осью.
Подробнее: [THREE.Quaternion](https://threejs.org/docs/#api/en/math/Quaternion).
```js
protected _worldQuaternionStart: THREE.Quaternion;
```

## _worldAxisDir: THREE.Vector3 {#worldAxisDir}
Поле хранит вектор направления оси в мировых координатах, в момент активации оси.\
При [setActive](#setActive)(`true`) в данный вектор сохраняется [направление](#axisDir) оси в мировых координатах.  Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).
```js
protected _worldAxisDir: THREE.Vector3;
```
 
## _startPoint: THREE.Vector3 {#StartPoint}
Поле хранит начальное положение курсора на [плоскости оси](#AxisPlane) при начале манипуляции с осью. Используется для расчета смещения курсора в плоскости оси во время манипуляций с осью. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).
```js
protected _startPoint: THREE.Vector3;
```

## _endPoint: THREE.Vector3 {#EndPoint}
Поле хранит текущее, или последнее положение курсора на [плоскости оси](#AxisPlane) при манипуляции с осью. Используется для расчета смещения курсора в плоскости оси относительно [начальной точки](#StartPoint) во время манипуляций с осью. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).
```js
protected _endPoint: THREE.Vector3;
```
## Конструктор
```js
constructor(axisDir: THREE.Vector3, 
            handle: IGizmoObject,
            picker?: IGizmoObject,
            helper?: IGizmoObject);
```
где:
`axisDir` -- направление оси в локальных координатах. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

`handle` -- задает [handle](#handle) - геометрию оси, рисуемую на сцене. Подробнее: [IGizmoObject](../IGizmoObject).

`picker` -- задает [picker](#picker) - геометрию оси, используемую для проверки пересечений. Не обязательный параметр. Подробнее: [IGizmoObject](../IGizmoObject).

`helper` -- задает [helper](#helper) - вспомогательную геометрию оси. Не обязательный параметр. Подробнее: [IGizmoObject](../IGizmoObject).

## Методы

### getHovered()
Метод возвращает значение ховера для оси.
```js
  getHovered(): boolean;
```
Возвращает `true`, если ховер активен.

### setHovered()
Метод устанавливает значение ховера для оси, а так же вызывает методы `setHovered(value)` у объектов [handle](#handle), [picker](#picker) и [helper](#helper).
```js
  setHovered(value: boolean): void;
```
где:
`value` - значение ховера.

### getActive()
Метод возвращает статус активности для оси.
```js
  getActive(): boolean;
```
Возвращает `true`, если объект активен.

### setActive() {#setActive}
Метод устанавливает статус активности для оси, а так же вызывает методы `setActive(value)` у объектов [handle](#handle), [picker](#picker) и [helper](#helper).
```js
  setActive(value: boolean): void;
```
где:
`value` - значение активности оси.
Если `value` равен `true`, то запоминает текущее [положение](#worldPositionStart) оси в мировых координатах, [кватернион поворота](#worldQuaternionStart) и [вектор направления](#worldAxisDir) оси в мировых координатах. В противном случае, сбрасывает значения [начального](#StartPoint) и [конечного](#EndPoint) положения курсора.

### dispose()
Метод освобождает ресурсы, выделенные оси, а также вызывает методы `dispose()` у объектов [handle](#handle), [picker](#picker) и [helper](#helper).
```js
  dispose(): void;
```

### moveByNdcPt()
Абстрактный метод, вычисляет матрицу трансформации объекта, вызванной манипуляциями с осью.
```js
  abstract moveByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Matrix4;
```
где:
`ndcPos` -- [текущее положение](#EndPoint) курсора в Normalized Device Coordinates (NDC пространство). Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).

`camera` -- камера, используемая для отрисовки `GizmoAxis` на сцене. Используется для перевода Normalized Device Coordinates (NDC пространство) в мировые координаты. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).

Возвращает матрицу трансформации объекта. Подробнее: [THREE.Matrix4](https://threejs.org/docs/#api/en/math/Matrix4).

### updateGizmoPlane()
Абстрактный метод, обновляет [плоскость](#AxisPlane), используемую для расчётов смещения курсора, при манипуляциях с осью.
```js
  protected abstract updateGizmoPlane(camera: THREE.Camera): void;
```
где:
`camera` -- камера, используемая для отрисовки `GizmoAxis` на сцене. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).

### setStartPt()
Метод вычисляет [начальное положение](#StartPoint) курсора на [плоскости оси](#AxisPlane).
```js
  protected setStartPt(ndcPos: THREE.Vector2, camera: THREE.Camera): void;
```
где:
`ndcPos` -- положение курсора в Normalized Device Coordinates (NDC пространство). Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).

`camera` -- камера, используемая для отрисовки `GizmoAxis` на сцене. Используется для перевода Normalized Device Coordinates (NDC пространство) в мировые координаты. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).