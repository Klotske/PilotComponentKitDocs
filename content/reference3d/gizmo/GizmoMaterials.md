---
title: "GizmoMaterials"
draft: false
weight: 9
---

## GizmoMaterials {#GizmoMaterials}
**GizmoMaterials** -- материалы, используемые для отрисовки [гизмо объектов](../IGizmoObject). Подробнее:\
[THREE.Material](https://threejs.org/docs/#api/en/materials/Material),\
[THREE.MeshBasicMaterial](https://threejs.org/docs/#api/en/materials/MeshBasicMaterial).

```js
export class GizmoMaterials {
  // базовый материал для мешей
  static gizmoMaterial: THREE.MeshBasicMaterial;

  // полностью прозрачный материал
  static matInvisible: THREE.MeshBasicMaterial;

  // красный непрозрачный материал
  static matRed: THREE.MeshBasicMaterial;

  // зелёный непрозрачный материал
  static matGreen: THREE.MeshBasicMaterial;

  // синий непрозрачный материал
  static matBlue: THREE.MeshBasicMaterial;

  // желтый непрозрачный материал
  static matYellow: THREE.MeshBasicMaterial;

  // фиолетовый непрозрачный материал
  static matViolet: THREE.MeshBasicMaterial;
  
  // желтый полупрозрачный материал
  static matYellowTransparent: THREE.MeshBasicMaterial;
}
```