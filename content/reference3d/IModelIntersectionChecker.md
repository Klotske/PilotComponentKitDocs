---
title: "IModelIntersectionChecker"
draft: false
weight: 9
---

**IModelIntersectionChecker** -- интерфейс обработки пересечений объектов на сцене.

```js
export interface IModelIntersectionChecker {
  get modelCenter(): THREE.Vector3;
  get boundingBox(): THREE.Box3;

  getIntersectionPoint(): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionByRay(ray: THREE.Ray): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByRay(ray: THREE.Ray): { modelId: string, guid: string } | undefined;
  getIntersectionByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Intersection<THREE.Object3D> | undefined;
  getIntersectionIDByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): { modelId: string, guid: string } | undefined;
  getIntersectionIDByFrustumNdcPt(ndcFrustumBox: THREE.Box3, unProjMatrix: THREE.Matrix4, isContainsOnly: boolean): { modelId: string; guid: string; }[] | undefined;
}
```
