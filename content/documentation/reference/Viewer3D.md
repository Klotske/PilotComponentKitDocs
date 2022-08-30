---
title: "Viewer3D"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Viewer3D

Базовый класс для всех видов компонентов просмотра 3D моделей.

Этот класс содержит все, что нужно для отображения и взаимодействия с 3D моделями полученными из системы **Pilot-BIM**.

## Свойства

#### container
```js
container: HTMLElement;
```
HTML элемент, в котором создан компонент просмотра 3D моделей.

#### extensionsLoader
```js
extensionsLoader: ExtensionLoader;
```
Тип работы с расширениями. Подробнее смотри (ExtensionLoader)

#### events
```js
get events(): EventsDispatcher;
```
Свойство для управления событиями компонента.

#### model()
Получить консолидированную (общую) модель
```js
get model(): Model;
```

## Методы

#### start()
```js
 start(): number;
```
Метод инициализирует внутренние механизмы компонента.

#### finish()
```js
finish(): void;
```

Метод деинициализации внутренней логики компонента.

#### loadModelPart()
```js
loadModelPart(buffer, options, onSuccessCallback, onErrorCallback): void;
```
где:
  `buffer: ArrayBuffer` - массив байт модели,
  `options: any` - опции для загрузки части модели.
  `onSuccessCallback: SuccessCallback` - метод для обратного вызова в случае успешной загрузки части модели.
  `onErrorCallback: ErrorCallback` - метод для обратного вызова в случае неудачи загрузки части модели.

#### unloadModelPart()
```js
unloadModelPart(modelPart: string | ModelPart): void;
```
где:
  `modelPart` - идентификатор части модели или экземпляр части модели.

### getCameraPosition()
Получить текущее положение камеры
```js
getCameraPosition(): CameraPosition;
```

### setCameraPosition()
Задать позицию для камеры.
```js
setCameraPosition(cameraPosition: CameraPosition): void;
```
где:
`cameraPosition` - позиция камеры.

### makeScreenshot()
Сделать снимок сцены.
```js
makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>;
```
где:
`mimeType` - не облязательный параметр. Задает тип изображения (image/png, image/jpg и т.д.).
`quality` - качество снимка.

