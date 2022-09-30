---
title: "Viewer3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**Viewer3D** -- это базовый класс для всех видов компонентов работы с BIM-моделями.

Этот класс содержит всё необходимое для отображения и взаимодействия с моделями, полученными из системы **Pilot-BIM**.

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
Тип работы с расширениями. Подробнее смотри <a href="../ExtensionLoader/">ExtensionLoader</a>.

### events
```js
get events(): EventsDispatcher;
```
Свойство для управления событиями компонента.

### model
Получить консолидированную модель.
```js
get model(): Model;
```

## Методы

### start()
```js
 start(): number;
```
Метод инициализирует внутренние механизмы компонента.

### finish()
```js
finish(): void;
```
Метод деинициализирует внутренние механизмы компонента.

### loadModelPart()
```js
loadModelPart(buffer: ArrayBuffer, options: any, onSuccessCallback: SuccessCallback, onErrorCallback: ErrorCallback): void;
```
где:

  `buffer` -- массив байт модели,
  
  `options` -- опции для загрузки части модели,
  
  `onSuccessCallback` -- метод для обратного вызова в случае успешной загрузки части модели,
  
  `onErrorCallback` -- метод для обратного вызова в случае неудачи загрузки части модели.

#### unloadModelPart()
```js
unloadModelPart(modelPart: string | ModelPart): void;
```
где:
  `modelPart` -- идентификатор части модели или экземпляр части модели.

### getCameraPosition()
Метод позволяет получить текущее положение камеры.
```js
getCameraPosition(): CameraPosition;
```

### setCameraPosition()
Метод позволяет задать позицию камеры.
```js
setCameraPosition(cameraPosition: CameraPosition): void;
```
где:
`cameraPosition` - позиция камеры.

### makeScreenshot()
Метод позволяет сделать снимок сцены.
```js
makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>;
```
где:

`mimeType` -- не облязательный параметр. Задает тип изображения (image/png, image/jpg и т.д.).

`quality` -- качество снимка.

