---
title: "ClippingPlaneExtension"
draft: false
weight: 1
---

**ClippingPlaneExtension** -- расширение, которое позволяет задать секущие плоскости и кубы сечений на сцене.

Расширение имеет имя `PilotWeb3D.ClippingPlane`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/ClippingPlane3D/ClippingPlane.min.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ClippingPlane");
```

## Методы

### activate()
Метод активирует расширение.
```js
activate(): void;
```
### deactivate()
Метод деактивирует расширение.
```js
deactivate(): void;
```

### addClipping()
Метод добавляет секущие объекты - секущие плоскости и кубы сечения на сцену.
```js
addClipping(clipping: ClippingDescription[]): void;
```
где:\
`clipping` -- список описаний секущих плоскостей и кубов сечения. Подробнее: [ClippingDescription](#ClippingDescription).

### getClipping()
Метод возвращает описания секущих плоскостей и кубов сечения на сцене. Подробнее: [ClippingDescription](#ClippingDescription).
```js
public getClipping(clippingIDs?: string[]): ClippingDescription[];
```
где:\
`clippingIDs` -- список идентификаторов секущих плоскостей и кубов сечения. Необязательный параметр. Если не задан, то возвращается описание всех секущих объектов.

### removeClipping() {#removePlanes}
Метод удаляет секущие плоскости и кубы сечения.
```js
public removeClipping(clippingIDs?: string[]): void;
```
где:\
`clippingIDs` -- список идентификаторов секущих плоскостей и кубов сечения. Необязательный параметр. Если не задан, то удаляются все секущие объекты.

### ClippingPlaneExtension.ClippingDescription {#ClippingDescription}
Тип описания секущего объекта.
```js
export type ClippingDescription = {
    normal: Point3,
    origin: Point3, 
    guid?: string,
    size?: number,
    isCube?: boolean,   // определено только для куба сечений
    scale?: Point3   // определено только для куба сечений
  };
```
### normal
Нормаль плоскости сечения, в случае описания секущей плоскости. Для куба сечения задает ориентацию Z-оси куба.
```js
normal: Point3
```
где:\
`normal` -- координаты вектора нормали в мировом пространстве. Подробнее: [Point3](../../reference3d/navigation/Point3).

### origin
Точка задает положение центра отображения секущей плоскости. Для куба сечения задает положение центра куба.
```js
origin: Point3
```
где:\
`origin` -- координаты точки в мировом пространстве. Подробнее: [Point3](../../reference3d/navigation/Point3).

### guid
Идентификатор плоскости сечения. Необязательный параметр. Может использоваться для выборочного [удаления](#removePlanes) плоскостей сечения.
```js
guid?: string 
```

### size
Задает длину ребра отображения секущей плоскости. Для куба сечения задает длину ребра куба. Опциональный параметр.
```js
size?: number 
```
Если не задан, то для секущей плоскости используется значение по умолчанию: `10000`. Для куба сечения размер вычисляется таким образом, чтобы куб занимал одну треть экрана по высоте.

### isCube
Флаг указывает на то, что описание соответствует кубу сечения. Для куба сечения принимает значение `true`, в противном случае может быть `undefined` или `false`.
```js
isCube?: boolean 
```

### scale
Задает масштаб куба сечения, опциональный параметр.
```js
scale?: Point3 
```
где:\
`scale` -- параметры масштабирования куба сечения. Подробнее: [Point3](../../reference3d/navigation/Point3).