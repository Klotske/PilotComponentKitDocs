---
title: "GuiViewer3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

**GuiViewer3D** -- это класс для компонента просмотра 3D моделей. Он расширяет возможности базового класса `Viewer3D` и содержит все, 
что нужно для отображения и взаимодействия с 3D моделями полученными из системы **Pilot-BIM**.

## Свойства

### container
```js
container: HTMLElement;
```
HTML элемент, в котором создан компонент просмотра BIM-моделей.

### extensionsLoader
```js
extensionsLoader: ExtensionLoader;
```
Тип работы с расширениями. Подробнее смотри (ExtensionLoader).

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
 start(): Promise<number>;
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

### unloadModelPart()
```js
unloadModelPart(modelPart: string | ModelPart): void;
```
где:
  `modelPart` -- идентификатор части модели или экземпляр части модели.

### getToolbar()
Метод для получения экземпляра типа работы с панелью инструментов.
```js
getToolbar(): ViewerToolbar;
```

### getCameraPosition()
Метод для получения текущего положения камеры.
```js
getCameraPosition(): CameraPosition;
```

### setCameraPosition()
Метод, позволяющий задать позицию камеры.
```js
setCameraPosition(params: CameraPosition): void;
```
где:
`params` -- параметры камеры.

### makeScreenshot()
Метод, позволяющий сделать снимок сцены.
```js
makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>;
```
где:
`mimeType` -- не обязательный параметр. Задает тип изображения (image/png, image/jpg и т.д.).

`quality` -- качество снимка.

