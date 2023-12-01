---
title: "ModelLoadingOptions"
draft: false

---

**ModelLoadingOptions** - опции загрузки модели в компонент **PilotWeb3d**.

```js
export class ModelLoadingOptions {
  guid: string; // уникальный идентификатор модели
  isConsolidatedModel?: boolean; // флаг, позволяющий дозагрузить модели в уже загруженную сцену
}
```