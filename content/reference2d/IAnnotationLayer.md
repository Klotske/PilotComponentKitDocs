---
title: "IAnnotationLayer"
draft: false
weight: 10
---

**IAnnotationLayer** -- интерфейс управления замечаниями на странице документа.

```js
export interface IAnnotationLayer {
  get pageDiv(): HTMLDivElement;
  get div(): HTMLDivElement | null;

  addOverlay(overlay: HTMLElement): void;
  removeOverlay(overlay: HTMLElement): void;
  getOverlays(): HTMLElement[];
}
```

## Свойства

### pageDiv
Содержит корневой HTML-элемент страницы.
```js
get pageDiv(): HTMLDivElement;
```

### div
Содержит корневой HTML-элемент слоя замечаний.
```js
get div(): HTMLDivElement | null;
```

## Методы

### addOverlay
Добавляет HTML-элемент на слой замечаний.
```js
addOverlay(overlay: HTMLElement): void;
```
где:\
  `overlay` -- HTML-элемент.


### removeOverlay
Удаляет HTML-элемент из слоя замечаний.
```js
removeOverlay(overlay: HTMLElement): void;
```
где:\
  `overlay` -- HTML-элемент.


### getOverlays
Получает все добавленные на слой замечаний HTML-элементы.
```js
getOverlays(): HTMLElement[];
```


