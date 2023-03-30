---
title: "I3DRenderer"
draft: false
weight: 9
---

## I3DRenderer {#I3DRenderer}
**I3DRenderer** -- интерфейс, позволяющий взаимодействовать с программой отрисовки.
Поодробнее [THREE.WebGLRenderer](https://threejs.org/docs/#api/en/renderers/WebGLRenderer).

```js
export interface I3DRenderer {
  clear(color?: boolean, depth?: boolean, stencil?: boolean): void;
  clearDepth(): void;
  render(scene: THREE.Object3D, camera: THREE.Camera): void;
  getSize(target: THREE.Vector2): THREE.Vector2;
  setSize(width: number, height: number, updateStyle?: boolean): void;
  setViewport(x: THREE.Vector4 | number, y?: number, width?: number, height?: number): void;
  clippingPlanes: THREE.Plane[];
  domElement: HTMLCanvasElement;
}
```

## Поля

###  clippingPlanes
Глобальные секущие плоскости. Влияют на все операции отрисовки.
```js
  clippingPlanes: THREE.Plane[];
```

###  domElement {#domElement}
[Canvas](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas) на котором происходит отрисовка.
```js
  domElement: HTMLCanvasElement;
```

## Методы

###  clear() {#clear}
Метод очищает цветовой буффер, буффер глубины и буффер шаблона.
```js
  clear(color?: boolean, depth?: boolean, stencil?: boolean): void;
```
где:\
`color` -- `true`, для очистки цветового буффера. По умолчанию `true`.\
`depth` -- `true`, для очистки буффера глубины. По умолчанию `true`.\
`stencil` -- `true`, для очистки буффера шаблона. По умолчанию `true`.

###  clearDepth(): void
Метод очищает буффер глубины. Эквивалентно вызову [.clear](#clear)(false, true, false).
```js
  clearDepth(): void;
```

###  render()
Метод отрисовывает [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D) с помощью камеры.
```js
  render(scene: THREE.Object3D, camera: THREE.Camera): void;
```
где:\
`scene` -- объект для отрисовки. Подробнее: [THREE.Object3D](https://threejs.org/docs/index.html#api/en/core/Object3D).\
`camera` -- камера. Подробнее: [THREE.Camera](https://threejs.org/docs/index.html#api/en/cameras/Camera).

###  getSize()
Метод возвращает ширину и высоту [domElement](#domElement) в пикселях.
```js
  getSize(target: THREE.Vector2): THREE.Vector2;
```
где:\
`target` -- результат будет скопирован в этот [THREE.Vector2](https://threejs.org/docs/index.html#api/en/math/Vector2).\
Возвращает `target`.

###  setSize()
Метод изменяет размер [domElement](#domElement), а также [устанавливает область просмотра](#setViewport) в соответствии с этим размером.

```js
  setSize(width: number, height: number, updateStyle?: boolean): void;
```
где:\
`width` -- ширина окна.\
`height` -- высота окна.\
`updateStyle` -- при значении `false` предотвращает любые изменения стиля [domElement](#domElement).

###  setViewport() {#setViewport}
Метод устанавливает область просмотра для отрисовки: от (x, y) до (x + width, y + height).
```js
  setViewport(x: THREE.Vector4 | number, y?: number, width?: number, height?: number): void;
```
где:\
`x` -- x-координата левого нижнего угла окна, либо 4-компонентный вектор: [THREE.Vector4](https://threejs.org/docs/index.html#api/en/math/Vector4), задающий параметры окна.\
`y` --  y-координата левого нижнего угла окна.\
`width` -- ширина окна.\
`height` -- высота окна.