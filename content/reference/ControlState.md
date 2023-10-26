---
title: "ControlState"
draft: false
---

**ControlState.State**  - возможные состояния элементов управления.
```js
export namespace ControlState {
  export enum State {
    ACTIVE = 0, // Активна
    INACTIVE = 1, // Не активна
    DISABLED = 2 // Отключена
  }
}
```