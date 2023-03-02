---
title: "ModelElement"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 5
---

**ModelElement** -- это класс для получения информации об элементе.

## Свойства

### id
Получает идентификатор элемента.
```js
get id(): string;
```

### modelPartId
Получает идентификатор части модели, к которой относится этот элемент.
```js
get modelPartId(): string;
```

### parent
Получает родительский элемент. Если родитель отсутствует, то  вернется значение `undefined`.
```js
get parent(): ModelElement | undefined;
```

### type
Получает тип элемента.
```js
get type(): string;
```

### name
Получает имя элемента.
```js
get name(): string;
```

### children
Получает детей элемента.
```js
get children(): ModelElement[];
```

### hasGeometry
Проверяет наличие геометрии у элемента.
```js
get hasGeometry(): boolean;
```

### boundingBoxCenter
Получает центр bounding box элемента.
```js
get boundingBoxCenter(): Point3;
```
Подробнее смотри <a href="../Point3">Point3</a>.
