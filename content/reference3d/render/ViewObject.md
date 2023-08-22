---
title: "ViewObject"
draft: false
weight: 9
---

**ViewObject** -- абстрактный класс, описывающий объект на сцене. Расширяет [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D).

```js
export abstract class ViewObject extends THREE.Object3D {
  readonly entityGuid: string;
  readonly modelGuid: string;

  constructor(entityGuid?: string, modelGuid?: string, color?: Color);

  abstract get mesh(): THREE.Mesh | null;
  abstract get edges(): THREE.LineSegments | null;
  setVisible(iVal: boolean): void;
  isVisible(): boolean;
  setHidden(iVal: boolean): void;
  isHidden(): boolean;
  setSelected(iVal: boolean): void;
  isSelected(): boolean;
  setHovered(iVal: boolean): void;
  isHovered(): boolean;
  setColor(color: Color): void;
  resetColor(): void;
  getOriginalColor(): Color;
  dispose(): void;

  getBoundingBox(): THREE.Box3;
  raycast(iRaycaster: THREE.Raycaster, oIntersects: THREE.Intersection[]): void;

  protected setHoveredForObject(iVal: boolean): void;
  protected setSelectedForObject(iVal: boolean): void;
  protected setHiddenForObject(iVal: boolean): void;
  protected setVisibleForObject(iVal: boolean): void;
  protected setColorForObject(color: Color): void;
  protected resetColorForObject(): void;

  protected riseOnUpdated(updateType?: UpdateType, object?: THREE.Object3D): void;
}
```

