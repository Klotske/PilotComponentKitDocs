---
title: "INavigationTool"
draft: false
weight: 9
---

**INavigationTool** -- интерфейс, позволяющий взаимодействовать с навигацией на сцене.\
Для того, чтобы создать свой обработчик для навигации по сцене, необходимо реализовать интерфейс `PilotWeb3D.INavigationTool`, либо унаследоваться от класса `PilotWeb3D.NavigationTool`.

{{< hint type="note" icon=gdoc_info_outline title="Примечание">}}
Например, `MobileNavigation`, навигация для мобильных устройств:\
Здесь `PilotWeb3D.MobileNavigation` наследуется от `PilotWeb3D.NavigationTool`, который является реализацией интерфейса `PilotWeb3D.INavigationTool`.
{{< /hint >}}


## INavigationTool
Обработчик навигации, базовый интерфейс.

```js
export interface INavigationTool {
  get name(): string;
  init(navAgent: NavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
  setActive(isActive: boolean): void;
  getPivotPoint(): THREE.Vector3;
  setPivotPoint(pivotPoint: THREE.Vector3): void;
  setCameraParameters(iParams: { position: THREE.Vector3, eyeDir: THREE.Vector3, angle: number, viewCenter: THREE.Vector3 }): void;
  getCameraParameters(): { position: THREE.Vector3, eyeDir: THREE.Vector3, angle: number, viewCenter: THREE.Vector3 };
  getCamera(): THREE.Camera;
}
```

## NavigationTool
Обработчик навигации, базовый класс.

```js
export abstract class NavigationTool implements INavigationTool {
  protected _isActive: boolean;
  protected _cameraControl: ICameraControl;
  protected _intersectionChecker: IModelIntersectionChecker;
  protected _viewCenter: THREE.Vector3;
  protected _pivotPoint: THREE.Vector3;
  protected _navAgent: NavigationAgent;

  public abstract get name(): string;
  public init(navAgent: NavigationAgent, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
  public setActive(isActive: boolean): void;
  public getPivotPoint(): THREE.Vector3;
  public setPivotPoint(pivotPoint: THREE.Vector3): void;
  public setCameraParameters(iParams: { position: THREE.Vector3, eyeDir: THREE.Vector3, angle: number, viewCenter: THREE.Vector3 }): void;
  public getCameraParameters(): { position: THREE.Vector3, eyeDir: THREE.Vector3, angle: number, viewCenter: THREE.Vector3 };
  public getCamera(): THREE.Camera;

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

## DesktopNavigation
Обработчик навигации для десктопной версии приложения.
```js
export class DesktopNavigation extends NavigationTool {
  protected _prevMousePos?: THREE.Vector2;
  protected _mouseLftIsDown = false;
  protected _mouseLftIsDownPos?: THREE.Vector2;
  protected _mouseRhtIsDown = false;
  protected _mouseMidIsDown = false;

  protected onMouseEnter(ev: MouseEvent & NavigationEvent): void;
  protected onMouseLeave(ev: MouseEvent & NavigationEvent): void;
  protected onMouseMove(ev: MouseEvent & NavigationEvent): void;
  protected onMouseClick(ev: MouseEvent & NavigationEvent): void;
  protected onMouseDoubleClick(ev: MouseEvent & NavigationEvent): void;
  protected onMouseScroll(ev: WheelEvent & NavigationEvent): void;
  protected onMouseUp(ev: MouseEvent & NavigationEvent): void ;
  protected onKeyDown(ev: KeyboardEvent & NavigationEvent): void;
  protected onKeyUp(ev: KeyboardEvent & NavigationEvent): void;
  protected isAllMouseButtonsUp(): boolean;

  /** @deprecated */
  protected setImpulseDirection(dir: Direction, add: boolean): void;
  /** @deprecated */
  protected setIncreasedImpulse(isIncreased: boolean): void;
}
```
## MobileNavigation
Обработчик навигации для мобильной версии приложения.

```js
export class MobileNavigation extends NavigationTool {
  protected _initialTap?: THREE.Vector2;
  protected _prevTap?: THREE.Vector2;
  protected _prevPinch?: [THREE.Vector2, THREE.Vector2];

  protected _boundOnTouchStart = this.onTouchStart.bind(this);
  protected _boundOnTouchEnd = this.onTouchEnd.bind(this);
  protected _boundOnTouchMove = this.onTouchMove.bind(this);

  protected onTouchStart(evt: TouchEvent & NavigationEvent): void;
  protected onTouchEnd(evt: TouchEvent & NavigationEvent): void;
  protected onTouchMove(evt: TouchEvent & NavigationEvent): void;
  protected onSwipe(currentPos: THREE.Vector2): void;
  protected onPinch(iTouchPair: [THREE.Vector2, THREE.Vector2]): void;
  protected getPinchCenter(iTouchPair: [THREE.Vector2, THREE.Vector2]): THREE.Vector2;
  protected getTouchPoint(touch: Touch): THREE.Vector2;
  protected getTouchPair(curTouches: TouchList): [THREE.Vector2, THREE.Vector2];
}
```