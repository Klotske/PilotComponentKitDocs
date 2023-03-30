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
Источник DOM-событий для навигации с помощью мыши, тачпада и т.д. Подробнее: [INavigationEventSource](#INavigationEventSource).
```js
readonly canvasNavigationSource: INavigationEventSource;
```
Пример подписки на событие mousemove, используются [NavigationEventOptions](#NavigationEventOptions), заданные по умолчанию:
```js
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove);
//или
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove, false); //capture: false
//Те же опции, указанные явно:
navigationAgent.canvasNavigationSource.addEventListener("mousemove", onMouseMove, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, undefined));
//Для отписки от события, нужно передавать те же параметры, что и при подписке:
navigationAgent.canvasNavigationSource.removeEventListener("mousemove", onMouseMove, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, undefined));
```

#### keyboardNavigationSource
Источник DOM-событий для навигации с помощью клавиатуры. Подробнее: [INavigationEventSource](#INavigationEventSource).
```js
readonly keyboardNavigationSource: INavigationEventSource;
```
Пример подписки на событие `keyup`, используются [NavigationEventOptions](#NavigationEventOptions), заданные по умолчанию:
```js
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onMouseMove);
//или
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, {capture: false});
//Те же опции, указанные явно:
navigationAgent.keyboardNavigationSource.addEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
//Для отписки от события, нужно передавать те же параметры, что и при подписке:
navigationAgent.keyboardNavigationSource.removeEventListener("keyup", onKeyUp, new NavigationEventOptions(false, NavigationHandlerPriority.DefaultNavigation, false, 'desktopNavigation'));
```

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
  // Идентификатор подписчика на событие. Не обязательный параметр.
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