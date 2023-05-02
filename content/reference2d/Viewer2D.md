---
title: "Viewer2D"
date: 2022-11-29T14:44:03+03:00
draft: false
weight: 8
---

**Viewer2D** -- это базовый класс для всех видов компонентов работы с документами.

Этот класс содержит всё необходимое для отображения и взаимодействия с документами, полученными из системы **Pilot**.

## Свойства

### container
```js
container: HTMLElement;
```
HTML элемент, в котором создан компонент просмотра 3D моделей.

### extensionsLoader
```js
extensionsLoader: ExtensionLoader;
```
Тип работы с расширениями. Подробнее: <a href="../ExtensionLoader/">ExtensionLoader</a>.

### events
```js
get events(): EventsDispatcher;
```
Свойство для управления событиями компонента.

## Методы

### start()
```js
 start(): Promise<number>;
```
Метод инициализирует внутренние механизмы компонента.

### finish()
```js
finish(): void;
```
Метод деинициализирует внутренние механизмы компонента.

### loadDocument()
```js
loadDocument(buffer: ArrayBuffer, options: {}, onSuccessCallback: SuccessCallback, onErrorCallback: ErrorCallback): void 
```
где:
  `buffer` -- массив байт документа,
  `options` -- опции для загрузки документа,
  `onSuccessCallback` -- метод для обратного вызова в случае успешной загрузки документа,
  `onErrorCallback` -- метод для обратного вызова в случае неудачи загрузки документа.

### unloadDocument()
```js
unloadDocument(): void 
```
Выгружает документ из компонента.
