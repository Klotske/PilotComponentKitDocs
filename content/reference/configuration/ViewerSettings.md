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
  [SettingNames.TELEMETRY] : false,
  [SettingNames.ANTI_ALIASING]: true,
  [SettingNames.HIDE_EDGES_WHEN_NAVIGATING]: true,
  [SettingNames.DISPLAY_MODE]: DisplayMode.FACES_AND_EDGES,
  [SettingNames.NAVIGATION_CUBE]: true
}
```