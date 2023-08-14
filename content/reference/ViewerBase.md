---
title: "ViewerBase"
date: 2023-08-14T12:35:00+03:00
draft: false
---

**ViewerBase** -- базовый класс вьювера предоставляет API методы общие для вьюверов. Наследники <a href="../../../reference2d/Viewer2D">Viewer2D</a>, <a href="../../../reference3d/Viewer3D">Viewer3D</a>.

## Свойства

### container
```js
readonly container: HTMLElement;
```
HTML элемент хранящий вьювер.

### extensionsLoader
```js
readonly extensionsLoader: ExtensionLoader;
```
Объект управления расширениями.

### settings
```js
abstract settings: ISettings;
```
Объект управления настройками клиента. Подробнее: [ISettings](../SettingsBase).

### events
```js
abstract events: IEventsDispatcher;
```
Объект управления событиями вьювера. Подробнее: [IEventsDispatcher](../EventsDispatcher).

### rootContainer  {#rootContainer}
Получает контейнер-обёртку вьювера.
```js
get rootContainer(): HTMLElement;
```

## Методы

### getConfiguration()
Получает конфигурацию вьювера. Подробнее: [ViewerConfiguration](../ViewerConfiguration).
```js
getConfiguration(): ViewerConfiguration;
```

### finish()
Выгружает все расширения вьювера.
```js
finish(): void;
```

### setThemeFromSettings()
Устанавливает тему вьювера и его компонентов из настроек Подробнее: [ISettings](../SettingsBase). Если настройки не установлены берётся переданная в конструкторе конфигурация, если конфигурация не задана берутся значения по умолчанию
```js
protected setThemeFromSettings(): void;
```