---
title: "Viewer2D"
date: 2022-11-29T14:44:03+03:00
draft: false
weight: 8
---

**Viewer2D** -- это базовый класс для работы с документами компонента **PilotWeb2D**.

Этот класс содержит всё необходимое для отображения и взаимодействия с документами, полученными из системы **Pilot**.

## Свойства

### container
HTML элемент, в котором создан компонент просмотра 3D моделей.
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
get events(): EventsDispatcher;
```

## Методы

### start()
Метод инициализирует внутренние механизмы компонента.
```js
 start(): Promise<number>;
```

### finish()
Метод деинициализирует внутренние механизмы компонента.
```js
await finish(): Promise<void>;
```

### loadDocument()
Метод загружает документ в компонент.
```js
loadDocument(data: ArrayBuffer | string, options: DocumentLoadingOption): Promise<void>; 
```
где:\
  `data` - массив байт документа или ссылка на документ.\
  `options` - опции для загрузки документа (подробнее: <a href="../DocumentLoadingOptions/">DocumentLoadingOptions</a>).

### unloadDocument(){#unloadDocument}
Выгружает документ из компонента.
```js
unloadDocument(): void 
```

### getConfiguration()
Получает текущие настройки просмотрщика. Подробнее: <a href="/reference2d/configuration/ViewerConfiguration">ViewerConfiguration</a>.
```js
getConfiguration(): ViewerConfiguration
```
