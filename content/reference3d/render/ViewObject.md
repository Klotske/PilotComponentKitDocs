---
title: "ViewObject"
draft: false
weight: 9
---

## ViewObjectEventMap
**ViewObjectEventMap** -- события ViewObject.

```js
export interface ViewObjectEventMap extends THREE.Object3DEventMap {
  // событие уничтожения объекта
  dispose: {},
  // событие изменения объекта
  update: { updateType: UpdateType },
}
```
При изменении объекта подписчикам также сообщается тип изменения. Подробнее: [UpdateType](../UpdateType).

## ViewObject
**ViewObject** -- абстрактный класс, описывающий объект на сцене. Расширяет [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D).

```js
export abstract class ViewObject extends THREE.Object3D<ViewObjectEventMap> {
  readonly entityGuid: string;
  readonly modelGuid: string;

  constructor(entityGuid?: string, modelGuid?: string, color?: Color);

  abstract get mesh(): THREE.Mesh | null;
  abstract get edges(): THREE.LineSegments | null;
  setVisible(value: boolean): void;
  isVisible(): boolean;
  setHidden(value: boolean): void;
  isHidden(): boolean;
  setSelected(value: boolean): void;
  isSelected(): boolean;
  setHovered(value: boolean): void;
  isHovered(): boolean;
  setColor(color: Color): void;
  getColor(): Color;
  resetColor(): void;
  getOriginalColor(): Color;
  isGhosted(): boolean;
  setGhosted(value: boolean): void;
  dispose(): void;

  getBoundingBox(): THREE.Box3;
  raycast(iRaycaster: THREE.Raycaster, oIntersects: THREE.Intersection[]): void;

  protected setHoveredForObject(value: boolean): void;
  protected setSelectedForObject(value: boolean): void;
  protected setHiddenForObject(value: boolean): void;
  protected setVisibleForObject(value: boolean): void;
  protected setColorForObject(color: Color): void;
  protected setGhostModeForObject(value: boolean): void;
  protected resetColorForObject(): void;

  protected riseOnUpdated(updateType?: UpdateType, object?: THREE.Object3D): void;
}
```

