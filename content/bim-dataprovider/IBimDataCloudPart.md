---
title: IBimDataCloudPart
draft: false
weight: 4
---

**IBimDataCloudPart** -- интерфейс объекта-посредника для чтения файлов облаков точек.
Наследуется от [IBimDataPart](../IBimDataPart).

```js
export interface IBimDataCloudPart extends IBimDataPart  {
  getCloudPoints(index: number): Promise<Float32Array>;
  getCloudHierarchy(): Promise<BimCloudHierarchyItem[]>;
  getCloudParameters(): Promise<Map<string, string>>;
  getCloudMetadata(): Promise<BimCloudMetadata>;
}
```

## Методы

### getCloudPoints()
Метод возвращает данные о точках в узле октодерева облака точек.
```js
  getCloudPoints(index: number): Promise<Float32Array>;
```
где:\
`index` -- идентификатор данных узла октодерева.\
Возвращает массив данных вида: `[x0, y0, z0, c0, ... , xn, yn, zn, cn]`.
Массив последовательно описывает точки узла, на каждую точку приходится 4 элемента: `x, y, z, color`.
Цвет точки закодирован в BGRA32 формате.

### getCloudHierarchy()
Метод возвращает иерархию октодерева облака точек.
```js
  getCloudHierarchy(): Promise<BimCloudHierarchyItem[]>;
```
Подробнее: [BimCloudHierarchyItem](#BimCloudHierarchyItem).
{{< hint type="note" title="Примечание">}}
Иерархия дерева записана с помощью обхода в ширину. Данные об узлах дерева расположены в массиве уровень за уровнем.\
Например, для дерева с корневым узлом `r`, обозначим дочерние узлы добавлением цифры к имени: `r1`, `r2`, `r3`. Дочерними узлами для `r1` будут соответственно `r11`, `r12`, `r13`. Тогда данные об узлах дерева будут расположены в массиве следующим образом: 
`[r, r1, r2, r3, r11, r12, r13, r21, r22, r23, r31, ...]`
{{< /hint >}}

### getCloudParameters()
Метод возвращает параметры облака точек в виде словаря с данными в текстовом виде.
```js
  getCloudParameters(): Promise<Map<string, string>>;
```

### getCloudMetadata()
Метод возвращает параметры облака точек, в прочитанном и обработанном виде.
```js
  getCloudMetadata(): Promise<BimCloudMetadata>;
```
Подробнее: [BimCloudMetadata](#BimCloudMetadata).

# BimCloudHierarchyItem {#BimCloudHierarchyItem}
Класс описывает узел октодерева облака точек.
```js
export class BimCloudHierarchyItem {
  index: number;    // идентификатор узла октодерева
  dataIndex: number;    // идентификатор данных узла октодерева
  type: BimHierarchyItemType;   // тип узла октодерева
  mask: number;   // битовая маска, показывающая, какие из дочерних узлов существуют
  numPoints: number;    // количество точек в узле октодерева
  min: { x: number, y: number, z: number };   //  BoundingBox.min - габариты узла октодерева
  max: { x: number, y: number, z: number };   //  BoundingBox.max - габариты узла октодерева
}
```

# BimCloudHierarchyItem {#BimCloudHierarchyItem}
Перечисление типов узлов октодерева.
```js
export enum BimHierarchyItemType {
  NORMAL = 0,   // узел содержит как данные о точках, так и дочерние узлы
  LEAF = 1,   // лист октодерева, содержит только данные о точках, не имеет дочерних узлов
  PROXY = 2   // узел содержит только дочерние узлы
}
```

# BimCloudMetadata {#BimCloudMetadata}
```js
export class BimCloudMetadata {
  depth: number;
  min: { x: number, y: number, z: number };   // BoundingBox.min - габариты октодерева
  max: { x: number, y: number, z: number };   // BoundingBox.max - габариты октодерева
  
  baseSpacing: number;    // расстояние между точками на нулевом уровне дерева (корневой узел)
  // расстояние между точками уменьшается в 2 раза за каждый уровень: spacing = baseSpacing / (1 << node.level)

  version?: number;
  filename?: string;
  description?: string;
  inputPoints?: number;
  processedPoints?: number;
  nodesCount?: number;
  nodesPoints?: number;
  posOffset?: { x: number, y: number, z: number };
  posScale?: { x: number, y: number, z: number };
  root_min?: { x: number, y: number, z: number };
  root_max?: { x: number, y: number, z: number };
}
```