---
title: "IDocument"
draft: false
weight: 10
---

**IDocument** -- это интерфейс для доступа к элементам управления документа.

```js
export interface IDocument {
  increaseScale(steps?: number, scaleFactor?: number): void;
  decreaseScale(steps?: number, scaleFactor?: number): void;
  fit(): void;

  getPageAsync(pageNumber: number): Promise<IDocumentPage>;
  getPageByTarget(element: HTMLElement): IDocumentPage | undefined;

  scrollPageIntoViewAsync(pageNumber: number): Promise<void>;
}
```

## Методы

### increaseScale
Увиличивает масштаб отображения документа.
```js
increaseScale(steps?: number, scaleFactor?: number): void;
```
где:\
`steps` -- количество шагов,
`scaleFactor` -- масштаб.

### decreaseScale
Уменьшает масштаб отображения документа.
```js
decreaseScale(steps?: number, scaleFactor?: number): void;
```
где:\
`steps` -- количество шагов,
`scaleFactor` -- масштаб.

### fit
Выравнивает документ по ширене просмотрщика.
```js
fit(): void;
```

### getPageAsync
Получает страницу по номеру. Подробнее [IDocumentPage](../IDocumentPage)
```js
getPageAsync(pageNumber: number): Promise<IDocumentPage>;
```
где:\
`pageNumber` -- номер запрашиваемой страницы.

### getPageByTarget
Получает страницу по заданному HTML-элементу. Подробнее [IDocumentPage](../IDocumentPage)
```js
getPageByTarget(element: HTMLElement): IDocumentPage | undefined;
```
где:\
`element` -- HTML-элемент, который находится внутри страницы

### scrollPageIntoViewAsync
Проскролировать до указанной страницы
```js
scrollPageIntoViewAsync(pageNumber: number): Promise<void>;
```
где:\
`pageNumber` -- номер страницы.
