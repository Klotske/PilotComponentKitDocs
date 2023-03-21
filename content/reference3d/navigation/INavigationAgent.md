---
title: "INavigationAgent"
draft: false
weight: 9
---

## INavigationAgent {#INavigationAgent}
**INavigationAgent** -- интерфейс, позволяющий работать с источниками событий навигации.
```js
export interface INavigationAgent  {

  readonly canvasNavigationSource: INavigationEventSource;
  readonly keyboardNavigationSource: INavigationEventSource;

  getNavigationArea(): DOMRect;
}
```

### Поля
#### canvasNavigationSource
Источник DOM-событий для навигации с помощью мыши, тачпада и т.д. Смотри [INavigationEventSource](#INavigationEventSource).
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

#### keyboardNavigationSource
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
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, {capture: false});
```
Те же опции, указанные явно:
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
```

Для отписки от события, нужно передавать те же параметры, что и при подписке:
```js
navigationAgent.keyboardNavigationSource.removeEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
```
{{< /hint >}}

### Методы

#### getNavigationArea()
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
  // Задает и показывает было ли обработано событие.
  isHandled?: boolean;
}
```

## NavigationEventOptions {#NavigationEventOptions}
**NavigationEventOptions** -- опции подписки на событие навигации.
```js
export class NavigationEventOptions implements EventListenerOptions {
  // Перехват события при всплытии (false), иначе при погружении (true). По умолчанию: false.
  capture: boolean;
  // Приоритет вызова обработчиков: от наибольшего к наименьшему. По умолчанию: NavigationHandlerPriority.CustomExtensions.
  priority: number | NavigationHandlerPriority;
  // Перехват события, если событие уже было обработано ранее (true), иначе событие игнорируется (false). По умолчанию false.
  alwaysHandle: boolean;
  // (Опционально) идентификатор подписчика на событие.
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