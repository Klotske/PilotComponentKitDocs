---
title: "MeshPoints"
draft: false
weight: 9
---

**MeshPoints** -- класс, описывающий точки для отрисовки в виде полигональной сетки. Расширяет [THREE.Mesh](https://threejs.org/docs/#api/en/objects/Mesh).

```js
export class MeshPoints extends THREE.Mesh {

  constructor();

  geometry: THREE.InstancedBufferGeometry;

  material: MeshPointMaterial;

  color: Color;

  pointSize: number;

  addPoint(pointParameter?: MeshPointParameter): number;

  updatePoint(index: number, pointParameter: MeshPointParameter): void;

  removePoint(index: number): void;

  updateAttributes(): void;

  dispose(): void;
}
```

## Конструктор
```js
  constructor();
```

## Поля

### geometry: THREE.InstancedBufferGeometry
Геометрия, используемая для отрисовки единичной точки. Все добавленные точки будут отрисованы на сцене с помощью данной геометрии.
```js
  get geometry(): THREE.InstancedBufferGeometry;
  set geometry(value: THREE.InstancedBufferGeometry);
```
По умолчанию используется геометрия круга. Подробнее: [THREE.InstancedBufferGeometry](https://threejs.org/docs/#api/en/core/InstancedBufferGeometry).

### material: MeshPointMaterial
Материал точек для отрисовки.
```js
  get material(): MeshPointMaterial;
  set material(value: MeshPointMaterial);
```
По умолчанию: `new MeshPointMaterial({ sizeAttenuation: false, transparent: true, depthTest: false })`. Подробнее: [MeshPointMaterial](#MeshPointMaterial).

### color: Color {#color}
Задает или возвращает значение цвета точек по умолчанию. Если цвет точки не задан при добавлении, будет использоваться именно это значение.
```js
  get color(): Color;
  set color(value: Color);
```
По умолчанию: `new Color( 1, 1, 1, 1 )`. Подробнее: [Color](../Color).

### pointSize: number {#pointSize}
Задает или возвращает размер точки в пикселях по умолчанию. Если размер точки не задан при добавлении, будет использоваться именно это значение.
```js
  get pointSize(): string;
  set pointSize(value: string);
```
По умолчанию: `1`.

### point: number {#point}
Задает или возвращает позицию новой точки по умолчанию. Если позиция точки не задана при добавлении, будет использоваться именно это значение.
```js
  get point(): THREE.Vector3;
  set point(value: THREE.Vector3);
```
По умолчанию: `new THREE.Vector3(0, 0, 0)`. Подробнее [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

## Методы

### addPoint()
Метод добавляет точку для отрисовки с заданными параметрами. По окончанию добавления точек необходимо обновить атрибуты геометрии с помощью метода [updateAttributes](#updateAttributes).
```js
  addPoint(pointParameter?: MeshPointParameter): number;
```
где:
`pointParameter` -- параметры точки. Подробнее: [MeshPointParameter](#MeshPointParameter).\
Возвращает порядковый номер добавленной точки.

### updatePoint() {#updatePoint}
Метод обновляет параметры точки.
```js
  updatePoint(index: number, pointParameter: MeshPointParameter): void;
```
где:
`index` -- порядковый номер добавленной точки.\
`pointParameter` -- обновлённые параметры точки. Допустимо определять внутри `pointParameter` только изменившиеся параметры точки. Например, для изменения цвета достаточно передать `{ color : newColor }`, при этом позиция точки и её размер останутся неизменными. Подробнее: [MeshPointParameter](#MeshPointParameter).

### removePoint()
Метод удаляет точку. По окончанию удаления точек необходимо обновить атрибуты геометрии с помощью метода [updateAttributes](#updateAttributes).
```js
  removePoint(index: number): void;
```
где:
`index` -- порядковый номер точки.

### updateAttributes() {#updateAttributes}
Метод обновляет атрибуты геометрии. Необходимо вызывать по окончанию добавления либо удаления точек.
```js
  updateAttributes(): void;
```

### dispose()
Метод освобождает ресурсы выделенные `MeshPoints`.
```js
dispose(): void;
```

## MeshPointParameter {#MeshPointParameter}
Параметры точки в `MeshPoints`.
```js
export interface MeshPointParameter {
  point?: THREE.Vector3,
  color?: Color,
  size?: number
}
```
где:
`point` -- позиция точки в мировых координатах, опциональный параметр. Если не задан, будет использоваться [положение по умолчанию](#point). Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).\
`color` -- цвет точки, опциональный параметр. Если не задан, будет использоваться [цвет по умолчанию](#color). Подробнее: [Color](../Color).\
`size` -- размер точки в пикселях, опциональный параметр. Если не задан, будет использоваться [размер по умолчанию](#pointSize).


## MeshPointMaterial {#MeshPointMaterial}
Материал, используемый для отрисовки точек в виде полигональной сетки. Расширяет [THREE.ShaderMaterial](https://threejs.org/docs/#api/en/materials/ShaderMaterial).

```js
export class MeshPointMaterial extends CustomMaterial {;
  constructor(parameters?: MeshPointMaterialParameters);

  sizeAttenuation: boolean;

  get resolution(): THREE.Vector2;
  set resolution(value: THREE.Vector2);
}
```

## Конструктор
```js
  constructor(parameters?: MeshPointMaterialParameters);
```
где:
`parameters` -- параметры материала. Опциональный параметр. Подробнее: [MeshPointMaterialParameters](#MeshPointMaterialParameters); 

## Поля

###  sizeAttenuation: boolean
Задает значение флага, показывающего влияние перспективы на точки - уменьшается ли размер точки с глубиной кадра.
Влияет на отображение только с перспективной камерой.
```js
  sizeAttenuation: boolean;

```
По умолчанию: `true` - размер точки зависит от перспективы.

## Свойства

### resolution: THREE.Vector2
Задает и получает размеры области отрисовки. Нужно для корректной отрисовки точек в `sizeAttenuation = false` режиме. Данное свойство обновляется автоматически перед отрисовкой.
```js
  get resolution(): THREE.Vector2;
  set resolution(value: THREE.Vector2);
```
Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).


## MeshPointMaterialParameters {#MeshPointMaterialParameters}
Параметры `MeshPointMaterial`. Задают соответствующее свойства [MeshPointMaterial](#MeshPointMaterial).
```js
export interface MeshPointMaterialParameters extends THREE.ShaderMaterialParameters {
  sizeAttenuation?: boolean | undefined;
}
```
