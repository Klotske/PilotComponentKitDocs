---
title: "ModelPart"
date: 2022-08-29T14:44:03+03:00
draft: false

---

**ModelPart** -- этот интерфейс позволяет получить информацию о части консолидированной модели.

## Свойства

### id
Получает идентификатор части консолидированной модели.
```js
get id() : string;
```

### elementTree()
Получает экземпляр дерева элементов части консолидированной модели.
```js
get elementTree() : ModelElementTree
```

## Методы

### setModelPartPlacement()
Метод позволяет задать смещение и масштаб части консолидированной модели на сцене.
```js
  setModelPartPlacement(placement?: THREE.Matrix4Tuple | number[], scaling?: number): void;
```
где:\
`placement` -- матрица трансформации в глобальном пространстве, 4х4 - row-major order.

`scaling` -- масштаб части модели.

### dispose()
Освобождает ресурсы, занятые частью консолидированной модели.
```js
dispose() : void;
```
