---
title: "ILayerManager"
date: 2023-08-29T14:44:03+03:00
draft: false
weight: 10
---

**ILayerManager** -- это интерфейс для управления слоями на документе.

```js
type LayerByPageMap = Map<number, ILayer>;

interface ILayersManager {
  createLayer(name: string): void;
  deleteLayer(name: string): boolean;
  getLayer(name: string): LayerByPageMap | null;
  hasLayer(name: string): boolean;
}
```

## Методы

### createLayer
Создает новый слой на документе.
```js
createLayer(name: string): void;
```
где:\
`name` -- уникальное имя слоя.

### deleteLayer
Удаляет слой из документа.
```js
deleteLayer(name: string): boolean;
```
где:\
`name` -- уникальное имя слоя.

### getLayer
Получает слой документа.
```js
getLayer(name: string): Map<number, ILayer> | null;
```
где:\
`name` -- уникальное имя слоя.
Возвращает карту слоев документа разбитую по страницам. Подробнее: <a href="../ILayer">ILayer</a>

### hasLayer
Проверяет существует ли слой у документа.
```js
hasLayer(name: string): boolean;
```
где:\
`name` -- уникальное имя слоя.

