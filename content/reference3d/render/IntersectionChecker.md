---
title: "IntersectionChecker"
draft: false
weight: 9
---

## IIntersectionChecker  {#IIntersectionChecker}
**IIntersectionChecker** -- базовый интерфейс обработки пересечений объектов. Подробнее: [ISceneIntersectionChecker](#ISceneIntersectionChecker) и [IModelIntersectionChecker](#IModelIntersectionChecker).

```js
export interface IIntersectionChecker<TOptions extends IntersectionCheckOptions> {
  getIntersectionPoint(): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionByRay(ray: THREE.Ray, camera: THREE.Camera, options?: TOptions): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByRay(ray: THREE.Ray, camera: THREE.Camera, options?: TOptions): { modelId: string, guid: string } | undefined;
  getIntersectionByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera, options?: TOptions): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera, options?: TOptions): { modelId: string, guid: string } | undefined;
  getIntersectionIDByFrustumNdcPt(ndcFrustumBox: THREE.Box3, unProjMatrix: THREE.Matrix4, isContainsOnly: boolean, options?: TOptions): { modelId: string; guid: string; }[] | undefined;
}
```
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
  getIntersectionByRay(ray: THREE.Ray, camera: THREE.Camera, options?: TOptions): THREE.Intersection<THREE.Object3D> | undefined;
```
где:

`ray` -- луч с которым считаются пересечения. Подробнее: [THREE.Ray](https://threejs.org/docs/#api/en/math/Ray).\
`camera` -- камера, используемая в отрисовке. Необходима для проверки пересечений с объектами, не зависящими от глубины кадра (Спрайты, текстовые метки, точки замечаний и т.д.).\
`options` -- параметры проверки пересечений, необязательный параметр. Подробнее: [SceneCheckOptions](#SceneCheckOptions), [ModelCheckOptions](#ModelCheckOptions).\
Возвращает объект типа `THREE.Intersection`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionIDByRay()
Метод возвращает `modelId` и `entityGuid` ближайшего объекта модели пересекающегося с лучом.
```js
  getIntersectionIDByRay(ray: THREE.Ray, camera: THREE.Camera, options?: TOptions): { modelId: string, guid: string } | undefined;
```
где:

`ray` -- луч с которым считаются пересечения. Подробнее: [THREE.Ray](https://threejs.org/docs/#api/en/math/Ray).\
`camera` -- камера, используемая в отрисовке. Необходима для проверки пересечений с объектами, не зависящими от глубины кадра (Спрайты, текстовые метки, точки замечаний и т.д.).
`options` -- параметры проверки пересечений, необязательный параметр. Подробнее: [SceneCheckOptions](#SceneCheckOptions), [ModelCheckOptions](#ModelCheckOptions).\
Возвращает объект `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionByNdcPt()
Метод возвращает ближайшее пересечение объекта модели с лучом, выпущенным из точки нахождения камеры в направлении точки в Normalized Device Coordinates (NDC пространство).
```js
  getIntersectionByNdcPt(ndcPoint: THREE.Vector2, camera: THREE.Camera, options?: TOptions): THREE.Intersection<THREE.Object3D> | undefined;
```
где:

`ndcPoint` -- 2D координаты точки в Normalized Device Coordinates (NDC пространство) в которую выпускается луч. Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).\
`camera` -- камера, используемая для определения положения начала луча, и для перевода Normalized Device Coordinates (NDC пространство) в мировые координаты. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).\
`options` -- параметры проверки пересечений, необязательный параметр. Подробнее: [SceneCheckOptions](#SceneCheckOptions), [ModelCheckOptions](#ModelCheckOptions).\
Возвращает объект типа `THREE.Intersection`, если пресечение существует. В противном случае возвращает `undefined`. 

###  getIntersectionIDByNdcPt()
Метод возвращает `modelId` и `entityGuid` ближайшего объекта модели, пересекающегося с лучом, выпущенным из точки нахождения камеры в направлении точки в Normalized Device Coordinates (NDC пространство).
```js
  getIntersectionIDByNdcPt(ndcPoint: THREE.Vector2, camera: THREE.Camera, options?: TOptions): { modelId: string, guid: string } | undefined;
```
где:

`ndcPoint` -- 2D координаты точки в Normalized Device Coordinates (NDC пространство) в которую выпускается луч. Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).\
`camera` -- камера, используемая для определения положения начала луча, и для перевода Normalized Device Coordinates (NDC пространство) в мировые координаты. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).\
`options` -- параметры проверки пересечений, необязательный параметр. Подробнее: [SceneCheckOptions](#SceneCheckOptions), [ModelCheckOptions](#ModelCheckOptions).\
Возвращает объект `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает `undefined`.


###  getIntersectionIDByFrustumNdcPt() {#getIntersectionIDByFrustumNdcPt}
Метод возвращает список `modelId` и `entityGuid` объектов модели, пересекаемых усеченной пирамидой (Frustum).
```js
  getIntersectionIDByFrustumNdcPt(ndcFrustumBox: THREE.Box3, unProjMatrix: THREE.Matrix4, isContainsOnly: boolean, options?: TOptions): { modelId: string; guid: string; }[];
```
где:

`ndcFrustumBox` -- Представление `Frsutum` в Normalized Device Coordinates (NDC пространство). Подробнее: [THREE.Box3](https://threejs.org/docs/?q=Box3#api/en/math/Box3).\
`unProjMatrix` -- Матрица проекции координат Normalized Device Coordinates (NDC пространство) в мировые координаты. Подробнее: [THREE.Matrix4](https://threejs.org/docs/#api/en/math/Matrix4).\
`isContainsOnly` -- если `true`, то отбрасываются не полностью содержащиеся внутри пирамиды объекты. В противном случае в вывод включаются как содержащиеся внутри пирамиды объекты, так и касающиеся или пересекающиеся с ней.\
`options` -- параметры проверки пересечений, необязательный параметр. Подробнее: [SceneCheckOptions](#SceneCheckOptions), [ModelCheckOptions](#ModelCheckOptions).\
Если при расчёте учитываются секущие плоскости, то `isContainsOnly` также указывает на то, что объект не должен быть обрезан секущими.\

Возвращает список объектов `{ modelId: string, guid: string }`, если пресечение существует. В противном случае возвращает пустой массив.

Пример расчёта пересечений с `Frustum`, образованным областью видимости камеры:
```js
  const camera = viewer3D.navigation.getCamera();
  const unprojectionMatrix = new THREE.Matrix4();
  const ndcFrustumBox = new THREE.Box3();
  //матрица проекции из Normalized Device Coordinates (NDC пространство) в мировые координаты:
  unprojectionMatrix.multiplyMatrices(camera.matrixWorld, camera.projectionMatrixInverse);
  //левый нижний угол усеченной пирамиды в Normalized device coordinates (NDC пространство: x=-1, y=-1), ближняя плоскость камеры (nearPlane): z = -1:
  ndcFrustumBox.min = new THREE.Vector3(-1, -1, -1);
  //правый верхний угол усеченной пирамиды в Normalized device coordinates (NDC пространство: x=1, y=1), дальняя плоскость камеры (farPlane): z = 1:
  ndcFrustumBox.max = new THREE.Vector3(1, 1, 1);

  //Находим все объекты содержащиеся внутри и/или пересекающие усечённую пирамиду, без учета секущих плоскостей.
  const intersections = intersectionChecker.getIntersectionIDByFrustumNdcPt(ndcFrustumBox, unprojectionMatrix, false, false);
```
Более сложный пример использования: [BoxSelectionExtension](../../../extensions3d/BoxSelection).


# ISceneIntersectionChecker {#ISceneIntersectionChecker}
**ISceneIntersectionChecker** -- интерфейс обработки пересечений объектов на отдельной сцене. Расширяет `IIntersectionChecker`.
```js
  export interface ISceneIntersectionChecker extends IIntersectionChecker<SceneCheckOptions> {
    /** Возвращает ограничивающий объём сцены. */
    get boundingBox(): THREE.Box3;
  }
```

## SceneCheckOptions  {#SceneCheckOptions}
**SceneCheckOptions** -- опции проверки пересечений для `ISceneIntersectionChecker`.
```js
  export interface SceneCheckOptions {
    /** Определяет учитываются ли секущие плоскости при расчете пересечений на данной сцене.
     *  Если учитываются, то пересечения с объектами за пределами секущего объема отбрасываются.*/
    filterByClipping?: boolean;
  }
```

# IModelIntersectionChecker {#IModelIntersectionChecker}
**IModelIntersectionChecker** -- интерфейс обработки пересечений всех объектов модели. Расширяет `IIntersectionChecker`.
```js
  export interface IModelIntersectionChecker extends IIntersectionChecker<ModelCheckOptions> {
    /** Возвращает ограничивающий объём всей модели. */
    get boundingBox(): THREE.Box3;
    /** Возвращает центр ограничивающего объёма модели. */
    get modelCenter(): THREE.Vector3;
  }
```

## ModelCheckOptions  {#ModelCheckOptions}
**ModelCheckOptions** -- опции проверки пересечений для `IModelIntersectionChecker`.
```js
  export interface ModelCheckOptions extends SceneCheckOptions {
    /** Наименования сцен, которые участвуют в проверке пересечений.
     *  Если не задано, то пересечения проверяются для всех сцен. */
    sceneNames?: string[],
  }
```