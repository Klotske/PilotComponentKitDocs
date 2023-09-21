---
title: "CameraParameters"
date: 2022-09-30T14:44:03+03:00
draft: false
weight: 9
---

**CameraParameters** -- описание параметров камеры.
```js
export type CameraParameters = {
  /** Camera position */
  position: Point3,
  /** Camera view direction: vector pointing from camera to target */
  eyeDir: Point3,
  /** Field of view: angle in radians */
  angle: number,
  /** (optional) Camera up vector*/
  upDir?: Point3,
  /** (optional) Vector pointing to the center of viewing area.*/
  viewCenter?: Point3
};
```

### position
Позиция камеры. Подробнее: [Point3](../Point3).
```js
position: Point3;
```

### eyeDir
Вектор направления взгляда камеры. Подробнее: [Point3](../Point3).
```js
eyeDir: Point3;
```

### angle
Поле зрения камеры. Задается в радианах.
```js
angle: number
```

### upDir
Вектор направления верха камеры, не обязательный параметр. Подробнее: [Point3](../Point3).
```js
upDir?: Point3
```

### viewCenter {#viewCenter}
Вектор точки взгляда, не обязательный параметр. Подробнее: [Point3](../Point3).\
Используется как опорная точка при вращении камеры во время навигации, если не задан [PivotPoint](../INavigationTool/#setPivotPoint). 
```js
viewCenter?: Point3;
```
