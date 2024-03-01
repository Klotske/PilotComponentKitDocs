---
title: "IRenderViewer3D"
draft: false
weight: 9
---

## IRenderViewer3D {#IRenderViewer3D}
**IRenderViewer3D** -- интерфейс для работы с отрисовкой сцен и объектами на сцене.

```js
export interface IRenderViewer3D {
  getIntersectionChecker(): IModelIntersectionChecker;
  updateCurrentCanvas(): Promise<void>;
  placeObjectOnScene(iObj: THREE.Object3D, sceneID?: string, redraw?: boolean): Promise<void>;
  removeObjectFromScene(iObj: THREE.Object3D, redraw?: boolean): Promise<void>;
  setClipping(planes: THREE.Plane[], sceneID?: string): void;
  setActiveClipPlaneIndices(indices: number[]): void;
  getScenes(): IUserScene[];
  addScene(name: string, isClippable: boolean): IUserScene;
  removeScene(scene: IUserScene): void;
}
```

## Методы

### getIntersectionChecker()
Предоставляет [IModelIntersectionChecker](../IntersectionChecker#IModelIntersectionChecker) -- интерфейс обработки пересечений для всех сцен.
```js
getIntersectionChecker(): IModelIntersectionChecker;
```
Возвращает интерфейс обработки пересечений. Подробнее:  [IModelIntersectionChecker](../IntersectionChecker#IModelIntersectionChecker).

### updateCurrentCanvas()
Метод вызывает полную перерисовку сцен.\
Если параметр `force` установлен в `true`, то отрисовка кадра произойдёт после принудительного обновления сцен.
```js
updateCurrentCanvas(force?: boolean): Promise<void>;
```
где:\
`force` -- флаг, указывающий на принудительное обновление сцен. По умолчанию -- `false`.

###  placeObjectOnScene()
Метод помещает объект на определённую сцену.
```js
 placeObjectOnScene(iObj: THREE.Object3D, sceneID?: string, redraw?: boolean): Promise<void>;
```
где:\
`iObj` -- объект, который нужно поместить на сцену.\
`sceneID` -- имя сцены. Необязательный параметр. По умолчанию -- `MainScene`.\
`redraw` -- флаг, указывающий на принудительную перерисовку сцен после добавления объекта. По умолчанию -- `false`.

###  removeObjectFromScene()
Метод удаляет объект со сцены.
```js
  removeObjectFromScene(iObj: THREE.Object3D, redraw?: boolean): Promise<void>;
```
где:\
`iObj` -- объект, который нужно удалить.\
`redraw` -- флаг, указывающий на принудительную перерисовку сцен после удаления объекта. По умолчанию -- `false`.

###  setClipping() {#setClipping}
Метод задает секущие плоскости для визулизации.
```js
setClipping(planes: THREE.Plane[]): void;
```
где:\
`planes` -- список плоскостей сечения. Подробнее: [THREE.Plane](https://threejs.org/docs/#api/en/math/Plane).

###  setActiveClipPlaneIndices()
Метод задает активные плоскости сечения. Сечения активных плоскостей окрашены в голубой цвет.
```js
setActiveClipPlaneIndices(indices: number[]): void;
```
где:\
`indices` -- список индексов активных плоскостей сечения. Каждый индекс указывает на плоскость в списке, переданном в [setClipping()](#setClipping).

###  getScenes()
Метод возвращает список всех используемых сцен.
```js
  getScenes(): IUserScene[];
```
Возвращает список сцен. Подробнее: [IUserScene](../IUserScene).

###  addScene()
Метод добавляет новую сцену для отрисовки.
```js
  addScene(name: string, isClippable: boolean): IUserScene;
```
где:\
`name` -- идентификатор новой сцены.

`isClippable` -- параметр, указывающий, влияют ли секущие плоскости на отрисовку этой сцены. Если `false`, то секущие плоскости не применяются к объектам на этой сцене и проверка пересечений с объектами на этой сцене также не учитывает секущие плоскости.
Возвращает добавленную сцену. Подробнее: [IUserScene](../IUserScene).

###  removeScene()
Метод удаляет сцену из списка используемых для отрисовки сцен.
```js
  removeScene(scene: IUserScene): void;
```
где:\
`scene` -- сцена для удаления. Подробнее: [IUserScene](../IUserScene).