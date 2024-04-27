---
title: "ModelLoadingOptions"
draft: false

---

**ModelLoadingOptions** - опции загрузки модели в компонент **PilotWeb3d**.

```js
export class ModelLoadingOptions {
  guid: string; // уникальный идентификатор модели
  isConsolidatedModel?: boolean; // флаг, позволяющий дозагрузить модели в уже загруженную сцену
  placement?: number[]; // пользовательское смещение модели в глобальном пространстве (матрица 4х4, Row-major order)
  scale?: number; // пользовательский масштаб модели
}
```