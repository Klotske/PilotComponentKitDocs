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

  get isActive(): boolean;
  set isActive(value: boolean);

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

### Свойства

#### isActive()
Свойство определяет активность агента навигации.
```js
  get isActive(): boolean;
  set isActive(value: boolean);
```

### Методы

#### getNavigationArea()
Метод позволяет получить прямоугольник текущей рабочей области навигации.
```js
getNavigationArea(): DOMRect;
```
Возвращает объект [DOMRect](https://developer.mozilla.org/en-US/docs/Web/API/DOMRect).

{{< hint type="important" icon=gdoc_error_outline title="Важно">}}
В десктопной реализации навигации, при перемещении курсора за пределы рабочей области навигации происходит деактивация источника событий клавиатуры. При возвращении курсора в рабочую область происходит активация источника событий клавиатуры.\
Таким образом, события клавиатуры не генерируются если курсор находится за пределами рабочей области.
{{< /hint >}}


## INavigationEventSource {#INavigationEventSource}
**INavigationEventSource** -- интерфейс источника событий навигации.
```js
export interface INavigationEventSource {
  // Свойство определяет активность источника событий навигации.
  get isActive(): boolean;
  set isActive(value: boolean);

  addEventListener<T extends keyof NavigationEventSourceEventMap>(type: T, listener: (this: object, ev: NavigationEventSourceEventMap[T] & NavigationEvent) => void, options?: boolean | EventListenerOptions | NavigationEventOptions): void;

  removeEventListener<T extends keyof NavigationEventSourceEventMap>(type: T, listener: (this: object, ev: NavigationEventSourceEventMap[T] & NavigationEvent) => void, options?: boolean | EventListenerOptions | NavigationEventOptions): void;
}
```

## NavigationEventSourceEventMap
**NavigationEventSourceEventMap** -- события, генерируемые источником событий навигации.\
Расширяет `HTMLElementEventMap` -- список встроенных DOM событий.
```js
export interface NavigationEventSourceEventMap extends HTMLElementEventMap {
  `active`: ActiveEvent
}
```
где:\
`active` -- событие возникающее при изменении активности данного источника событий навигации. Подробнее: [ActiveEvent](#ActiveEvent).

## ActiveEvent {#ActiveEvent}
Представляет событие, которое происходит при изменении активности источника событий навигации.\
Расширяет `Event`.
```js
export interface ActiveEvent extends Event {
  // Активность источника событий навигации.
  readonly isActive: boolean
}
```

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
  // Идентификатор подписчика на событие. Необязательный параметр.
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