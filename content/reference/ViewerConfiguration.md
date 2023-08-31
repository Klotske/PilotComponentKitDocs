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
      content: ToolbarContentAlignment.CENTER
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
Управляет расположением кнопок на панели инструментов. Подробнее: [ToolbarContentAlignment](#ToolbarContentAlignment).

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

## Методы

### mergeConfigurationAndSettings()
Метод объединяет переданную конфигурацию и настройки, заменяя значения из конфигурации значениями из настроек.
```js
public mergeConfigurationAndSettings(configuration: ViewerSettings, settings: ISettings): void;
```
где:

`configuration` -- конфигурация. Подробнее: [ViewerSettings](#ViewerSettings).\
`settings` -- значение настройки. Подробнее: [ISettings](../ISettings).

### createConfiguration()
Метод объединяет объединяет свойства из переданных параметров в объект origin. Origin подменяется свойствами из configuration, если configuration не был передан или был передан пустой объект, то configuration присваивается origin по ссылке.
```js
public createConfiguration(configuration: ViewerSettings, origin: ViewerSettings): void;
```
где:

`configuration` -- конфигурация. Подробнее: [ViewerSettings](#ViewerSettings).\
`origin` -- значение настройки. Подробнее: [ViewerSettings](#ViewerSettings).

### changeTheme()
Метод меняет тему вьювера.
```js
public changeTheme(newTheme: string): void;
```
где:

`newTheme` -- значение новой темы из SettingsTheme. Подробнее: [SettingsTheme](#SettingsTheme).

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

## ToolbarContentAlignment {#ToolbarContentAlignment}
**ToolbarContentAlignment**  - возможные позиции содержимого в панели инструментов.
```js
export enum ToolbarContentAlignment {
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