## Конструктор
```js
  constructor(entityGuid?: string, modelGuid?: string, color?: Color);
```
где:
`entityGuid`-- идентификатор объекта модели, которому соответствует `ViewObject`. Опциональный параметр, если не задан, то объекту присваивается нулевой guid. Подробнее: [ModelElement.id](../../ModelElement#id).\
`modelGuid` -- идентификатор части модели, к которой относится объект модели. Опциональный параметр, если не задан, то объекту присваивается нулевой guid. Подробнее: [ModelElement.modelPartId](../../ModelElement#modelPartId).\
`color` -- начальный цвет объекта. Опциональный параметр, если не задан, то объекту присваивается цвет по умолчанию - `new Color(1, 1, 1, 1)`. Подробнее: [Color](../Color).

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
Используется для отрисовки объекта при выделении (Hover/Select), и при [расчёте пересечений](../IModelIntersectionChecker#getIntersectionIDByFrustumNdcPt) с `Frustum`.
```js
  abstract get mesh(): THREE.Mesh | null;
```

###  get edges()
Геометрическое представление `ViewObject` в виде `THREE.LineSegments`. Подробнее: [THREE.LineSegments](https://threejs.org/docs/#api/en/objects/LineSegments).\
Используется для отрисовки объекта при выделении (Hover/Select), и при [расчёте пересечений](../IModelIntersectionChecker#getIntersectionIDByFrustumNdcPt) с `Frustum`.
```js
  abstract get edges(): THREE.LineSegments | null;
```

## Методы

### setVisible()
Метод управляет видимостью объекта на сцене.
```js
setVisible(iVal: boolean): void;
```
где:
`iVal` -- видимость объекта.

### isVisible()
Метод проверяет видимость объекта на сцене.
```js
isVisible(): boolean;
```
Вовзращает `true`, если объект виден. В противном случае возвращает `false`.

### setHidden()
Метод управляет скрытием объекта со сцены. Скрытие объектов используется только для ускорения отрисовки сцены и не влияет на проверку пересечений.
```js
setHidden(iVal: boolean): void;
```
где:
`iVal` -- скрыт ли объект.

### isHidden()
Метод проверяет видимость объекта на сцене.
```js
isHidden(): boolean;
```
Вовзращает `true`, если объект скрыт. В противном случае возвращает `false`.

### setSelected()
Метод управляет селектированием объекта.
```js
setSelected(iVal: boolean): void;
```
где:
`iVal` -- выбран ли объект.

### isSelected()
Метод проверяет селектирование объекта.
```js
isSelected(): boolean;
```
Вовзращает `true`, если объект выбран. В противном случае возвращает `false`.

### setHovered()
Метод управляет ховером объекта.
```js
setHovered(iVal: boolean): void;
```
где:
`iVal` -- активность ховера над объектом.

### isHovered()
Метод проверяет активность ховера над объектом.
```js
isHovered(): boolean;
```
Вовзращает `true`, если ховер активен. В противном случае возвращает `false`.

### setColor()
Метод задает цвет объекта.
```js
setColor(color: Color): void;
```
где:
`color` -- цвет объекта. Подробнее: [Color](../Color).

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
Вовзвращает объект типа [Color](../Color).

### dispose()
Метод освообождает ресурсы, выделенные `ViewObject`.
```js
dispose(): void;
```

### getBoundingBox()
Метод возвращает граничный объём `ViewObject`.\
Реализация по умолчания возвращает пустой `THREE.Box3`. Метод доступен для переопределения.
```js
 getBoundingBox(): THREE.Box3;
```
Вовзвращает объект типа [THREE.Box3](https://threejs.org/docs/#api/en/math/Box3).

### raycast()
Метод вычисляет пересечение `ViewObject` с лучом.\
Для расчета пересечений на сцене, должен быть переопределён в подклассах.\
Метод пустой по умолчанию, доступен для переопределения.
Подробнее: [THREE.Object3D.raycast](https://threejs.org/docs/index.html#api/en/core/Object3D.raycast)
```js
 raycast(iRaycaster: THREE.Raycaster, oIntersects: THREE.Intersection[]): void;
```

### protected setHoveredForObject()
Метод описывает поведение объекта при ховере.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setHoveredForObject(iVal: boolean): void;
```
где:
`iVal` -- активность ховера над объектом.

### protected setSelectedForObject()
Метод описывает поведение объекта при селекте.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setSelectedForObject(iVal: boolean): void;
```
где:
`iVal` -- значение селекта над объектом.

### protected setHiddenForObject()
Метод описывает поведение объекта при скрытии.\
Реализация по умолчанию работает только для объектов на основной сцене `MainScene`. Метод доступен для переопределения.
```js
protected setHiddenForObject(iVal: boolean): void;
```
где:
`iVal` -- видимость объекта на сцене.

### protected setVisibleForObject()
Метод описывает поведение объекта при изменении видимости.\
Реализация по умолчанию использует свойство [Object3D.visibility](https://threejs.org/docs/index.html#api/en/core/Object3D.visible). Метод доступен для переопределения.
```js
protected setVisibleForObject(iVal: boolean): void;
```
где:
`iVal` -- видимость объекта на сцене.

### protected setColorForObject() {#setColorForObject}
Метод описывает поведение объекта при изменении цвета.\
Метод пустой по умолчанию, доступен для переопределения.
```js
protected setColorForObject(color: Color): void;
```
где:
`color` -- цвет объекта. Подробнее: [Color](../Color).

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
где:
`updateType` -- тип обновления. Подробнее: [UpdateType](../UpdateType).\
`object` -- объект, источник обновения. По умолчанию текущий объект.

  ```js
  // При изменении дочерних объектов, которые не являются `ViewObject`,
  // для оповещения об их изменениях можно использовать `riseOnUpdated` родительского объекта.

  // При изменении видимости текущего объекта:
  this.visible = false;
  // Опопвещам об изменениях:
  this.riseOnUpdated(UpdateType.Visibility);
  // Эквивалентно вызову:
  this.dispatchEvent({ type: 'update', updateType: UpdateType.Visibility });

  // При изменении видимости дочернего объекта:
  childMesh.visibility = false;
  // Опопвещам об изменениях:
  this.riseOnUpdated(UpdateType.Visibility, childMesh);
  // Эквивалентно вызову:
  childMesh.dispatchEvent({ type: 'update', updateType: UpdateType.Visibility });
  ```