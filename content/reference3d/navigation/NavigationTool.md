---
title: "NavigationTool"
draft: false
weight: 9
---

## NavigationTool

**NavigationTool** - Обработчик навигации, базовый класс.

```js
export abstract class NavigationTool implements INavigationTool {
  protected _isActive: boolean;
  protected _cameraControl: ICameraControl;
  protected _intersectionChecker: IModelIntersectionChecker;
  protected _viewCenter: THREE.Vector3;
  protected _pivotPoint: THREE.Vector3;
  protected _navAgent: INavigationAgent;

  public abstract get name(): string;
  public init(navAgent: INavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
  public setActive(isActive: boolean): void;
  public getPivotPoint(): THREE.Vector3;
  public setPivotPoint(pivotPoint: THREE.Vector3): void;
  public setCameraParameters(iParams: CameraParameters): void;
  public getCameraParameters(): CameraParameters;

  protected abstract addEvents(): void;
  protected abstract removeEvents(): void;
  protected handleHovered(object: THREE.Object3D): void;
  protected handleClick(object: THREE.Object3D, ctrlKey: boolean): void;
  protected handleDblClick(object: THREE.Object3D): void;
  protected getViewCenter(): THREE.Vector3;
  protected setViewCenter(viewCenter: THREE.Vector3): void;
  protected rotate(movement: THREE.Vector2): void;
  protected translate(prevPos: THREE.Vector2, currPos: THREE.Vector2): void;
  protected spin(movement: THREE.Vector2): void;
  protected zoom(deltaSign: number): void;
  protected resetSelection();
  protected onEventHandled(event: Event & NavigationEvent): void;
}
```
