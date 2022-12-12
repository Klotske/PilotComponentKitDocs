---
title: "Extension"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 9
---

**Extension** -- это базовый класс описания расширения.

## Свойства

### _viewer
```js
protected _viewer: Viewer3D;
```

## Методы

### load()
Метод вызвается, когда расширение было загружено.
```js
load() : boolean | Promise<boolean>;
```

### unload()
Метод вызвается, когда расширение было выгружено.
```js
unload(): boolean;
```

### activate()
Активировать работу плагина
```js
activate() : boolean;
```
Возвращает `true`, если активация прошла успешно.

### deactivate()
Деактивировать работу плагина
```js
deactivate(): boolean;
```
Возвращает `true`, если деактивация прошла успешно.

### getName()
Метод вызвается, когда расширение пытается получить имя расширения.
```js
getName(): string;
```

### onToolbarCreated()
Метод вызывается, когда панель инструментов построилась, и расширение имеет возможность добавить/изменить/удалить элементы управления.
```js
onToolbarCreated(builder: ToolbarBuilder): void;
```
где:
`builder` -- построитель панели инструментов.

### onMouseDown()
Метод вызывается, когда произошло событие нажатия левой клавиши мыши.

```js
onMouseDown(event: MouseEvent): void;
```
где:
`event` -- событие мыши.

### onMouseMove()
Метод вызывается, когда произошло событие перемещения мыши.

```js
onMouseMove(event: MouseEvent): void;
```
где:
`event` -- событие мыши.

### onMouseUp()
Метод вызывается, когда произошло событие отпускания левой клавиши мыши.

```js
onMouseUp(event: MouseEvent): void;
```
где:
`event` -- событие мыши.
