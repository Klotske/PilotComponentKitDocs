---
title: "IDocumentPage"
draft: false
weight: 10
---

**IDocumentPage** - интерфейс управления страницей документа.

```js
export interface IDocumentPage {
  get div(): HTMLDivElement;
  get canvas(): HTMLCanvasElement | SVGSVGElement;
  get pageNumber(): number;
  get viewport(): DOMRect;
  get annotationLayer(): IAnnotationLayer | null;
  get height() : number;
  get width() : number;
  get scale(): number;

  update(params?: IPageUpdateParams): void;
  dispose();
}
```

## Свойства

### div
Содержит корневой HTML-элемент страницы.
```js
get div(): HTMLDivElement;
```

### canvas
Содержит HTML-элемент с содержимым страницы.
```js
get canvas(): HTMLCanvasElement | SVGSVGElement;
```

### pageNumber
Содержит номер страницы.
```js
get pageNumber(): number;
```

### viewport
Содержит габаритные размеры страницы.
```js
get viewport(): DOMRect;
```

### annotationLayer
Содержит объект для взаимодействия со слоем замечаний. Подробнее: [IAnnotationLayer](../IAnnotationLayer).
```js
get annotationLayer(): IAnnotationLayer | null;
```

### height
Содержит высоту страницы в пикселях.
```js
get height() : number;
```

### width
Содержит ширину страницы в пикселях.
```js
get width() : number;
```

### scale
Содержит текущий масштаб страницы.
```js
get scale() : number;
```

## Методы

### update
Обновляет страницу с заданными параметрами. Подробнее: [IPageUpdateParams](../IPageUpdateParams).
```js
update(params?: IPageUpdateParams): void;
```

### dispose
Очищает ресурсы страницы.
```js
dispose(): void;
```