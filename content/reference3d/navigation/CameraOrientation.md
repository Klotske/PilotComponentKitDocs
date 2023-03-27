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
Вектор направления взгляда камеры.
```js
viewDir: THREE.Vector3;
```

### upDir
Вектор направления верха камеры. Не обязательный параметр. Если не указан, то сохраняется текущее направление верха камеры.
```js
upDir: THREE.Vector3;
```

