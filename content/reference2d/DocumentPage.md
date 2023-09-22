---
title: "DocumentPage"
draft: false
weight: 12
---

**DocumentPage** -- класс для взаимодействия со страницей документа.

```js
class DocumentPage {
  pageElement: HTMLElement;
  svg: SVGSVGElement;
  pageNumber: number;
  setScale(scale: number): void;
  getScale(): number;
}
```

## Поля

### pageElement
Содержит HTML-контейнер для страницы документа.
```js
pageElement: HTMLElement;
```

### svg
Содержит `svg` элемент с данными документа.
```js
svg: SVGSVGElement;
```

### pageNumber
Содержит номер страницы.
```js
pageNumber: number;
```

## Методы

### setScale
Задает новый масштаб для страницы.
```js
setScale(scale: number): void;
```
где:
`scale` -- масштаб.

### getScale
Получает масштаб для страницы.
```js
getScale(): number;
```