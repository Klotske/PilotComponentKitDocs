---
title: "ModelElement"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**ModelElement** -- это класс для получения информации об элементе.

## Свойства

### id
Получает идентификатор элемента.
```js
get id(): string;
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

