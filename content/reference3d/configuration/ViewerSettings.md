---
title: "ViewerSettings"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**ViewerSettings** - класс описывающий настройки просмотрщика компонента **PilotWeb3D**.

```js
type ViewerSettings = Record<string, any>;
```

### Настройки просмотрщика по умолчанию

Компонент имеет следующие настройки установленные по умолчанию:

```js
const defaultViewer3DSettings: ViewerSettings = {
  [SettingsNames.TELEMETRY] : false,
  [SettingsNames.AXES] : true,
  [SettingsNames.CAMERA_ANIMATION]: true,
  [SettingsNames.HIDE_SMALL_ELEMENTS_WHEN_NAVIGATING]: false,
  [SettingsNames.GLOBAL_LIGHT]: true,
  [SettingsNames.LIGHT_SOURCE]: true,
  [SettingsNames.ANTI_ALIASING]: true,
  [SettingsNames.HIDE_SMALL_ELEMENTS_MOVING]: false,
  [SettingsNames.SMALL_ELEMENT_SIZE]: 10,
  [SettingsNames.LABEL_LINE_LENGTH]: 1000,
  [SettingsNames.HIDE_EDGES_WHEN_NAVIGATING]: true,
  [SettingsNames.DISPLAY_MODE]: DisplayMode.FACES_AND_EDGES,
  [SettingsNames.NAVIGATION_CUBE]: true
}
```