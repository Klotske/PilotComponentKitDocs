---
title: "IUserScene"
draft: false
weight: 9
---

## IUserScene {#IUserScene}
**IUserScene** -- интерфейс, позволяющий взаимодействовать со сценой.

```js
export interface IUserScene {
  readonly name: string;
  get needsUpdate(): boolean;
  get needsRedraw(): boolean;
  get intersectionChecker(): IModelIntersectionChecker | null;
  get threeObjectRepresentation(): THREE.Object3D | null;

  addRange(objects: THREE.Object3D[]): void;
  updateRange(objects: TPair<THREE.Object3D, UpdateType>[]): void;
  removeRange(objects: THREE.Object3D[]): void;
  has(obj: THREE.Object3D): boolean;
  traverse(callback: (object: THREE.Object3D) => void): void;
  setClipping(planes: THREE.Plane[]): void;
  manageScene(context?: IRenderOperationContext): boolean;
  render(context: IRenderOperationContext): void;
  clear(): void;
  dispose(): void;
}
```

## Поля

### readonly name: string
Имя сцены.
```js
readonly name: string;
```

## Свойства

###  get needsUpdate(): boolean
Показывает, нужно ли обновить сцену.
```js
 get needsUpdate(): boolean;
```
Возвращает `true`, если нужно обновить сцену, в противном случае `false`.

###  get needsRedraw(): boolean
Показывает, нужно ли перерисовать сцену.
```js
  get needsRedraw(): boolean;
```
Возвращает `true`, если нужно перерисовать сцену, в противном случае `false`.

###  get intersectionChecker(): IModelIntersectionChecker
Предоставляет [IModelIntersectionChecker](../IModelIntersectionChecker) - интерфейс обработки пересечений, для данной сцены.
```js
  get intersectionChecker(): IModelIntersectionChecker | null;
```
Если проверка пересечений на сцене поддерживается, то возвращается интерфейс обработки пересечений. В противном случае возвращается `null`. Подробнее смотри  [IModelIntersectionChecker](../IModelIntersectionChecker).

###  get threeObjectRepresentation(): THREE.Object3D
Представление сцены в виде иерархии [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D) объектов.\
Используется для построения визуального дерева, не используется в рендере.
```js
  get threeObjectRepresentation(): THREE.Object3D | null;
```
Возвращает [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D), если сцена поддерживает такое представление. В противном случае возвращается `null`.

## Методы

### addRange(objects: THREE.Object3D[]): void
Метод позволяет добавить коллекцию объектов на сцену.
```js
addRange(objects: THREE.Object3D[]): void;
```
где:
`objects` -- список объектов для добавления на сцену. Подробнее смотри [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).

###  updateRange(objects: TPair<THREE.Object3D, UpdateType>[]): void
Метод позволяет обновить объекты на сцене.
```js
  updateRange(objects: TPair<THREE.Object3D, UpdateType>[]): void;
```
где:
`objects` -- список объектов для обновления. Каждый элемент списка является парой из самого объекта и соответствующего ему типа обновления.
Подробнее смотри [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D), [TPair](../common/TPair), [UpdateType](../UpdateType).

###  removeRange(objects: THREE.Object3D[]): void
Метод позволяет удалить коллекцию объектов со сцены.
```js
removeRange(objects: THREE.Object3D[]): void;
```
где:
`objects` -- список объектов для удаления. Подробнее смотри [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).

###  has(obj: THREE.Object3D): boolean
Метод показывает добавлен ли объект на сцену.
```js
has(obj: THREE.Object3D): boolean;
```
где:
`objects` -- проверяемый объект. Подробнее смотри [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).\
Вовзвращает `true`, если объект добавлен на сцену. В противном случае `false`.


###  traverse(callback: (object: THREE.Object3D) => void): void
Метод осуществляет перебор объектов на сцене.
```js
traverse(callback: (object: THREE.Object3D) => void): void;
```
где:
`callback` -- функция вызываемая для всех объектов на сцене.

###  setClipping(planes: THREE.Plane[]): void;
Метод задает плоскости сечения для данной сцены.
```js
setClipping(planes: THREE.Plane[]): void;
```
где:
`planes` -- список плоскостей сечения. Подробнее смотри [THREE.Plane](https://threejs.org/docs/#api/en/math/Plane).

###  manageScene(context?: IRenderOperationContext): boolean
Метод передает управление сцене для обработки изменений на сцене, для работы алгоритмов оптимизации отрисовки, для работы алгоритмов оптимизации проверки пересечений и т.д.
```js
manageScene(context?: IRenderOperationContext): boolean;
```
где:
`context` -- контекст операции рендера. Подробнее смотри [IRenderOperationContext](../IRenderOperationContext).
Вовзвращает `true`, если все запланированные операции на сцене были выполнены. Возвращает `false`, если требуется повторная передача управления.

###  render(context: IRenderOperationContext): void
Метод выполняет отрисовку сцены в данном [контексте](../IRenderOperationContext).
```js
render(context: IRenderOperationContext): void;
```
где:
`context` -- контекст операции рендера. Подробнее смотри [IRenderOperationContext](../IRenderOperationContext).

###  clear(): void
Метод удаляет все объекты со сцены, за исключением [объектов освещения](https://threejs.org/docs/?q=Light#api/en/lights/Light), добавляемых по умолчанию.
```js
clear(): void;
```

###  dispose(): void
Метод  удаляет все объекты со сцены, и освобождает все ресурсы сцены.
```js
dispose(): void;
```
