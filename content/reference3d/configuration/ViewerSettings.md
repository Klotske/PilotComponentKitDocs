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
  [SettingsNames.ANTI_ALIASING]: true,
  [SettingsNames.HIDE_EDGES_WHEN_NAVIGATING]: true,
  [SettingsNames.DISPLAY_MODE]: DisplayMode.FACES_AND_EDGES,
  [SettingsNames.NAVIGATION_CUBE]: true
}
```