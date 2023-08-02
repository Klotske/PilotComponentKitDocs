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
  set clippingEnable(value: boolean);
  get clippingEnable(): boolean;

  addRange(objects: THREE.Object3D[]): void;
  updateRange(objects: TPair<THREE.Object3D, UpdateType>[]): void;
  removeRange(objects: THREE.Object3D[]): void;
  has(obj: THREE.Object3D): boolean;
  traverse(callback: (object: THREE.Object3D) => void): void;
  setClipping(planes: THREE.Plane[]): void;
  manageScene(context?: IRenderOperationContext): boolean;
  render(context: IRenderOperationContext): void;
  clear(): void;
}
```

## Поля

### readonly name
Имя сцены.
```js
readonly name: string;
```

## Свойства

###  get needsUpdate()
Показывает нужно ли обновить сцену.
```js
 get needsUpdate(): boolean;
```
Возвращает `true`, если нужно обновить сцену, в противном случае `false`.

###  get needsRedraw()
Показывает нужно ли перерисовать сцену.
```js
  get needsRedraw(): boolean;
```
Возвращает `true`, если нужно перерисовать сцену, в противном случае `false`.

###  get intersectionChecker()
Предоставляет [IModelIntersectionChecker](../IModelIntersectionChecker) - интерфейс обработки пересечений для данной сцены.
```js
  get intersectionChecker(): IModelIntersectionChecker | null;
```
Если проверка пересечений на сцене поддерживается, то возвращается интерфейс обработки пересечений. В противном случае возвращается `null`. Подробнее:  [IModelIntersectionChecker](../IModelIntersectionChecker).

###  get threeObjectRepresentation()
Представление сцены в виде иерархии [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D) объектов.\
Используется для построения визуального дерева, не используется в рендере.
```js
  get threeObjectRepresentation(): THREE.Object3D | null;
```
Возвращает [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D), если сцена поддерживает такое представление. В противном случае возвращается `null`.

###  get clippingEnable()
Показывает влияют ли секущие плоскости на отрисовку и проверку пересечений на данной сцене.
```js
  get clippingEnable(): boolean;
```
Возвращает `true`, если секущие плоскости влияют на отрисовку и проверку пересечений на данной сцене.

###  set clippingEnable()
Включает или выключает влияние секущих плоскостей на отрисовку и проверку пересечений на данной сцене.
```js
  set clippingEnable(value: boolean);
```
где:
`value` -- параметр. Если `value` равен `true`, то объекты на сцене обрезаются секущими плоскостями, а также при проверке пересечений на данной сцене не учитываются отсечённые объекты. 

## Методы

### addRange()
Метод добавляет список объектов на сцену.
```js
addRange(objects: THREE.Object3D[]): void;
```
где:
`objects` -- список объектов для добавления на сцену. Подробнее: [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).

###  updateRange()
Метод обновляет объекты на сцене.
```js
  updateRange(objects: TPair<THREE.Object3D, UpdateType>[]): void;
```
где:
`objects` -- список объектов для обновления. Каждый элемент списка является парой из самого объекта и соответствующего ему типа обновления.
Подробнее: [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D), [UpdateType](../UpdateType).

###  removeRange()
Метод удаляет список объектов со сцены.
```js
removeRange(objects: THREE.Object3D[]): void;
```
где:
`objects` -- список объектов для удаления. Подробнее: [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).

###  has()
Метод показывает добавлен ли объект на сцену.
```js
has(obj: THREE.Object3D): boolean;
```
где:
`objects` -- проверяемый объект. Подробнее: [THREE.Object3D](https://threejs.org/docs/#api/en/core/Object3D).\
Вовзвращает `true`, если объект добавлен на сцену. В противном случае `false`.


###  traverse()
Метод осуществляет перебор объектов на сцене.
```js
traverse(callback: (object: THREE.Object3D) => void): void;
```
где:
`callback` -- функция вызываемая для всех объектов на сцене.

###  setClipping()
Метод задает плоскости сечения для данной сцены.
```js
setClipping(planes: THREE.Plane[]): void;
```
где:
`planes` -- список плоскостей сечения. Подробнее: [THREE.Plane](https://threejs.org/docs/#api/en/math/Plane).

###  manageScene()
Метод передает управление сцене для выполнения внутренних операций: обработки изменений на сцене, оптимизации отрисовки, оптимизации проверки пересечений и т.д.
```js
manageScene(context?: IRenderOperationContext): boolean;
```
где:
`context` -- контекст операции рендера. Подробнее: [IRenderOperationContext](../IRenderOperationContext).
Вовзвращает `true`, если все запланированные операции на сцене были выполнены. Возвращает `false`, если требуется повторная передача управления.

###  render()
Метод выполняет отрисовку сцены в данном [контексте](../IRenderOperationContext).
```js
render(context: IRenderOperationContext): void;
```
где:
`context` -- контекст операции рендера. Подробнее: [IRenderOperationContext](../IRenderOperationContext).

###  clear()
Метод удаляет все объекты со сцены, за исключением объектов [THREE.Light](https://threejs.org/docs/?q=Light#api/en/lights/Light), добавляемых по умолчанию.
```js
clear(): void;
```

