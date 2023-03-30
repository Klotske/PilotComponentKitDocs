---
title: "ModelElementProperty"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 5
---

**ModelElementProperty** -- этот класс описывает свойство элемента модели.

```js
class ModelElementProperty {
  name: string;
  unit: number;
  value: ModelElementPropertyValue;
}
```

## Свойства

### name
Имя свойства элемента
```js
name: string;
```

### unit
Единица измерения свойства элемента.
```js
unit: number;
```

### value
Значение свойства элемента. Подробнее: см <a href="/reference3d/ModelElementPropertyValue">ModelElementPropertyValue</a>
```js
value: ModelElementPropertyValue;
```