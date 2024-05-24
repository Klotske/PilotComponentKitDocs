---
title: "IGizmoObject"
draft: false
weight: 9
---

## IGizmoObject {#IGizmoObject}
**IGizmoObject** -- интерфейс, описывающий поведение объектов гизмо. 

```js
export interface IGizmoObject extends THREE.Object3D {
  //Метод возвращает статус ховера над IGizmoObject.
  getHovered(): boolean;
  //Метод задает ховер для IGizmoObject.
  setHovered(value: boolean): void;
  //Метод возвращает статус активности манипуляций над IGizmoObject.
  getActive(): boolean;
  //Метод задает статус активности манипуляций над IGizmoObject.
  setActive(value: boolean): void;
  //Метод освобождает выделенные объектом ресурсы.
  dispose(): void;
}
```

## GizmoObject {#GizmoObject}
**GizmoObject** -- реализация интерфейса [IGizmoObject](#IGizmoObject). При изменении ховера, либо активности объекта, меняет материал геометрий.

```js
export class GizmoObject extends THREE.Object3D implements IGizmoObject {
  constructor(protected _meshes: THREE.Mesh[], 
    readonly baseMaterial: THREE.Material,
    readonly hoverMaterial: THREE.Material,
    readonly activeMaterial: THREE.Material
  );
  getHovered(): boolean;
  setHovered(value: boolean): void;
  getActive(): boolean;
  setActive(value: boolean): void;
  dispose(): void;

  override raycast(raycaster: THREE.Raycaster, intersects: THREE.Intersection<THREE.Object3D<THREE.Event>>[]): void;
}
```
## Поля

### _meshes: THREE.Mesh[] {#meshes}
Геометрии, используемые для рендера на сцене. Также используются при [расчете пересечений](#raycast) с `GizmoObject`.

### baseMaterial: THREE.Material {#baseMaterial}
Материал геометрий, применяемый в отсутствии ховера и при неактивном `GizmoObject`. По умолчанию: [GizmoMaterials](../GizmoMaterials).**gizmoMaterial**.
```js
baseMaterial: THREE.Material;
```

### hoverMaterial: THREE.Material {#hoverMaterial}
Материал геометрий, применяемый при ховере над `GizmoObject`. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellowTransparent**.
```js
hoverMaterial: THREE.Material;
```

### activeMaterial: THREE.Material {#activeMaterial}
Материал геометрий, применяемый при активной манипуляции над `GizmoObject`. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.
```js
activeMaterial: THREE.Material;
```

## Конструктор
```js
  constructor(protected _meshes: THREE.Mesh[], 
    readonly baseMaterial: THREE.Material,
    readonly hoverMaterial: THREE.Material,
    readonly activeMaterial: THREE.Material
  );
```
где:\
`_meshes` -- геометрии объекта для отрисовки на сцене.

`baseMaterial` -- материал геометрий, применяемый в отсутствии ховера и при неактивном `GizmoObject`. Необязательный параметр. Подробнее: [THREE.Material](https://threejs.org/docs/#api/en/materials/Material).

`hoverMaterial` -- материал геометрий, применяемый при ховере над `GizmoObject`. Необязательный параметр. Подробнее: [THREE.Material](https://threejs.org/docs/#api/en/materials/Material).

`activeMaterial` -- материал геометрий, применяемый при активной манипуляции над `GizmoObject`. Необязательный параметр. Подробнее: [THREE.Material](https://threejs.org/docs/#api/en/materials/Material).

## Методы

### getHovered()
Метод возвращает статус ховера для `GizmoObject`.
```js
  getHovered(): boolean;
```
Возвращает `true`, если над объектом находится курсор.

### setHovered()
Метод устанавливает значение ховера для `GizmoObject`. 
```js
  setHovered(value: boolean): void;
```
где:\
`value` - значение ховера.\
Если `value` равно `true`, то материал геометрий изменится на `hoverMaterial`, если `GizmoObject` не активен. В противном случае, материалом геометрий будет или `baseMaterial`, или `activeMaterial`, в зависимости от активности `GizmoObject`.

### getActive()
Метод возвращает статус активности для `GizmoObject`.
```js
  getActive(): boolean;
```
Возвращает `true`, если объект активен.

### setActive()
Метод устанавливает статус активности для `GizmoObject`.
```js
  setActive(value: boolean): void;
```
где:\
`value` - значение активности.\
Если `value` равно `true`, то материал геометрий изменится на `activeMaterial`. В противном случае, материалом геометрий будет или `baseMaterial`, или `hoverMaterial`, в зависимости от значения ховера для `GizmoObject`. Активность `GizmoObject` имеет больший приоритет в установке материала геометрий, чем ховер.

### raycast {#raycast}
Переопределённый метод [Object3D.raycast](https://threejs.org/docs/#api/en/core/Object3D.raycast). Проверяет пересечения для всех [геометрий](#meshes) `GizmoObject`.
```js
override raycast(raycaster: THREE.Raycaster, intersects: THREE.Intersection<THREE.Object3D<THREE.Event>>[]): void
```