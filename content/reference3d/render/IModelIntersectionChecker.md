---
title: "IModelIntersectionChecker"
draft: false
weight: 9
---

**IModelIntersectionChecker** -- интерфейс обработки пересечений объектов на сцене.

```js
export interface IModelIntersectionChecker {
  get modelCenter(): THREE.Vector3;
  get boundingBox(): THREE.Box3;

  getIntersectionPoint(): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionByRay(ray: THREE.Ray): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByRay(ray: THREE.Ray): { modelId: string, guid: string } | undefined;
  getIntersectionByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): { modelId: string, guid: string } | undefined;
  getIntersectionIDByFrustumNdcPt(ndcFrustumBox: THREE.Box3, unProjMatrix: THREE.Matrix4, isContainsOnly: boolean): { modelId: string; guid: string; }[] | undefined;
}
```

## Свойства

###  get modelCenter()
Центр модели.
```js
  get modelCenter(): THREE.Vector3;
```
Возвращает вектор указывающий в центр модели. Подробнее смотри [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

###  get boundingBox()
Ограничивающий объем модели.
```js
  get boundingBox(): THREE.Box3;
```
Возвращает ограничивающий объем модели. Подробнее смотри [THREE.Box3](https://threejs.org/docs/?q=Box3#api/en/math/Box3).

## Методы

###  getIntersectionPoint()
Метод возвращает последнее рассчитанное пересечение модели.
```js
  getIntersectionPoint(): THREE.Intersection<THREE.Object3D> | undefined;
```
Возвращает объект типа `THREE.Intersection`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionByRay()
Метод возвращает ближайшее пересечение объекта модели с лучом.
```js
  getIntersectionByRay(ray: THREE.Ray): THREE.Intersection<THREE.Object3D> | undefined;
```
где: `ray` -- луч с которым считаются пересечения. Подробнее смотри [THREE.Ray](https://threejs.org/docs/#api/en/math/Ray).\
Возвращает объект типа `THREE.Intersection`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionIDByRay()
Метод возвращает `modelId` и `entityGuid` ближайшего объекта модели пересекающегося с лучом.
```js
  getIntersectionIDByRay(ray: THREE.Ray): { modelId: string, guid: string } | undefined;
```
где: `ray` -- луч с которым считаются пересечения. Подробнее смотри [THREE.Ray](https://threejs.org/docs/#api/en/math/Ray).\
Возвращает объект `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionByNdcPt()
Метод возвращает ближайшее пересечение объекта модели с лучом, выпущенным из точки нахождения камеры в направлении точки в NDC-пространстве.
```js
  getIntersectionByNdcPt(ndcPoint: THREE.Vector2, camera: THREE.Camera): THREE.Intersection<THREE.Object3D> | undefined;
```
где:\
`ndcPoint` -- 2D координаты точки в NDC-пространстве в которую выпускается луч. Подробнее смотри [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).\
`camera` -- камера, используемая для определения положения начала луча, и для перевода NDC-координат в мировые координаты. Подробнее смотри [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).\
Возвращает объект типа `THREE.Intersection`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionIDByNdcPt()
Метод возвращает `modelId` и `entityGuid` ближайшего объекта модели, пересекающегося с лучом, выпущенным из точки нахождения камеры в направлении точки в NDC-пространстве.
```js
  getIntersectionIDByNdcPt(ndcPoint: THREE.Vector2, camera: THREE.Camera): { modelId: string, guid: string } | undefined;
```
где:\
`ndcPoint` -- 2D координаты точки в NDC-пространстве в которую выпускается луч. Подробнее смотри [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).\
`camera` -- камера, используемая для определения положения начала луча, и для перевода NDC-координат в мировые координаты. Подробнее смотри [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).\
Возвращает объект `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает `undefined`.


###  getIntersectionIDByFrustumNdcPt() {#getIntersectionIDByFrustumNdcPt}
Метод возвращает список `modelId` и `entityGuid` объектов модели, пересекаемых усеченной пирамидой (Frustum).
```js
  getIntersectionIDByFrustumNdcPt(ndcFrustumBox: THREE.Box3, unProjMatrix: THREE.Matrix4, isContainsOnly: boolean): { modelId: string; guid: string; }[];
```
где:\
`ndcFrustumBox` -- Представление `Frsutum` в NDC-пространстве. Подробнее смотри [THREE.Box3](https://threejs.org/docs/?q=Box3#api/en/math/Box3).\
`unProjMatrix` -- Матрица проекции координат NDC-пространства в мировые координаты. Подробнее смотри [THREE.Matrix4](https://threejs.org/docs/#api/en/math/Matrix4).\
`isContainsOnly` -- если `true`, то отбрасываются не полностью содержащиеся внутри пирамиды объекты. В противном случае в вывод включаются как содержащиеся внутри пирамиды объекты, так и касающиеся или пересекающиеся с ней.\
Возвращает список объектов `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает пустой массив.

{{< hint type="note" icon=gdoc_info_outline title="Пример">}}
Расчёт пересечений с `Frustum`, образованным областью видимости камеры:
```js
  const camera = viewer3D.navigation.getCamera();
  const unprojectionMatrix = new THREE.Matrix4();
  const ndcFrustumBox = new THREE.Box3();
  //матрица проекции из NDC-пространства в мировые координаты:
  unprojectionMatrix.multiplyMatrices(camera.matrixWorld, camera.projectionMatrixInverse);
  //левый нижний угол усеченной пирамиды в NDC (x=-1, y=-1), ближняя плоскость камеры (nearPlane): z = -1:
  ndcFrustumBox.min = new THREE.Vector3(-1, -1, -1);
  //правый верхний угол усеченной пирамиды в NDC (x=1, y=1), дальняя плоскость камеры (farPlane): z = 1:
  ndcFrustumBox.max = new THREE.Vector3(1, 1, 1);

  const intersections = intersectionChecker.getIntersectionIDByFrustumNdcPt(ndcFrustumBox, unprojectionMatrix, false);
```
Более сложный пример использования смотри [BoxSelectionExtension](../../../extensions3d/BoxSelection).
{{< /hint >}}
