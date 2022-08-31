---
title: "ModelElementTree"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**ModelElementTree** -- это класс для работы с деревом элементов части консолидированной модлели.

## Методы

### enumElementChildren()
Метод позволяет пройтись по всем элементам дерева и выполнить заданную функцию над каждым элементом.
```js
enumElementChildren(element: string | ModelElement, callback: (guid: string) => void, recursive?: boolean): void;
```
где:

`element` -- идентификатор или экземпляр элемента.

`callback` -- функция-обработчик элемента.

`recursive` -- обрабатывать рекурсивно все ветки элемента или только его детей. Параметр не обязательный.

### getRootElement()
Метод позволяет получить корневой элемент части консолидированной модели.
```js
getRootElement(): ModelElement;
```

### getAllElements()
Метод позволяет получить все элементы дерева списком.
```js
getAllElements(): ModelElement[] 
```

### isViewableElement()
Метод проверяет, может ли элемент быть отрисован на сцене.
```js
isViewableElement(element: string | ModelElement): boolean;
```
где:
`element` -- идентификатор или экземпляр элемента.

### isDetachedElement()
Метод проверяет, отсоединён элемент от корневого элемента или нет.
```js
isDetachedElement(element: string | ModelElement): boolean;
```
где:
`element` -- идентификатор или экземпляр элемента.