---
title: "ModelElementTree"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## ModelElementTree

Класс для работы с деревом элементов части консолидированной модлели.

## Методы

#### enumElementChildren()
Пройтись по всем элементам дерева и выполнить заданную функцию над каждым элементом.
```js
enumElementChildren(element: string | ModelElement, callback: (guid: string) => void, recursive?: boolean): void;
```
где:
`element` - идентификатор или экземпляр элемента.
`callback` - функция-обработчик элемента.
`recursive` - обрабатывать рекурсивно вес ветки элемнта или только его детей. Параметр не обязательный.

#### getRootElement()
Получить корневой элемент части консолидированной модели.
```js
getRootElement(): ModelElement;
```

#### getAllElements()
Получить все элементы дерева списком.
```js
getAllElements(): ModelElement[] 
```

#### isViewableElement()
Проверяет может ли элемент быть отрисован на сцене.
```js
isViewableElement(element: string | ModelElement): boolean;
```
где:
`element` - идентификатор или экземпляр элемента.

#### isDetachedElement()
Проверяет отсоединен элемент от корневого элемента или нет.
```js
isDetachedElement(element: string | ModelElement): boolean;
```
где:
`element` - идентификатор или экземпляр элемента.