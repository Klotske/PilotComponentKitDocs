---
title: "CameraParameters"
date: 2022-09-30T14:44:03+03:00
draft: false
weight: 9
---

**CameraParameters** -- описание параметров камеры.

## Свойства

### position
Позиция камеры. Задается параметрами x, y, z. Подробнее смотри [Point3](../Point3).
```js
position: Point3;
```

### eyeDir
Вектор направления взгляда камеры. Задается параметрами x, y, z. Подробнее смотри [Point3](../Point3).
```js
eyeDir: Point3;
```

### angle
Поле зрения камеры. Задается в радианах.
```js
angle: number
```

### viewCenter
Вектор точки взгляда. Подробнее смотри [Point3](../Point3).
```js
viewCenter: Point3;
```
