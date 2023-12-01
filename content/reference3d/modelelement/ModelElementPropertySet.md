---
title: "ModelElementPropertySet"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 5
---

**ModelElementPropertySet** -- этот класс описывает свойства элемента модели.

```js
class ModelElementPropertySet {
  name: string;
  properties: ModelElementProperty[];
  type: IfcType;
}
```

## Свойства

### name
Имя категории свойств элемента
```js
name: string;
```

### properties
Список свойств элемента. Подробнее: см <a href="/reference3d/ModelElementProperty">ModelElementProperty</a>
```js
properties: ModelElementProperty[];
```

### type
Тип категории свойств элемента. Подробнее: см <a href="/reference3d/IfcType">IfcType</a>
```js
type: IfcType;
```