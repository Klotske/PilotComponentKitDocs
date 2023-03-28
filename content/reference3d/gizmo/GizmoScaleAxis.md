---
title: "GizmoScaleAxis"
draft: false
weight: 9
---

## GizmoScaleAxis {#GizmoScaleAxis}
**GizmoScaleAxis** -- встроенная реализация оси масштабирования, для [GizmoControl](../GizmoControl).  Подробнее: [GizmoAxis](../GizmoAxis).

```js
export class GizmoScaleAxis extends GizmoAxis {
  constructor(axisDir: THREE.Vector3, readonly handle: IGizmoObject, readonly picker?: IGizmoObject, readonly helper?: IGizmoObject) {
    super(axisDir, handle, picker, helper);
    this.name = 'GizmoScaleAxis';
  }

  public moveByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Matrix4 {
    this.updateGizmoPlane(camera);

    if (!this._startPoint)
      this.setStartPt(ndcPos, camera);

    this._raycaster.setFromCamera(ndcPos, camera);

    const planeIntersect = this._raycaster.ray.intersectPlane(this._plane, new THREE.Vector3());
    if (!planeIntersect)
      return null;

    this._endPoint.copy(planeIntersect);

    const localStart = this._startPoint.clone().sub(this._worldPositionStart).dot(this._worldAxisDir);
    const localEnd = this._endPoint.clone().sub(this._worldPositionStart).dot(this._worldAxisDir);

    const scaleValue = localEnd / localStart;

    return new THREE.Matrix4().makeScale(
      this._axisDir.x !== 0 ? scaleValue : 1,
      this._axisDir.y !== 0 ? scaleValue : 1,
      this._axisDir.z !== 0 ? scaleValue : 1
    );

  }

  protected override updateGizmoPlane(camera: THREE.Camera): void {
    this._raycaster.setFromCamera({ x: 0, y: 0 }, camera);
    const eye = this._raycaster.ray.direction;

    const alignVector = eye.clone().cross(this._worldAxisDir);

    let dirVector = this._worldAxisDir.clone().cross(alignVector);

    if (dirVector.length() === 0) {
      dirVector = eye;
    }

    this._plane.setFromNormalAndCoplanarPoint(dirVector, this._worldPositionStart);
  }
}
```