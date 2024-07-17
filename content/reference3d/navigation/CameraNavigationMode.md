---
title: "CameraNavigationMode"
date: 2022-09-30T14:44:03+03:00
draft: false
weight: 9
---
## CameraNavigationMode {#CameraNavigationMode}
**CameraNavigationMode** -- классификация перемещений, осуществляемых камерой при навигации.

```js
export enum CameraNavigationMode {
  // Движение отсутствует
  None = 0,
  // Вращение по круговой орбите
  Rotation = 1 << 0,
  // Линейное движение
  Translation = 1 << 1,
  // Вращение вокруг собственной оси
  Spin = 1 << 2,
  // Приближение или удаление
  Zoom = 1 << 3
}
```

## CameraMode {#CameraMode}
**CameraMode** -- классификация типов проекций камеры, используемых для отображения объектов на сцене.

```js
export enum CameraMode {
  // Ортогональная проекция
  ORTHOGRAPHIC = 0,
  // Перспективная проекция
  PERSPECTIVE = 1,
}
```