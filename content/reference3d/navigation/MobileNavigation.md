---
title: "MobileNavigation"
draft: false
weight: 9
---

## MobileNavigation
**MobileNavigation** - Обработчик навигации для мобильной версии приложения.

```js
export class MobileNavigation extends NavigationTool {
  protected _initialTap?: THREE.Vector2;
  protected _prevTap?: THREE.Vector2;
  protected _prevPinch?: [THREE.Vector2, THREE.Vector2];

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