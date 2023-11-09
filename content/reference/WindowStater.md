---
title: "WindowStater"
date: 2023-07-03T13:19:03+03:00
draft: false
---

**WindowStater** -- класс для хранения состояния диалогового окна.

## IWindowStyle {#IWindowStyle}
**IWindowStyle** -- интерфейс, хранящий свойства стилей диалогового окна. 

```js
export interface IWindowStyle {
  // Свойство, хранящее ширину окна
  width: string,
  // Свойство, хранящее высоту окна
  height: string,
  // Свойство, хранящее координату по горизонтали относительно левого края окна
  left: string,
  // Свойство, хранящее координату по горизонтали относительно правого края окна
  right: string,
  // Свойство, хранящее координату по вертикали
  top: string
}
```

## IWindowStateOptions {#IWindowStateOptions}
**IWindowStateOptions** -- интерфейс, хранящий свойства для работы ресайза и перетаскивания диалогового окна. 

```js
export interface IWindowStateOptions {
  // Ключ по которому будут сохранены настройки для восстановления при последующем открытии окна
  saveKey: string;
  // Свойство, которое обозначает надо ли устанавливать окну сохранённые настройки размера при последующем открытии
  restoreWindowSize: boolean;
  // Свойство, которое обозначает надо ли устанавливать окну сохранённые настройки позиции при последующем открытии
  restoreWindowPosition: boolean;
}
```

## Конструктор
```js
  constructor(savedStateOptions: IWindowStateOptions, containerToRestore: HTMLElement);
```
где:\
`savedStateOptions`-- объект для хранения свойств работы с окном.\
`containerToRestore` -- HTML элемент с которым происходит сохранение/восстановление настроек (css стилей). Подробнее: [IWindowStyle](#IWindowStyle).

## Свойства

### windowStylesState  {#windowStylesState}
Получает сохранённые стили окна, если был установлен saveKey.
```js
get windowStylesState(): IWindowStyle;
```

### windowOptionsState  {#windowOptionsState}
Получает настройки, установленные окну.
```js
get windowOptionsState(): IWindowStateOptions;
```

## Методы

### restore()
Восстанавливает положение окна и его ширину/высоту исходя из IWindowStyle.
```js
restore(): void
```

### saveWindowState()
Сохраняет стили окна в localStorage, если был передан saveKey из IWindowStateOptions.
```js
saveWindowState(): void
```