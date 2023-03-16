---
title: "DesktopNavigation"
draft: false
weight: 9
---

## DesktopNavigation
**DesktopNavigation** - Обработчик навигации для десктопной версии приложения
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
}
```