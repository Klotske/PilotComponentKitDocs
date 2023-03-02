---
title: "NavigationEventHandler"
draft: false
weight: 9
---

**NavigationEventHandler** -- базовый класс работы с навигацией.
Для того, чтобы создать свой обработчик для навигации по сцене необходимо унаследоваться от класса `PilotWeb3D.NavigationEventHandler`.

Например навигация для расширения BoxSelection:
Здесь `BoxSelectionNavigationHandler` класс наследуется от `PilotWeb3D.DesktopNavigationEventHandler` который является наследником базового класса `PilotWeb3D.NavigationEventHandler`.
```js

export class BoxSelectionNavigationHandler extends PilotWeb3D.DesktopNavigationEventHandler {
  private _selectionStartPoint: THREE.Vector2 = new THREE.Vector2();
  private _selectionEndPoint: THREE.Vector2 = new THREE.Vector2();
  private _selectionKeyEnable = false;
  private _boxSelectionEnable = false;
  private _selectionRectangle: HTMLDivElement;
  private _styleContains = 'box-selection-contains';
  private _styleIntersects = 'box-selection-intersects';

  override get name(): string {
    return "BoxSelectionNavigationHandler";
  }

  constructor(private _model: PilotWeb3D.Model) {
    super();
    this._selectionRectangle = document.createElement('div');
    this._selectionRectangle.classList.add(this._styleContains);
    this._selectionRectangle.style.pointerEvents = 'none';
  }

  protected override onMouseMove(ev: MouseEvent): void {
    if (this._boxSelectionEnable) {
      const currentPos = new THREE.Vector2(ev.clientX, ev.clientY);
      this.onSelectionMove(currentPos);
      this._prevMousePos.copy(currentPos);
    } else {
      super.onMouseMove(ev);
    }
  }

  protected override onMouseClick(ev: MouseEvent): void {
    if (this._selectionKeyEnable) {// left button
      return;
    }
    else {
      super.onMouseClick(ev);
    }
  }

  protected override onMouseDown(ev: MouseEvent): void {
    super.onMouseDown(ev);
    if (ev.button == MouseButtons.Left)
      this.switchSelectionMode();
  }

  protected override onMouseUp(ev: MouseEvent): void {
    super.onMouseUp(ev);
    if (ev.button == MouseButtons.Left)
      this.switchSelectionMode();
  }

  protected override onKeyDown(ev: KeyboardEvent): void {
    super.onKeyDown(ev);
    if (ev.key === "Shift") {
      if (ev.repeat)
        return;
      this._selectionKeyEnable = true;
      this.switchSelectionMode();
    }
  }

  protected override onKeyUp(ev: KeyboardEvent): void {
    super.onKeyUp(ev);
    if (ev.key === "Shift") {
      if (ev.repeat)
        return;
      this._selectionKeyEnable = false;
      this.switchSelectionMode();
    }
  }

  private switchSelectionMode(): void {
    if (this._selectionKeyEnable && this._mouseLftIsDown && !this._boxSelectionEnable) {
      this.onSelectionStart(this._prevMousePos);
    }
    else if (this._boxSelectionEnable) {
      this.onSelectionEnd(this._prevMousePos);
    }
  }

  private onSelectionStart(mousePos: THREE.Vector2): void {
    this._boxSelectionEnable = true;
    this._selectionStartPoint = mousePos.clone();
    this._canvas.parentElement.appendChild(this._selectionRectangle);
  }

  private onSelectionEnd(mousePos: THREE.Vector2): void {
    this._boxSelectionEnable = false;
    this._selectionEndPoint = mousePos.clone();
    this._selectionRectangle.style.left = mousePos.x + 'px';
    this._selectionRectangle.style.top = mousePos.y + 'px';
    this._selectionRectangle.style.width = 1 + "px";
    this._selectionRectangle.style.height = 1 + "px";
    this._canvas.parentElement.removeChild(this._selectionRectangle);
    this.handleBoxSelection();
  }

  private onSelectionMove(mousePos: THREE.Vector2): void {
    const left = Math.min(this._selectionStartPoint.x, mousePos.x);
    const right = Math.max(this._selectionStartPoint.x, mousePos.x);
    const top = Math.min(this._selectionStartPoint.y, mousePos.y);
    const bottom = Math.max(this._selectionStartPoint.y, mousePos.y);

    this._selectionRectangle.style.left = left + 'px';
    this._selectionRectangle.style.top = top + 'px';
    this._selectionRectangle.style.width = (right - left) + "px";
    this._selectionRectangle.style.height = (bottom - top) + "px";

    if (mousePos.x >= this._selectionStartPoint.x) {
      this._selectionRectangle.classList.replace(this._styleIntersects, this._styleContains);
    } else {
      this._selectionRectangle.classList.replace(this._styleContains, this._styleIntersects);
    }
  }

  private handleBoxSelection(): void {
    if (this._selectionStartPoint.x === this._selectionEndPoint.x) {
      this._selectionEndPoint.x += 1;
    }

    if (this._selectionStartPoint.y === this._selectionEndPoint.y) {
      this._selectionEndPoint.y += 1;
    }

    const isContainsOnly = this._selectionEndPoint.x > this._selectionStartPoint.x;

    const unProjMatrix = new THREE.Matrix4();
    const ndcFrustumBox = this.calcNdcFrustumBox(unProjMatrix);
    const intersectionIDs = this._intersectionChecker.getIntersectionIDByFrustumNdcPt(ndcFrustumBox, unProjMatrix, isContainsOnly);

    const selectionIDs: Map<string, string[]> = new Map<string, string[]>();
    for (const { modelId, guid } of intersectionIDs) {
      selectionIDs.has(modelId) ? selectionIDs.get(modelId).push(guid) : selectionIDs.set(modelId, [guid]);
    }

    this._model.clearSelection();
    for (const [modelId, guids] of selectionIDs) {
      this._model.select(guids, modelId, PilotWeb3D.SelectionMode.Append);
    }
  }

  private calcNdcFrustumBox(unprojectMatrix: THREE.Matrix4): THREE.Box3 {
    const camera = this._cameraControl.getCamera();
    camera.updateMatrix();
    camera.updateMatrixWorld(true);

    unprojectMatrix.multiplyMatrices(camera.matrixWorld, camera.projectionMatrixInverse);
    const ndcFrustumBox = new THREE.Box3();
    //Get screen coordinates
    const left = Math.min(this._selectionStartPoint.x, this._selectionEndPoint.x);
    const top = Math.min(this._selectionStartPoint.y, this._selectionEndPoint.y);
    const right = Math.max(this._selectionStartPoint.x, this._selectionEndPoint.x);
    const bottom = Math.max(this._selectionStartPoint.y, this._selectionEndPoint.y);

    //Get ndc coordinates
    const topRight = getNdcPos(new THREE.Vector2(right, top), this._canvas);
    const bottomLeft = getNdcPos(new THREE.Vector2(left, bottom), this._canvas);

    ndcFrustumBox.min = new THREE.Vector3(bottomLeft.x, bottomLeft.y, -1);
    ndcFrustumBox.max = new THREE.Vector3(topRight.x, topRight.y, 1);

    return ndcFrustumBox;
  }
```


