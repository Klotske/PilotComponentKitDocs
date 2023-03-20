---
title: "UpdateType"
draft: false
weight: 9
---

**UpdateType** -- флаговое перечисление, описывающее типы изменений [ViewObject](../ViewObject).

```js
export enum UpdateType {
  /**No changes */
  NONE = 0,
  /**Object has been removed from the scene */
  REMOVE = 1 << 0,
  /**Object has been added to the scene */
  ADD = 1 << 1,
  /**Оbject has been significantly changed. Re-insert required */
  HARD = 1 << 2,
  /**Child objects has been changed*/
  Children = 1 << 3,
  /**Object geometry has been changed */
  Geometry = 1 << 4,
  /**Object position has been changed */
  Position = 1 << 5,
  /**Object material has been changed */
  Material = 1 << 6,
  /**Object color has been changed */
  Color = 1 << 7,
  /**Object selection status has been changed */
  Selection = 1 << 8,
  /**Object visibility has been changed */
  Visibility = 1 << 9,
}
```