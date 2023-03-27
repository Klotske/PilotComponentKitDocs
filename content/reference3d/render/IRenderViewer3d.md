---
title: "IRenderViewer3D"
draft: false
weight: 9
---

## IRenderViewer3D {#IRenderViewer3D}
**IRenderViewer3D** -- интерфейс, для работы с отрисовкой сцен и объектами на сцене.

```js
export interface IRenderViewer3D {
  getIntersectionChecker(): IModelIntersectionChecker;
  updateCurrentCanvas(): Promise<void>;
  placeObjectOnScene(iObj: THREE.Object3D, sceneID?: string): Promise<void>;
  removeObjectFromScene(iObj: THREE.Object3D): Promise<void>;
  setClipping(planes: THREE.Plane[], sceneID?: string): void;
  getScenes(): IUserScene[];
}
```

## Методы

### getIntersectionChecker()
Предоставляет [IModelIntersectionChecker](../IModelIntersectionChecker) - интерфейс обработки пересечений для всех сцен.
```js
getIntersectionChecker(): IModelIntersectionChecker;
```
Возвращается интерфейс обработки пересечений. Подробнее:  [IModelIntersectionChecker](../IModelIntersectionChecker).

### updateCurrentCanvas()
Метод вызывает полную перерисовку сцен.
```js
updateCurrentCanvas(): Promise<void>;
```

###  placeObjectOnScene()
Метод помещает объект на определённую сцену.
```js
 placeObjectOnScene(iObj: THREE.Object3D, sceneID?: string): Promise<void>;
```
где:\
`iObj` -- объект, который нужно поместить на сцену.\
`sceneID` -- Имя сцены. Не обязательный параметр. По умолчанию `MainScene`.

###  removeObjectFromScene()
Метод удаляет объект со сцены.
```js
  removeObjectFromScene(iObj: THREE.Object3D): Promise<void>;
```
где:\
`iObj` -- объект, который нужно удалить.

###  setClipping()
Метод задает плоскости сечения для определённой сцены.
```js
setClipping(planes: THREE.Plane[], sceneID?: string): void;
```
где:\
`planes` -- список плоскостей сечения. Подробнее: [THREE.Plane](https://threejs.org/docs/#api/en/math/Plane).\
`sceneID` -- Имя сцены. Не обязательный параметр. По умолчанию `MainScene`.

###  getScenes()
Метод возвращает список всех используемых сцен.
```js
  getScenes(): IUserScene[];
```
Возвращает список сцен. Подробнее: [IUserScene](../IUserScene).