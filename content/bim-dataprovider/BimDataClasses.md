---
title: BimDataClasses
draft: false
weight: 5
---

## BimDataTessellation {#BimDataTessellation}
Класс описывает тесселяцию элемента модели.
```js
export class BimDataTessellation {
  key: string;    // уникальный идентификатор тесселяции
  vertices: Float32Array;   // координаты вершин [x0, y0, z0, ... , xn, yn, zn]
  normals: Float32Array;    // координаты нормалей [x0, y0, z0, ... , xn, yn, zn]
  indices: Uint32Array;   // индексы вершин в треугольниках граней меша
  edgeIndices: Uint32Array;   // индексы вершин рёбер меша
}
```


## BimDataElement {#BimDataElement}
Класс описывает элемент модели.
```js
export class BimDataElement {
  guid: string;   // уникальный идентификатор элемента
  objectState: BimDataNodeState;    // состояние элемента модели
  revision: bigint;     // версия элемента модели
  parentGuid: string;     // идентификатор родительского элемента
  name: string;   // имя элемента
  type: string;   // тип элемента
  representationType!: string;  // IFC тип геометрического представления, считывается из IFC файла при обработке
  representationStatus!: string;  // статус обработки геометрического представления: SUCCESS — геометрия объекта успешно построена, 
  // NO_REPRESENTATION — объект не имеет геометрического представления, 
  // SOLID-CREATION_ERROR — не удалось построить тело для данного объекта

  gridObject?: BimDataGridObject;   // сетка осей элемента модели

  meshesProperties: Map<string, BimDataMeshProperty[]>;   // параметры геометрического представления элемента на сцене,
  // ключами словаря являются уникальные идентификаторы тесселяций
  // значениями словаря являются параметры объектов, построенных по данной тесселяции
}
```
{{< hint type="important" title="Важно">}}
Свойство `objectState` принимает значения, отличные от `BimDataNodeState.Added`, только при получении списка элементов посредством метода [IBimDataModelPart::getDiffElements](../IBimDataModelPart/#getDiffElements).
{{< /hint >}}
{{< hint type="note" title="Примечание">}}
Свойство `parentGuid` корневого элемента равно `00000000-0000-0000-0000-000000000000`.
{{< /hint >}}

## BimDataNodeState {#BimDataNodeState}
Перечисление состояний элемента модели.
```js
export enum BimDataNodeState 
{
  Undefined = 0,    // состояние не определено
  Added = 1,    // элемент добавлен
  Removed = 2,    // элемент удалён
  AttributesModified = 3,   // атрибуты элемента изменены
  AttributesQuantitiesModified = 4,   // изменены атрибуты типа IfcElementQuantity
  PlacementModified = 8,    // изменилось геометрическое представление объекта на сцене
  PlacementAndAttributesModified = AttributesModified | PlacementModified,
  PlacementAndAttributesQuantitiesModified = AttributesQuantitiesModified | PlacementModified
}
```

## BimDataGridObject {#BimDataGridObject}
Класс описывает сетку осей элемента модели.
```js
export class BimDataGridObject {
  gridPlacement: Float64Array;    // матрица трансформации в глобальном пространстве, 4х4 - row-major order.
  gridAxes: BimDataGridAxis[];    // список осей - IfcGridAxis
}
```

## BimDataGridAxis {#BimDataGridAxis}
Класс описывает элемент сетки осей.
```js
export class BimDataGridAxis {
  id: number;     // идентификатор оси
  type: number;   // тип оси: Line = 0, Circle = 1, Arc = 2 
  data: Float32Array; // параметры оси
  label: string;  // текстовая метка оси
}
```

## BimDataMeshProperty {#BimDataMeshProperty}
Класс описывает параметры геометрического представления объекта на сцене.
```js
export class BimDataMeshProperty {
  meshColor: number;    // цвет геометрического представления объекта, закодирован в RGBA32 формате
  meshPlacement: Float64Array;    // матрица трансформации в глобальном пространстве, 4х4 - row-major order.
}
```

## BimDataElementPropertySet {#BimDataElementPropertySet}
Класс описывает набор свойств элемента модели.
```js
export class BimDataElementPropertySet {
  name: string;   // наименование набора
  properties: BimDataElementProperty[];   // список свойств в наборе
  type: BimDataIfcType;   // IFC тип элемента, берётся из IFC файла при обработке
}
```

## BimDataElementProperty {#BimDataElementProperty}
Класс описывает свойство элемента.
```js
export class BimDataElementProperty {
  name: string;  // имя свойства
  unit: number; // единицы измерения
  value: BimDataElementPropertyValue;  // значение свойства
}
```

## BimDataElementPropertyValue {#BimDataElementPropertyValue}
Класс описывает значение свойства.
```js
export class BimDataElementPropertyValue {
  str_value?: string;   // строковое значение
  int_value?: number;   // целочисленное значение
  double_value?: number;    // число с плавающей запятой
  date_value?: bigint;    // значение даты-времени в тактах (.NET / System / DateTime.Ticks)
  array_value: Array<string>;   // строковый список (пустой список, если не определён)
  decimal_value?: number;   // десятичное число
  guid_value?: string; // guid
  array_int_value: Array<number>;   // целочисленный список (пустой список, если не определён)
  bool_value?: boolean;   // логическое значение

  get value(): unknown;   // возвращает значение свойства
}
```
{{< hint type="important" icon=gdoc_error_outline title="Важно" >}}
Заполнено будет только одно поле, соответствующее типу значения этого свойства.
Например: если значение равно `0.0`, то будет заполнено поле `double_value`.
{{< /hint >}}
