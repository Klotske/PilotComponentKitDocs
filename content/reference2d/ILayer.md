---
title: "ILayer"
date: 2023-08-29T14:44:03+03:00
draft: false
weight: 10
---

**ILayer** -- это интерфейс для управления слоем на странице.

```js
interface ILayer {
  get div(): HTMLDivElement;
  addOverlay(overlay: HTMLElement): boolean;
  removeOverlay(overlay: HTMLElement): boolean;
  getOverlays(): HTMLElement[];
  getViewBox(): DOMRect;
  dispose(): void;
}
```
## Свойства

### div
Содержит HTML-элемент для слоя.
```js
get div(): HTMLDivElement;
```

## Методы

### addOverlay
Добавляет HTML-элемент на слой.
```js
addOverlay(overlay: HTMLElement): boolean;
```
где:\
`overlay` -- HTML-элемент, который надо добавить на слой.

### removeOverlay
Удаляет HTML-элемент из слоя.
```js
removeOverlay(overlay: HTMLElement): boolean;
```
где:\
`overlay` -- HTML-элемент, который надо удалить из слой.

### getOverlays
Получает все элементы добавленные на слой.
```js
getOverlays(): HTMLElement[];
```

### getViewBox
Получает габариты слоя.
```js
getViewBox(): DOMRect;
```

### dispose
Удаляет все ресурсы на слое.
```js
dispose(): void;
```
