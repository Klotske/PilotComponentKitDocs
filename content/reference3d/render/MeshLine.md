---
title: "MeshLine"
draft: false
weight: 9
---

**MeshLine** -- класс описывающий линии для отрисовки в виде полигональной сетки. Расширяет [THREE.Mesh](https://threejs.org/docs/#api/en/objects/Mesh).

```js
export class MeshLine extends THREE.Mesh {
  override material: MeshLineMaterial;
  override geometry: MeshLineGeometry;

 constructor(geometry?: MeshLineGeometry, material?: MeshLineMaterial);
}
```

## Конструктор
```js
  constructor(geometry?: MeshLineGeometry, material?: MeshLineMaterial);
```
где:
`geometry` -- геометрия, опциональный параметр. Если не задано, используется пустая геометрия.\
`material` -- материал линий, опциональный параметр. Если не задано, используется материал по умолчанию.

## Поля

### material: MeshLineMaterial
Материал линий. Подробнее [MeshLineMaterial](#MeshLineMaterial).
```js
  material: MeshLineMaterial;
```

### geometry: MeshLineGeometry
Геометрия линий. Подробнее [MeshLineGeometry](#MeshLineGeometry).
```js
  geometry: MeshLineGeometry;
```


# MeshLineMaterial {#MeshLineMaterial}

**MeshLineMaterial** -- материал для отрисовки линий в виде полигональной сетки.
```js
export class MeshLineMaterial extends CustomMaterial {
  constructor(parameters: MeshLineMaterialParameters);

  get linewidth(): number;
  set linewidth(value: number);

  get opacity(): number;
  set opacity(value: number);

  get color(): THREE.Color;
  set color(value: THREE.Color);

  get worldUnits(): boolean;
  set worldUnits(value: boolean);

  get dashed(): boolean;
  set dashed(value: boolean);

  get dashScale(): number;
  set dashScale(value: number);

  get dashSize(): number;
  set dashSize(value: number);

  get dashOffset(): number;
  set dashOffset(value: number);

  get gapSize(): number;
  set gapSize(value: number);

  get resolution(): THREE.Vector2;
  set resolution(value: THREE.Vector2);
}
```

## Конструктор
```js
  constructor(parameters: MeshLineMaterialParameters);
```
где:
`parameters` -- параметры материала. Подробнее [MeshLineMaterialParameters](#MeshLineMaterialParameters).

## Свойства

### linewidth: number
Определяет значение ширины линий. В зависимости от значения [worldUnits](#worldUnits) задается в мировых координатах или в пикселях.
```js
  get linewidth(): number;
  set linewidth(value: number);
```
По умолчанию: `1`.

### opacity: number
Определяет значение прозрачности линий.
```js
  get opacity(): number;
  set opacity(value: number);
```
По умолчанию: `1`.

### color: Color {#color}
Определяет значение цвета линий.
```js
  get color(): Color;
  set color(value: Color);
```
По умолчанию: `new Color( 1, 1, 1, 1 )`. Подробнее: [Color](../Color).

### worldUnits: boolean {#worldUnits}
Определяет в каком пространстве задана ширина линий. Если `true`, то ширина линий задана в мировых координтах и на линию будет влиять перспектива - размер линии будет уменьшаться с глубиной кадра. В противном случае, размер линии считается в пикселях и остаетя неизменным, переспектива не оказывает влияния на ширину линиии.
```js
  get worldUnits(): boolean;
  set worldUnits(value: boolean);
```
По умолчанию: `true`.

### dashed: boolean
Определяет является ли линия пунктирной.
```js
  get dashed(): boolean;
  set dashed(value: boolean);
```
По умолчанию: `false`.

### dashScale: boolean
Определяет коэффициент-делитель для пунктира. Длина пунктирного отрезка (длина штриха + длина пустого промежутка) делится на данный коэффициент.\
Нпример значение `dashScale = 2` приведёт к уменьшению длины пунктирного отрезка в два раза и соответственному увеличению частоты штрихов в линии, тоже в два раза.
```js
  get dashScale(): number;
  set dashScale(value: number);
```
По умолчанию: `1`.

### dashSize: boolean
Определяет длину штриха в пунктирном отрезке.
```js
  get dashSize(): number;
  set dashSize(value: number);
```
По умолчанию: `1`.

### dashOffset: boolean
Определяет смещение штриха в пунктирном отрезке.
```js
  get dashOffset(): number;
  set dashOffset(value: number);
```
По умолчанию: `0`.

### gapSize: boolean
Определяет длину пустого промежутка в пунктирном отрезке.
```js
  get gapSize(): number;
  set gapSize(value: number);
```
По умолчанию: `1`.

### resolution: THREE.Vector2
Задает и получает размеры области отрисовки. Нужно для корректной отрисовки линий в `worldUnits = false` режиме. Данное свойство обновляется автоматически перед отрисовкой.
```js
  get resolution(): THREE.Vector2;
  set resolution(value: THREE.Vector2);
```
Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).

## MeshLineMaterialParameters {#MeshLineMaterialParameters}
Параметры `MeshLineMaterial`. Задают соответствующие свойства [MeshLineMaterial](#MeshLineMaterial).
```js
export interface MeshLineMaterialParameters extends THREE.ShaderMaterialParameters {
  color?: THREE.ColorRepresentation | undefined;
  dashed?: boolean | undefined;
  dashScale?: number | undefined;
  dashSize?: number | undefined;
  dashOffset?: number | undefined;
  gapSize?: number | undefined;
  linewidth?: number | undefined;
  resolution?: THREE.Vector2 | undefined;
  worldUnits?: boolean | undefined;
}
```

# MeshLineGeometry {#MeshLineGeometry}
Геометрия, используемая для отрисовки линий в виде полигональной сетки. Линии задаются указанием точек.
```js
export class MeshLineGeometry extends THREE.InstancedBufferGeometry {

  constructor();

  setPoints(points: THREE.Vector3[]): this;

  setPositions(array: ArrayLike<number>): this;

  setColors(array: ArrayLike<number>): this;

  updatePoint(index: number, point: THREE.Vector3): void;

  updateColor(index: number, color: THREE.Color): void;
}
```

## Методы

### setPoints()
Метод задает точки линии. 
```js
  setPoints(points: THREE.Vector3[]): this;
```
где:
`points` -- точки линии. Подробнее: [THREE.Vector3](https://www.google.com/search?q=THREE.Vector3).

При вызове этого метода происходит перестроение атрибутов геометрии, что является ресурсозатратной операцией. Поэтому, для изменения координат точек, если количество точек не изменяется, следует использовать метод [updatePoint](#updatePoint).

### setPositions()
Метод задает точки линии из координат переданных в виде массива.
```js
  setPositions(array: ArrayLike<number>): this;
```
где:
`array` -- массив с координатами точек. Координаты расположены последовательно, по 3 элемента на точку: `[ x0, y0, z0, x1, y1, z1, ... ]`.

При вызове этого метода происходит перестроение атрибутов геометрии, что является ресурсозатратной операцией. Поэтому, для изменения координат точек, если количество точек не изменяется, следует использовать метод [updatePoint](#updatePoint).

### setColors()
Метод задает цвета отдельных участков линии. Цвета действуют в окрестностях точек к которым применяются, то есть все отрезки между точками будут поделены пополам и каждая половина будет окрашена в цвет ближайшей примыкающей точки. Если цвета не заданы, то для всей линии используется цвет материала: [MeshLineMaterial.color](#color).
```js
  setColors(array: ArrayLike<number>): this;
```
где:
`array` -- массив со значенями цветов точек. Значения расположены последовательно, по 3 элемента на точку: `[ r0, g0, b0, r1, g1, b1, ... ]`.

При вызове этого метода происходит перестроение атрибутов геометрии, что является ресурсозатратной операцией. Поэтому, для изменения цветов точек, если количество точек не изменяется, следует использовать метод [updateColor](#updateColor).

### updatePoint() {#updatePoint}
Метод обновляет координаты точки, без перестроения всей геометрии.
```js
  updatePoint(index: number, point: THREE.Vector3): void;
```
где:
`index` -- порядковый номер точки.\
`point` -- обновлённые координаты точки. Подробнее: [THREE.Vector3](https://www.google.com/search?q=THREE.Vector3).


### updateColor() {#updateColor}
Метод обновляет цвет точки, без перестроения всей геометрии.
```js
  updateColor(index: number, color: THREE.Color): void;
```
`index` -- порядковый номер точки.\
`color` -- обновлённый цвет точки. Подробнее: [THREE.Color](https://threejs.org/docs/#api/en/math/Color).