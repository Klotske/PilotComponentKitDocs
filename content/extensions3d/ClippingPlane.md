---
title: "ClippingPlaneExtension"
draft: false
---

**ClippingPlaneExtension** -- расширение, которое позволяет задать секущие плоскости на сцене.

Расширение имеет имя `PilotWeb3D.ClippingPlane`.

Пример подключения в `html`:
```html
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/ClippingPlane3D/ClippingPlane.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ClippingPlane");
```

## Методы

### activate()
Активировать расширение.
```js
activate(): void;
```
### deactivate()
Деактивировать расширение.
```js
deactivate(): void;
```

### addPlanes()
Добавить плоскости сечения на основную сцену, к уже существующим.
```js
addPlanes(planes: ClippingPlaneDescription[]): void;
```
где:\
`planes` -- список описаний плоскостей сечения. Подробнее смотри [ClippingPlaneDescription](#ClippingPlaneDescription).

### setPlanes()
Задать плоскости сечения на основной сцене, уже существующие плоскости на сцене удаляются.
```js
public setPlanes(planes: ClippingPlaneDescription[]): void;
```
где:\
`planes` -- список описаний плоскостей сечения. Подробнее смотри [ClippingPlaneDescription](#ClippingPlaneDescription).

### removePlanes() {#removePlanes}
Удалить плоскости сечения с основной сцены.
```js
public removePlanes(planeIDs?: string[]): void;
```
где:\
`planeIDs` -- (опционально), список идентификаторов плоскостей сечения. Если ничего не определено, то удаляются все существующие плоскости сечения.

### ClippingPlaneExtension.ClippingPlaneDescription {#ClippingPlaneDescription}
Описание плоскости сечения.
```js
export type ClippingPlaneDescription = {
    normal: { x: number, y: number, z: number },
    origin: { x: number, y: number, z: number }, 
    guid?: string };
```
### normal
Нормаль плоскости сечения.
```js
normal: { x: number, y: number, z: number }, 
```
где: `x`,`y`,`z` -- координаты вектора нормали в мировом пространстве.

### origin
Точка, принадлежащая плоскости сечения. Также в эту точку помещается `ClippingPlaneViewObject` - вспомогательный визуальный oбъект, для отображения плоскости.
```js
normal: { x: number, y: number, z: number }
```
где: `x`,`y`,`z` -- координаты точки в мировом пространстве.

### guid
Идентификатор плоскости сечения. Необязательный параметр. Может использоваться для выборочного [удаления](#removePlanes) плоскостей сечения.
```js
guid?: string 
```