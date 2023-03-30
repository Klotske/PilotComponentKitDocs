---
title: "GizmoTranslationAxis"
draft: false
weight: 9
---

## GizmoTranslationAxis {#GizmoTranslationAxis}
**GizmoTranslationAxis** -- встроенная реализация оси переноса для [GizmoControl](../GizmoControl). Подробнее: [GizmoAxis](../GizmoAxis).

```js
export class GizmoTranslationAxis extends GizmoAxis {
  constructor(axisDir: THREE.Vector3, readonly handle: IGizmoObject, readonly picker?: IGizmoObject, readonly helper?: IGizmoObject) {
    super(axisDir, handle, picker, helper);
    this.name = 'GizmoTranslationAxis';
  }

  moveByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Matrix4 {
    this.updateGizmoPlane(camera);

    if (!this._startPoint)
      this.setStartPt(ndcPos, camera);

    this._raycaster.setFromCamera(ndcPos, camera);

    const planeIntersect = this._raycaster.ray.intersectPlane(this._plane, new THREE.Vector3());
    if (!planeIntersect)
      return null;

    this._endPoint.copy(planeIntersect);

    const offset = this._endPoint.clone().sub(this._startPoint);

    const offsetValue = offset.dot(this._worldAxisDir);
    offset.copy(this._worldAxisDir).multiplyScalar(offsetValue);

    return new THREE.Matrix4().makeTranslation(offset.x, offset.y, offset.z);
  }

  protected override updateGizmoPlane(camera: THREE.Camera): void {
    this._raycaster.setFromCamera({ x: 0, y: 0 }, camera);
    const eye = this._raycaster.ray.direction;

    const alignVector = eye.clone().cross(this._worldAxisDir);

    let dirVector = this._worldAxisDir.clone().cross(alignVector);

    if (dirVector.length() === 0) {
      dirVector = eye;
    }

    dirVector.normalize();

    this._plane.setFromNormalAndCoplanarPoint(dirVector, this._worldPositionStart);
  }
}
```