## NavigationEventHandler
Обработчик навигации, базовый класс.

```js
export abstract class NavigationEventHandler {
    protected _isActive: boolean;
    protected _canvas: HTMLCanvasElement;
    protected _cameraControl: ICameraControl;
    protected _intersectionChecker: IModelIntersectionChecker;
    protected _viewCenter: THREE.Vector3;
    protected _pivotPoint: THREE.Vector3;
    abstract get name(): string;
    init(canvas: HTMLCanvasElement, cameraControl: ICameraControl, intersectionChecker: IModelIntersectionChecker): void;
    deInit(): void;
    dispose(): void;
    getViewCenter(): THREE.Vector3;
    setViewCenter(viewCenter: THREE.Vector3): void;
    getPivotPoint(): THREE.Vector3;
    setPivotPoint(pivotPoint: THREE.Vector3): void;
    setCameraParameters(iParams: {
        position: THREE.Vector3;
        eyeDir: THREE.Vector3;
        angle: number;
        viewCenter: THREE.Vector3;
    }): void;
    getCameraParameters(): {
        position: THREE.Vector3;
        eyeDir: THREE.Vector3;
        angle: number;
        viewCenter: THREE.Vector3;
    };
    getCamera(): THREE.Camera;
    clear(): void;
    protected handleHovered(object: THREE.Object3D): void;
    protected handleClick(object: THREE.Object3D, ctrlKey: boolean): void;
    protected handleDblClick(object: THREE.Object3D): void;
    protected abstract addEvents(): void;
    protected abstract removeEvents(): void;
    protected rotate(movement: THREE.Vector2): void;
    protected translate(prevPos: THREE.Vector2, currPos: THREE.Vector2): void;
    protected spin(movement: THREE.Vector2): void;
    protected zoom(deltaSign: number): void;
    protected resetSelection(): void;
}
```