## Конструктор
```js
  constructor(entityGuid?: string, modelGuid?: string, color?: Color);
```
где:\
`entityGuid`-- идентификатор объекта модели, которому соответствует `ViewObject`. Опциональный параметр. Если не задан, то объекту присваивается нулевой guid. Подробнее: [ModelElement.id](../../modelelement/ModelElement#id).

`modelGuid` -- идентификатор части модели, к которой относится объект модели. Опциональный параметр. Если не задан, то объекту присваивается нулевой guid. Подробнее: [ModelElement.modelPartId](../../modelelement/ModelElement#modelPartId).

`color` -- начальный цвет объекта. Опциональный параметр. Если не задан, то объекту присваивается цвет по умолчанию -- `new Color(1, 1, 1, 1)`. Подробнее: [Color](../Color).

## Поля

###  entityGuid
Идентификатор элемента модели, соответствующего этому `ViewObject`. Подробнее: [ModelElement.id](../../ModelElement#id).
```js
  readonly entityGuid: string;
```
Значение по умолчанию: `00000000-0000-0000-0000-000000000000`.

###  modelGuid
Идентификатор части модели, к которой относится элемент модели, соответствующий этому `ViewObject`. Подробнее: [ModelElement.modelPartId](../../ModelElement#modelPartId).
```js
  readonly entityGuid: string;
```
Значение по умолчанию: `00000000-0000-0000-0000-000000000000`.

## Свойства

###  get mesh()
Геометрическое представление `ViewObject` в виде `THREE.Mesh`. Подробнее: [THREE.Mesh](https://threejs.org/docs/#api/en/objects/Mesh).\
Используется для отрисовки объекта при выделении (Hover/Select) и при [расчёте пересечений](../IntersectionChecker#getIntersectionIDByFrustumNdcPt) с `Frustum`.
```js
  abstract get mesh(): THREE.Mesh | null;
```

###  get edges()
Геометрическое представление `ViewObject` в виде `THREE.LineSegments`. Подробнее: [THREE.LineSegments](https://threejs.org/docs/#api/en/objects/LineSegments).\
Используется для отрисовки объекта при выделении (Hover/Select) и при [расчёте пересечений](../IntersectionChecker#getIntersectionIDByFrustumNdcPt) с `Frustum`.
```js
  abstract get edges(): THREE.LineSegments | null;
```

## Методы

### setVisible()
Метод управляет видимостью объекта на сцене.
```js
setVisible(value: boolean): void;
```

где:

`value` -- видимость объекта.

### isVisible()
Метод проверяет видимость объекта на сцене.
```js
isVisible(): boolean;
```
Возвращает `true`, если объект виден. В противном случае возвращает `false`.

### setHidden()
Метод управляет скрытием объекта со сцены. Скрытие объектов используется только для ускорения отрисовки сцены и не влияет на проверку пересечений.
```js
setHidden(value: boolean): void;
```

где:

`value` -- скрыт ли объект.

### isHidden()
Метод проверяет видимость объекта на сцене.
```js
isHidden(): boolean;
```
Вовзращает `true`, если объект скрыт. В противном случае возвращает `false`.

### setSelected()
Метод управляет селектированием объекта.
```js
setSelected(value: boolean): void;
```

где:

`value` -- выбран ли объект.

### isSelected()
Метод проверяет селектирование объекта.
```js
isSelected(): boolean;
```
Возвращает `true`, если объект выбран. В противном случае возвращает `false`.

### setHovered()
Метод управляет ховером объекта.
```js
setHovered(value: boolean): void;
```

где:

`value` -- активность ховера над объектом.

### isHovered()
Метод проверяет активность ховера над объектом.
```js
isHovered(): boolean;
```
Возвращает `true`, если ховер активен. В противном случае возвращает `false`.

### setColor()
Метод задаёт цвет объекта.
```js
setColor(color: Color): void;
```

где:

`color` -- цвет объекта. Подробнее: [Color](../Color).

### getColor()
Метод возвращает текущий цвет объекта. Подробнее: [Color](../Color).
```js
getColor(): Color;
```

### resetColor()
Сбрасывает цвет объекта на изначальный.
```js
resetColor(): void;
```

### getOriginalColor()
Метод возвращает изначальный цвет объекта.
```js
getOriginalColor(): Color;
```
Возвращает объект типа [Color](../Color).

### isGhosted()
Метод проверяет, находится ли объект в призрачном режиме отрисовки.
```js
isGhosted(): boolean;
```

### setGhosted()
Метод задает призрачный режим отрисовки объекта -- объект рисуется бесцветным и полупрозрачным.
```js
setGhosted(value: boolean): void;
```

где:

`value` -- задаёт активность призрачного режима.

### dispose()
Метод освобождает ресурсы, выделенные `ViewObject`.
```js
dispose(): void;
```

### getBoundingBox()
Метод возвращает граничный объём `ViewObject`.\
Реализация по умолчанию возвращает пустой `THREE.Box3`. Метод доступен для переопределения.
```js
 getBoundingBox(): THREE.Box3;
```
Возвращает объект типа [THREE.Box3](https://threejs.org/docs/#api/en/math/Box3).

### raycast()
Метод вычисляет пересечение `ViewObject` с лучом.\
Для расчета пересечений на сцене должен быть переопределён в подклассах.\
Метод пустой по умолчанию, доступен для переопределения.
Подробнее: [THREE.Object3D.raycast](https://threejs.org/docs/index.html#api/en/core/Object3D.raycast)
```js
 raycast(iRaycaster: THREE.Raycaster, oIntersects: THREE.Intersection[]): void;
```

### protected setHoveredForObject()
Метод описывает поведение объекта при ховере.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setHoveredForObject(value: boolean): void;
```

где:

`value` -- активность ховера над объектом.

### protected setSelectedForObject()
Метод описывает поведение объекта при селекте.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setSelectedForObject(value: boolean): void;
```

где:

`value` -- значение селекта над объектом.

### protected setHiddenForObject()
Метод описывает поведение объекта при скрытии.\
Реализация по умолчанию работает только для объектов на основной сцене `MainScene`. Метод доступен для переопределения.
```js
protected setHiddenForObject(value: boolean): void;
```

где:

`value` -- видимость объекта на сцене.

### protected setVisibleForObject()
Метод описывает поведение объекта при изменении видимости.\
Реализация по умолчанию использует свойство [Object3D.visibility](https://threejs.org/docs/index.html#api/en/core/Object3D.visible). Метод доступен для переопределения.
```js
protected setVisibleForObject(value: boolean): void;
```

где:

`value` -- видимость объекта на сцене.

### protected setColorForObject() {#setColorForObject}
Метод описывает поведение объекта при изменении цвета.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setColorForObject(color: Color): void;
```

где:

`color` -- цвет объекта. Подробнее: [Color](../Color).

### protected setGhostModeForObject() {#setColorForObject}
Метод описывает поведение объекта в призрачном режиме.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setGhostModeForObject(value: boolean): void;
```

где:

`value` -- задаёт активность призрачного режима.

### protected resetColorForObject()
Метод описывает поведение объекта при сбрасывании цвета объекта на изначальный.\
Реализация по умолчанию использует [setColorForObject(originalColor)](#setColorForObject). Метод доступен для переопределения.
```js
protected resetColorForObject(): void;
```

### protected riseOnUpdated()
Метод сообщает подписчикам об изменении объекта. Подробнее: [EventDispatcher](https://threejs.org/docs/#api/en/core/EventDispatcher).
```js
  protected riseOnUpdated(updateType?: UpdateType, object?: THREE.Object3D): void;
```
где:\
`updateType` -- тип обновления. Подробнее: [UpdateType](../UpdateType).\
`object` -- объект, источник обновления. По умолчанию -- текущий объект.

  ```js
  // При изменении дочерних объектов, которые не являются `ViewObject`
  // для оповещения об их изменениях можно использовать `riseOnUpdated` родительского объекта.

  // При изменении видимости текущего объекта:
  this.visible = false;
  // Оповещаем об изменениях:
  this.riseOnUpdated(UpdateType.Visibility);
  // Эквивалентно вызову:
  this.dispatchEvent({ type: 'update', updateType: UpdateType.Visibility });

  // При изменении видимости дочернего объекта:
  childMesh.visibility = false;
  // Оповещаем об изменениях:
  this.riseOnUpdated(UpdateType.Visibility, childMesh);
  // Эквивалентно вызову:
  childMesh.dispatchEvent({ type: 'update', updateType: UpdateType.Visibility });
  ```