---
title: "IRenderOperationContext"
draft: false
weight: 9
---

## IRenderOperationContext {#IRenderOperationContext}
**IRenderOperationContext** -- интерфейс, представляющий контекст операции рендера.

```js
export interface IRenderOperationContext {
  isRedrawRequested: boolean;
  isForcedExecution: boolean;

  get renderer(): I3DRenderer;
  get camera(): THREE.Camera;
  get settings(): RenderViewSettings;
  get isNavigation(): boolean;
  get isSuspensionRequested(): boolean;
  get remainedTime(): DOMHighResTimeStamp;
  get elapsedTime(): DOMHighResTimeStamp;
  get lastFrameTimestamp(): DOMHighResTimeStamp;
  get lastRenderCycleTimestamp(): DOMHighResTimeStamp;
  get isElapsed(): boolean;
  get userData(): Map<string, object>;
}
```

## Поля

###  isRedrawRequested
Задает принудительную перерисовку сцен.
```js
isRedrawRequested: boolean;
```

###  isForcedExecution {#isForcedExecution}
Снимает ограничение на время исполнения операций рендера.\
Если `true`, операции исполняются принудительно, время исполнения не ограничено.
```js
isForcedExecution: boolean;
```

## Свойства

###  get renderer()
Возвращает объект [I3DRenderer](../I3DRenderer), используемый для отрисовки сцен.
```js
  get renderer(): I3DRenderer;
```
Возвращает объект [I3DRenderer](../I3DRenderer).

###  get camera()
Возвращает камеру, используемую для отрисовки сцен.
```js
  get camera(): THREE.Camera;
```
Возвращает объект [THREE.Camera](https://threejs.org/docs/#api/en/cameras/Camera).

###  get settings()
Возвращает текущие настройки рендера.
```js
  get settings(): RenderViewSettings;
```
Возвращает настройки рендера.

###  get isNavigation()
Показывает производится ли в данный момент навигация по сцене.
```js
  get isNavigation(): boolean;
```
Возвращает `true`, если навигация активна. В противном случае возвращает `false`.

###  get isSuspensionRequested() {#isSuspensionRequested}
Показывает что необходимо приостановить текущую операцию рендера и вернуть управление планировщику.
```js
  get isSuspensionRequested(): boolean;
```
Возвращает `true`, если требуется приостановить операцию. В противном случае возвращает `false`.\
Если [isForcedExecution](#isForcedExecution) равен `true`, то [isSuspensionRequested](#isSuspensionRequested) всегда возвращает `false`.

###  get remainedTime()
Сообщает сколько выделенного времени осталось на выполнение операции.
```js
  get remainedTime(): DOMHighResTimeStamp;
```
Возвращает [DOMHighResTimeStamp](https://developer.mozilla.org/en-US/docs/Web/API/DOMHighResTimeStamp) - количество оставшегося времени на выполнение.

###  get elapsedTime()
Сообщает сколько времени затрачено на выполнение операций в текущей итерации.
```js
  get remainedTime(): DOMHighResTimeStamp;
```
Возвращает [DOMHighResTimeStamp](https://developer.mozilla.org/en-US/docs/Web/API/DOMHighResTimeStamp) - затраченное время текущей итерации.

###  get lastFrameTimestamp()
Хранит время отрисовки последнего кадра.
```js
  get lastFrameTimestamp(): DOMHighResTimeStamp;
```
Возвращает [DOMHighResTimeStamp](https://developer.mozilla.org/en-US/docs/Web/API/DOMHighResTimeStamp) - время последней отрисовки.

###  get lastRenderCycleTimestamp()
Хранит время завершения последнего цикла рендера.
```js
  get lastRenderCycleTimestamp(): DOMHighResTimeStamp;
```
Возвращает [DOMHighResTimeStamp](https://developer.mozilla.org/en-US/docs/Web/API/DOMHighResTimeStamp) - время последнего цикла рендера.

###  get isElapsed() {#isElapsed}
Показывает закончилось ли время текущей итерации, выделенное на выполнение операций рендера.
```js
  get isElapsed(): boolean;
```
Возвращает `true`, если выделенное время кончилось. В противном случае возвращает `false`.\
В случае, если [isElapsed](#isElapsed) равен `true`, а [isForcedExecution](#isForcedExecution) равен `false`, то [isSuspensionRequested](#isSuspensionRequested) вернёт `true`.

###  get userData()
Данные, совместно используемые операциями в одном цикле рендера.
```js
  get userData(): Map<string, object>;
```
Возвращает словарь `Map<string, object>`.