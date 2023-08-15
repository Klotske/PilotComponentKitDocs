---
title: "ViewerConfiguration"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**ViewerConfiguration** - Базовый класс, описывающий настройки компонентов **PilotWeb2D** и **PilotWeb3D**.

```js
class ViewerConfiguration {
  appearance: ViewerSettings = {
    [BaseSettingsNames.TOOLBAR] : {
      direction: ToolbarDirection.TOP_FLUENT,
      content: ToolbarContent.CENTER
    } as ToolbarStyle,
    [BaseSettingsNames.THEME] : SettingsTheme.LIGHT_THEME;
  };
}
```

## Свойства

### appearance
```js
appearance: ViewerSettings;
```
Параметры внешнего вида вьювера.  Подробнее: [ViewerSettings](#ViewerSettings).

### direction
```js
direction: string;
```
Управляет положением панели инструментов. Подробнее: [ToolbarDirection](#ToolbarDirection).


### content
```js
content: string;
```
Управляет расположением кнопок на панели инструментов. Подробнее: [ToolbarContent](#ToolbarContent).

### theme
```js
theme: string;
```
Управляет темой вьювера и его компонентов. Подробнее: [SettingsTheme](#SettingsTheme).


### settingsPrefix
```js
settingsPrefix: string;
```
Задает префикс для настроек, хранящихся в браузере клиента.

## ToolbarDirection {#ToolbarDirection}
**ToolbarDirection**  - возможные позиции панели инструментов.
```js
export enum ToolbarDirection {
  TOP_FIXED = 'ascn-toolbar-fixed-top', // Фиксированный сверху
  TOP_FLUENT = 'ascn-toolbar-top', // Не фиксированный сверху
  BOTTOM_FIXED = 'ascn-toolbar-fixed-bottom', // Фиксированный снизу
  BOTTOM_FLUENT = 'ascn-toolbar-bottom', // Не фиксированный снизу
}
```

## ToolbarContent {#ToolbarContent}
**ToolbarContent**  - возможные позиции содержимого в панели инструментов.
```js
export enum ToolbarContent {
  CENTER = 'ascn-toolbar-content-center', // По центру
  START = 'ascn-toolbar-content-start', // Прижато к левому краю
  END = 'ascn-toolbar-content-end' // Прижато к правому краю
}
```
## SettingsTheme {#SettingsTheme}
**SettingsTheme**  - возможные варианты темы вьювера.
```js
export enum SettingsTheme {
  LIGHT_THEME = 'ascn-light', // Тёмная тема
  DARK_THEME = 'ascn-dark', // Светлая тема
}
```

## ViewerSettings {#ViewerSettings}
**ViewerSettings**  - настройки, ключами свойств которого являются строки, а значениями свойств является любой тип.
```js
type ViewerSettings = Record<string, any>;
```

