---
title: "DocumentProxy"
draft: false
weight: 11
---

**DocumentProxy** -- класс описания документа.

```js
class DocumentProxy {
  get pages(): DocumentPage[];
  get layers(): ILayersManager;
  getPage(pageNumber: number): DocumentPage | undefined;
  getPageByTarget(element: HTMLElement): DocumentPage | null;
  getFirstPage(): DocumentPage | undefined;
}
```

## Свойства

### pages
Содержит все страницы документа.
```js
get pages(): DocumentPage[];
```

### layers
Содержит все слои документа разбитые по страницам. Подробнее: <a href="../../reference2d/ILayersManager">ILayersManager</a>.
```js
get layers(): ILayersManager;
```

## Методы

### getPage
Получает заданную страницу. Подробнее: <a href="../../reference2d/DocumentPage">DocumentPage</a>.
```js
getPage(pageNumber: number): DocumentPage | undefined;
```
где:\
`pageNumber` -- номер страницы.

### getPageByTarget
Получает страницу по заданному HTML-элементу. Подробнее: <a href="../../reference2d/DocumentPage">DocumentPage</a>.
```js
getPageByTarget(element: HTMLElement): DocumentPage | null;
```
где:\
`element` -- HTML-элемент.

### getFirstPage()
Получает первую страницу документа. Подробнее: <a href="../../reference2d/DocumentPage">DocumentPage</a>.
```js
getFirstPage(): DocumentPage | undefined;
```
где:\
`element` -- HTML-элемент.



