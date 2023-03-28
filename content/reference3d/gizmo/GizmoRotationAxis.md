---
title: "GizmoRotationAxis"
draft: false
weight: 9
---

## GizmoRotationAxis {#GizmoRotationAxis}
**GizmoRotationAxis** -- встроенная реализация оси вращения, для [GizmoControl](../GizmoControl). Подробнее: [GizmoAxis](../GizmoAxis).

```js
export class GizmoRotationAxis extends GizmoAxis {
  constructor(axisDir: THREE.Vector3, readonly handle: IGizmoObject, readonly picker?: IGizmoObject, readonly helper?: IGizmoObject) {
    super(axisDir, handle, picker, helper);
    this.name = 'GizmoRotationAxis';
  }

  public moveByNdcPt(ndcPos: THREE.Vector2, camera: THREE.Camera): THREE.Matrix4 {
    this.updateGizmoPlane(camera);

    if (!this._startPoint)
      this.setStartPt(ndcPos, camera);

    this._raycaster.setFromCamera(ndcPos, camera);
    const planeIntersect = this._raycaster.ray.intersectPlane(this._plane, new THREE.Vector3());
    if (!planeIntersect)
      return null;

    const localStartPt = this._startPoint.clone().sub(this._worldPositionStart);
    this._endPoint.copy(planeIntersect);
    const localEndPt = this._endPoint.clone().sub(this._worldPositionStart);

    let angle = localEndPt.angleTo(localStartPt);

    const crossSign = Math.sign(localStartPt.clone().cross(localEndPt).dot(this._worldAxisDir));
    angle *= crossSign;

    return new THREE.Matrix4().makeRotationAxis(this._axisDir, angle);
  }

  protected override updateGizmoPlane(camera: THREE.Camera): void {
    this._plane.setFromNormalAndCoplanarPoint(this._worldAxisDir, this._worldPositionStart);
  }
}
```