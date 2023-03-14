---
title: "NavigationAgent"
draft: false
weight: 9
---

## NavigationAgent {#NavigationAgent}
**NavigationAgent** -- класс, предоставляющий источники событий навигации.
```js
export class NavigationAgent {

  readonly canvasNavigationSource: INavigationEventSource;
  readonly keyboardNavigationSource: INavigationEventSource;

  getNavigationArea(): DOMRect;
}
```

### Поля
#### canvasNavigationSource : INavigationEventSource
Источник DOM-событий для навигации с помощью мыши, тачпада и т.д.. Смотри [INavigationEventSource](#INavigationEventSource).
```js
readonly canvasNavigationSource: INavigationEventSource;
```
{{< hint type="tip" icon=gdoc_info_outline title="Примечание">}}
Пример подписки на событие `mousemove`, [опции](#NavigationEventOptions) по умолчанию:\
   *capture*: `false`; \
   priority: `NavigationHandlerPriority.CustomExtensions`; \
   *alwaysHandle*: `false`; \
   *navigationTargetName*?: `undefined`;
```js
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove);
```
или
```js
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove, false); //capture: false
```

Те же опции, указанные явно:
```js
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, undefined));
```

Для отписки от события, нужно передавать те же параметры, что и при подписке:
```js
navigationAgent.canvasNavigationSource.removeEventListener("mousemove", onMouseMove, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, undefined));
```
{{< /hint >}}

#### keyboardNavigationSource : INavigationEventSource
Источник DOM-событий для навигации с помощью клавиатуры. Смотри [INavigationEventSource](#INavigationEventSource).
```js
readonly keyboardNavigationSource: INavigationEventSource;
```
{{< hint type="tip" icon=gdoc_info_outline title="Примечание">}}
Пример подписки на событие `keyup`:
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onMouseMove);
```
или
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp,  false);
```
или
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, {capture: false});
```
или
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
```

Для отписки от события, нужно передавать те же параметры, что и при подписке:
```js
navigationAgent.keyboardNavigationSource.removeEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
```
{{< /hint >}}

### Методы

#### getNavigationArea(): DOMRect;
Метод позволяет получить прямоугольник текущей рабочей области навигации.
```js
getNavigationArea(): DOMRect;
```
Возвращает объект [DOMRect](https://developer.mozilla.org/en-US/docs/Web/API/DOMRect).

## INavigationEventSource {#INavigationEventSource}
**INavigationEventSource** -- интерфейс источника событий навигации.
```js
export interface INavigationEventSource {
  addEventListener<T extends keyof HTMLElementEventMap>(type: T, listener: (this: object, ev: HTMLElementEventMap[T] & NavigationEvent) => void, options?: boolean | EventListenerOptions | NavigationEventOptions): void;

  removeEventListener<T extends keyof HTMLElementEventMap>(type: T, listener: (this: object, ev: HTMLElementEventMap[T] & NavigationEvent) => void, options?: boolean | EventListenerOptions | NavigationEventOptions): void;
}
```
<!--more-->

## NavigationEvent {#NavigationEvent}
**NavigationEvent** -- базовый класс события навигации.
```js
export class NavigationEvent {
  isHandled?: boolean;
}
```

## NavigationEventOptions {#NavigationEventOptions}
**NavigationEventOptions** -- опции подписки на событие навигации.
```js
export class NavigationEventOptions implements EventListenerOptions {
   capture: boolean;
   priority: number | NavigationHandlerPriority;
   alwaysHandle: boolean;
   navigationTargetName?: string;
}
```

## NavigationHandlerPriority {#NavigationHandlerPriority}
**NavigationHandlerPriority** -- приоритет вызова обработчиков события навигации.\
Обработчики вызываются в порядке убывания приоритета: от `CustomExtensions` к `DefaultNavigation`.
```js
export enum NavigationHandlerPriority {
  DefaultNavigation = 0,
  GizmoHandlers = 20,
  EmbeddedExtensions = 40,
  CustomExtensions = 100
}
```
<!--more-->