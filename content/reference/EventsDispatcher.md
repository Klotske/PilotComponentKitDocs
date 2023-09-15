---
title: "IEventsDispatcher"
draft: false
weight: 10
---

**IEventsDispatcher** - интерфейс управления подписками на события.

```js
export interface IEventsDispatcher {
  addEventListener(event: string, listener: EventListener, options?: object): void;
  removeEventListener(event: string, listener: EventListener): void;
  hasEventListener(event: string, listener: EventListener): boolean;
  dispatchEvent(event: string | Event): void;
  dispatchEventAsync(event: string | Event): void;
  clearListeners(): void;
}
```

## Методы

### addEventListener()
Подписаться на событие
```js
addEventListener(event: string, listener: EventListener, options?: object): void;
```
где:\
`event` -- <a href="../Events">имя события</a>.\
`listener` -- обработчик события.\
`options` -- дополнительные параметры подписки. Необязательный параметр.

### removeEventListener()
Отписаться от события
```js
removeEventListener(event: string, listener: EventListener): void;
```
где:\
`event` -- <a href="../Events">имя события</a>.\
`listener` -- обработчик события.

### hasEventListener()
Проверить подписан ли обработчик на событие.
```js
hasEventListener(event: string, listener: EventListener): boolean;
```
где:\
`event` -- <a href="../Events">имя события</a>.\
`listener` -- обработчик события.

Возвращает результат проверики.

### dispatchEvent()
Возбудить событие.

```js
dispatchEvent(event: string | Event): void;
```
где:\
`event` -- <a href="../Events">имя события</a> или объект `Event`.

### dispatchEventAsync()
Возбудить событие. Асинхронный метод.

```js
dispatchEventAsync(event: string | Event): void;
```
где:\
`event` -- <a href="../Events">имя события</a> или объект `Event`.

### clearListeners()
Удалить всех подписчиков.

```js
clearListeners(): void;
```