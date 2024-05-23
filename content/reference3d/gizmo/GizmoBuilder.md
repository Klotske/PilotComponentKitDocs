---
title: "GizmoBuilder"
draft: false
weight: 9
---

## GizmoBuilder {#GizmoBuilder}
**GizmoBuilder** -- вспомогательный класс, конструирующий [GizmoControl](../GizmoControl) с реализацией по умолчанию. 

```js
export class GizmoBuilder {
  public static build(camera: THREE.Camera, navAgent: INavigationAgent, translation: GizmoAxisDir = GizmoAxisDir.XYZ, rotation: GizmoAxisDir = GizmoAxisDir.XYZ, scale: GizmoAxisDir = GizmoAxisDir.XYZ): GizmoControl;

  public static buildTranslationAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, handleHoveredMaterial?: THREE.Material, handleSelectedMaterial?: THREE.Material,
    pickerBaseMatrial?: THREE.Material, pickerHoveredMaterial?: THREE.Material, pickerSelectedMaterial?: THREE.Material
  ): GizmoAxis;

  public static buildRotationAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, handleHoveredMaterial?: THREE.Material, handleSelectedMaterial?: THREE.Material,
    pickerBaseMatrial?: THREE.Material, pickerHoveredMaterial?: THREE.Material, pickerSelectedMaterial?: THREE.Material
  ): GizmoAxis;

  public static buildScaleAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, handleHoveredMaterial?: THREE.Material, handleSelectedMaterial?: THREE.Material,
  ): GizmoAxis;
```
## Методы

## build()
Строит [GizmoControl](../GizmoControl) с реализацией по умолчанию.
```js
public static build(camera: THREE.Camera, navAgent: INavigationAgent, 
  translation: GizmoAxisDir, 
  rotation: GizmoAxisDir, 
  scale: GizmoAxisDir): GizmoControl;
```
где:\
`camera` -- камера, используемая для отрисовки `GizmoControl` на сцене. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).

`navAgent` -- агент навигации. Подробнее: [INavigationAgent](../../navigation/INavigationAgent).\.

`translation` -- перечисление осей переноса, которые необходимо добавить в контроллер. Необязательный параметр. По умолчанию [GizmoAxisDir](#GizmoAxisDir).**XYZ**.

`rotation` -- перечисление осей вращения, которые необходимо добавить в контроллер. Необязательный параметр. По умолчанию [GizmoAxisDir](#GizmoAxisDir).**XYZ**.

`scale` -- перечисление осей масштабирования, которые необходимо добавить в контроллер. Необязательный параметр. По умолчанию [GizmoAxisDir](#GizmoAxisDir).**XYZ**.

Возвращает объект [GizmoControl](../GizmoControl).


## buildTranslationAxis()
Строит ось переноса с реализацией по умолчанию. Подробнее [GizmoTranslationAxis](../GizmoTranslationAxis)
```js
  public static buildTranslationAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, 
    handleHoveredMaterial?: THREE.Material, 
    handleSelectedMaterial?: THREE.Material,
    pickerBaseMatrial?: THREE.Material, 
    pickerHoveredMaterial?: THREE.Material, 
    pickerSelectedMaterial?: THREE.Material
  ): GizmoAxis
```
где:\
`axisDir` -- направление оси переноса в локальных координатах. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

`navAgent` -- агент навигации. Подробнее: [INavigationAgent](../../navigation/INavigationAgent).

`handleBaseMatrial` -- базовый материал [handle](../GizmoAxis#handle) - геометрии. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**gizmoMaterial**.

`handleHoveredMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активном ховере. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.

`handleSelectedMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активной манипуляции над осью. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.

`pickerBaseMatrial` -- базовый материал [picker](../GizmoAxis#picker) - геометрии. По умолчанию: [GizmoMaterials](../GizmoMaterials)**.matInvisible**.

`pickerHoveredMaterial` -- материал [picker](../GizmoAxis#picker) - геометрии, при активном ховере. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials)**.matInvisible**.

`pickerSelectedMaterial` -- материал [picker](../GizmoAxis#picker) - геометрии, при активной манипуляции над осью.[GizmoMaterials](../GizmoMaterials)**.matInvisible**.

Возвращает объект [GizmoAxis](../GizmoAxis).

## buildRotationAxis()
Строит ось вращения с реализацией по умолчанию. Подробнее [GizmoRotationAxis](../GizmoRotationAxis)
```js
  public static buildRotationAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, 
    handleHoveredMaterial?: THREE.Material, 
    handleSelectedMaterial?: THREE.Material,
    pickerBaseMatrial?: THREE.Material, 
    pickerHoveredMaterial?: THREE.Material, 
    pickerSelectedMaterial?: THREE.Material
  ): GizmoAxis
```
где:\
`axisDir` -- направление оси вращения в локальных координатах. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

`navAgent` -- агент навигации. Подробнее: [INavigationAgent](../../navigation/INavigationAgent).

`handleBaseMatrial` -- базовый материал [handle](../GizmoAxis#handle) - геометрии. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**gizmoMaterial**.

`handleHoveredMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активном ховере. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.

`handleSelectedMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активной манипуляции над осью. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matViolet**.

`pickerBaseMatrial` -- базовый материал [picker](../GizmoAxis#picker) - геометрии. По умолчанию: [GizmoMaterials](../GizmoMaterials)**.matInvisible**.

`pickerHoveredMaterial` -- материал [picker](../GizmoAxis#picker) - геометрии, при активном ховере. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials)**.matYellowTransparent**.

`pickerSelectedMaterial` -- материал [picker](../GizmoAxis#picker) - геометрии, при активной манипуляции над осью.[GizmoMaterials](../GizmoMaterials)**.matYellowTransparent**.

Возвращает объект [GizmoAxis](../GizmoAxis).


## buildScaleAxis()
Строит ось масштабирования с реализацией по умолчанию. Подробнее [GizmoScaleAxis](../GizmoScaleAxis)
```js
  public static buildScaleAxis(axisDir: THREE.Vector3,
    handleBaseMatrial?: THREE.Material, 
    handleHoveredMaterial?: THREE.Material, 
    handleSelectedMaterial?: THREE.Material
  ): GizmoAxis
```
где:\
`axisDir` -- направление оси вращения в локальных координатах. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

`navAgent` -- агент навигации. Подробнее: [INavigationAgent](../../navigation/INavigationAgent).

`handleBaseMatrial` -- базовый материал [handle](../GizmoAxis#handle) - геометрии. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**gizmoMaterial**.

`handleHoveredMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активном ховере. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.

`handleSelectedMaterial` -- материал [handle](../GizmoAxis#handle) - геометрии, при активной манипуляции над осью. Необязательный параметр. По умолчанию: [GizmoMaterials](../GizmoMaterials).**matYellow**.

Возвращает объект [GizmoAxis](../GizmoAxis).

## GizmoAxisDir {#GizmoAxisDir}
Направление осей [GizmoControl](../GizmoControl), используемые в [GizmoBuilder](#GizmoBuilder).
```js
export enum GizmoAxisDir {
  // Не строить данный тип осей
  NONE = 0,
  // Строить ось X
  X = 1 << 0,
  // Строить ось Y
  Y = 1 << 1,
  // Строить ось Z
  Z = 1 << 2,
  // Строить ось X и ось Y
  XY = X | Y,
  // Строить ось Y и ось Z
  YZ = Y | Z,
  // Строить ось X и ось Y
  XZ = X | Z,
  // Строить оси X, Y и Z
  XYZ = X | Y | Z
}
```