## DesktopNavigationEventHandler
Обработчик навигации для десктопной версии приложения
```js
export class DesktopNavigationEventHandler extends NavigationEventHandler {
    protected _prevMousePos?: THREE.Vector2;
    protected _mouseLftIsDown: boolean;
    protected _mouseLftIsDownPos?: THREE.Vector2;
    protected _mouseRhtIsDown: boolean;
    protected _mouseMidIsDown: boolean;
    protected _boundOnMouseEnter: any;
    protected _boundOnMouseLeave: any;
    protected _boundOnMouseMove: any;
    protected _boundOnMouseClick: any;
    protected _boundOnMouseDoubleClick: any;
    protected _boundOnMouseScroll: any;
    protected _boundOnMouseDown: any;
    protected _boundOnMouseUp: any;
    protected _boundOnKeyDown: any;
    protected _boundOnKeyUp: any;
    get name(): string;
    protected addEvents(): void;
    protected removeEvents(): void;
    protected onMouseEnter(ev: MouseEvent): void;
    protected onMouseLeave(): void;
    protected onMouseMove(ev: MouseEvent): void;
    protected onMouseClick(ev: MouseEvent): void;
    protected onMouseDoubleClick(ev: MouseEvent): void;
    protected onMouseScroll(ev: WheelEvent): void;
    protected onMouseDown(ev: MouseEvent): void;
    protected onMouseUp(ev: MouseEvent): void;
    protected onKeyDown(ev: KeyboardEvent): void;
    protected onKeyUp(ev: KeyboardEvent): void;
    protected findSupportedEvent(array: string[]): string | undefined;
    protected isAllMouseButtonsUp(): boolean;
    protected setImpulseDirection(dir: Direction, add: boolean): void;
    protected setIncreasedImpulse(isIncreased: boolean): void;
}
```
## MobileNavigationEventHandler
Обработчик навигации для мобильной версии приложения

```js
export class MobileNavigationEventHandler extends NavigationEventHandler {
    protected _initialTap?: THREE.Vector2;
    protected _prevTap?: THREE.Vector2;
    protected _prevPinch?: [THREE.Vector2, THREE.Vector2];
    protected _boundOnTouchStart: any;
    protected _boundOnTouchEnd: any;
    protected _boundOnTouchMove: any;
    get name(): string;
    protected addEvents(): void;
    protected removeEvents(): void;
    protected onTouchStart(evt: TouchEvent): void;
    protected onTouchEnd(evt: TouchEvent): void;
    protected onTouchMove(evt: TouchEvent): void;
    protected onSwipe(currentPos: THREE.Vector2): void;
    protected onPinch(iTouchPair: [THREE.Vector2, THREE.Vector2]): void;
    protected getPinchCenter(iTouchPair: [THREE.Vector2, THREE.Vector2]): THREE.Vector2;
    protected getTouchPoint(touch: Touch): THREE.Vector2;
    protected getTouchPair(curTouches: TouchList): [THREE.Vector2, THREE.Vector2];
}
```