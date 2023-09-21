---
title: "GuiViewer3D"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 2
---

**GuiViewer3D** -- это класс для компонента просмотра 3D-моделей. Он расширяет возможности базового класса `Viewer3D` и содержит всё, 
что нужно для отображения и взаимодействия с 3D-моделями, полученными из системы **Pilot-BIM**.

## Свойства

### container
HTML-элемент, в котором создан компонент просмотра BIM-моделей.
```js
container: HTMLElement;
```

### extensionsLoader
Тип работы с расширениями. Подробнее: <a href="../ExtensionLoader">ExtensionLoader</a>.
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
где:\
  `buffer` -- массив байт модели,
  `options` -- опции для загрузки части модели,
  `onSuccessCallback` -- метод для обратного вызова в случае успешной загрузки части модели,
  `onErrorCallback` -- метод для обратного вызова в случае неуспешной загрузки части модели.

### unloadModelPart()
Метод для выгрузки части модели.
```js
unloadModelPart(modelPart: string | ModelPart): void;
```
где:\
  `modelPart` -- идентификатор части модели или экземпляр части модели.

### setVirtualOrigin()
Метод задаёт положение виртуального начала координат. Координаты объектов модели и положение камеры пересчитываются относительно нового начала координат.\
При изменении ВНК возникает событие `VIRTUAL_ORIGIN_CHANGED`. Подробнее: [Events3D](./Events/#Events3D).
```js
  setVirtualOrigin(point: Point3): void;
```
где:\
  `point` -- положение ВНК. Подробнее: [Point3](../../reference3d/navigation/Point3).

### setVirtualOrigin()
Метод возвращает положение виртуального начала координат. Подробнее: [Point3](../../reference3d/navigation/Point3).
```js
  setVirtualOrigin(point: Point3): void;
```

### getToolbar()
Метод получает объект для работы с панелью инструментов.
```js
getToolbar(): ViewerToolbar;
```

### makeScreenshot()
Метод, позволяющий сделать снимок сцены.
```js
makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>;
```
где:\
`mimeType` -- необязательный параметр. Задает тип изображения (image/png, image/jpg и т.д.).
`quality` -- качество снимка.

### getConfiguration()
Метод получает конфигурацию вьювера. Подробнее <a href="../configuration/Viewer3DConfiguration">Viewer3DConfiguration</a>.

```js
getConfiguration(): Viewer3DConfiguration;
```