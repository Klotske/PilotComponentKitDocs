---
title: "CameraOrientation"
date: 2022-09-30T14:44:03+03:00
draft: false
weight: 9
---

**CameraOrientation** -- описание ориентации камеры в мировом пространстве.
```js
export type CameraOrientation = {
  viewDir: THREE.Vector3,
  upDir?: THREE.Vector3
};
```

## Свойства

### viewDir
```js
viewDir: THREE.Vector3;
```
Вектор направления взгляда камеры.

### upDir
```js
upDir: THREE.Vector3;
```
(Опционально) Вектор направления верха камеры. Если не указан, сохраняется текущее направление верха камеры.

