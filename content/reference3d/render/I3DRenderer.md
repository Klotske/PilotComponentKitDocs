---
title: "I3DRenderer"
draft: false
weight: 9
---

## I3DRenderer {#I3DRenderer}
**I3DRenderer** -- интерфейс, позволяющий взаимодействовать с программой отрисовки.
Поодробнее смотри [THREE.WebGLRenderer](https://threejs.org/docs/#api/en/renderers/WebGLRenderer).

```js
export interface I3DRenderer {
  clear(color?: boolean, depth?: boolean, stencil?: boolean): void;
  clearDepth(): void;
  render(scene: THREE.Object3D, camera: THREE.Camera): void;
  getSize(target: THREE.Vector2): THREE.Vector2;
  setSize(width: number, height: number, updateStyle?: boolean): void;
  setViewport(x: THREE.Vector4 | number, y?: number, width?: number, height?: number): void;
  dispose(): void;
  clippingPlanes: THREE.Plane[];
  domElement: HTMLCanvasElement;
}
```

## Поля

###  clippingPlanes: THREE.Plane[]
Глобальные секущие плоскости. Влияют на все операции отрисовки.
```js
  clippingPlanes: THREE.Plane[];
```

###  domElement: HTMLCanvasElement {#domElement}
[Canvas](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas) на котором происходит отрисовка.
```js
  domElement: HTMLCanvasElement;
```

## Методы

###  clear(color?: boolean, depth?: boolean, stencil?: boolean): void {#clear}
Метод очищает цветовой буффер, буффер глубины и буффер шаблона.
```js
  clear(color?: boolean, depth?: boolean, stencil?: boolean): void;
```
где:\
`color` -- `true` для очистки цветового буффера. По умолчанию `true`.\
`depth` -- `true` для очистки буффера глубины. По умолчанию `true`.\
`stencil` -- `true` для очистки буффера шаблона. По умолчанию `true`.

###  clearDepth(): void
Очистите буфер глубины.  Эквивалентно вызову [.clear](#clear)(false, true, false).
```js
  clearDepth(): void;
```

###  render(scene: THREE.Object3D, camera: THREE.Camera): void
Отрисовывает [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D) с помощью камеры.
```js
  render(scene: THREE.Object3D, camera: THREE.Camera): void;
```
где:\
`scene` -- объект для отрисовки. Подробнее смотри [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D).\
`camera` -- камера. Подробнее смотри [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).

###  getSize(target: THREE.Vector2): THREE.Vector2
Возвращает ширину и высоту [domElement](#domElement) в пикселях.
```js
  getSize(target: THREE.Vector2): THREE.Vector2;
```
где:\
`target` -- результат будет скопирован в этот [THREE.Vector2](https://threejs.org/docs/index.html#api/en/math/Vector2).\
Возвращает `target`.

###  setSize(width: number, height: number, updateStyle?: boolean): void;
Изменяет размер [domElement](#domElement) с учетом соотношения пикселей устройства, а также [устанавливает область просмотра](#setViewport) в соответствии с этим размером, начиная с (0, 0).  

```js
  setSize(width: number, height: number, updateStyle?: boolean): void;
```
где:\
`width` -- ширина окна.\
`height` -- высота окна.\
`updateStyle` -- при значении `false` предотвращает любые изменения стиля [domElement](#domElement).

###  setViewport(x: THREE.Vector4 | number, y?: number, width?: number, height?: number): void; {#setViewport}
Метод устанавливает область просмотра для отрисовки от (x, y) до (x + width, y + height).
```js
  setViewport(x: THREE.Vector4 | number, y?: number, width?: number, height?: number): void;
```
где:\
`x` -- x-координата левого нижнего угла окна, либо [4-компонентный вектор](https://threejs.org/docs/index.html#api/en/math/Vector4) задающий параметры окна.\
`y` --  y-координата левого нижнего угла окна.\
`width` -- ширина окна.\
`height` -- высота окна.

###  dispose(): void
Освобождает ресурсы, связанные с графическим процессором, выделенные этим экземпляром.
```js
  dispose(): void;
```