---
title: "Viewer3D"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 8
---

**Viewer3D** -- это базовый класс для всех видов компонентов работы с BIM-моделями.

Этот класс содержит всё необходимое для отображения и взаимодействия с моделями, полученными из системы **Pilot-BIM**.

## Свойства

### container
HTML элемент, в котором создан компонент просмотра 3D-моделей.
```js
container: HTMLElement;
```

### extensionsLoader
Тип работы с расширениями. Подробнее: <a href="../ExtensionLoader/">ExtensionLoader</a>.
```js
extensionsLoader: ExtensionLoader;
```

### events
Свойство для управления событиями компонента.
```js
get events(): IEventsDispatcher;
```

### model
Свойство для получения консолидированной модели.
```js
get model(): Model;
```

### navigation
Свойство для получения объекта управления навигацией по модели.
```js
get navigation(): INavigation;
```
Подробнее: <a href="../navigation/INavigation">INavigation</a>


## Методы

### start()
Метод инициализирует внутренние механизмы компонента.
```js
 start(): Promise<number>;
```

### finish()
Метод деинициализирует внутренние механизмы компонента.
```js
finish(): void;
```

### loadModelPart()
Метод для управления загрузкой частей модели.
```js
loadModelPart(buffer: ArrayBuffer, options: any, onSuccessCallback: SuccessCallback, onErrorCallback: ErrorCallback): void;
```
где:

  `buffer` -- массив байт модели,
  
  `options` -- опции для загрузки части модели,
  
  `onSuccessCallback` -- метод для обратного вызова в случае успешной загрузки части модели,
  
  `onErrorCallback` -- метод для обратного вызова в случае неудачи загрузки части модели.

### unloadModelPart()
Метод для выгрузки части модели.
```js
unloadModelPart(modelPart: string | ModelPart): void;
```
где:
  `modelPart` -- идентификатор части модели или экземпляр части модели.

### makeScreenshot()
Метод позволяет сделать снимок сцены.
```js
makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>;
```
где:

`mimeType` -- необязательный параметр. Задает тип изображения (image/png, image/jpg и т.д.).
`quality` -- качество снимка.