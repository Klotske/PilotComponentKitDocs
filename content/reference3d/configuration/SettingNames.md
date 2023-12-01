---
title: "SettingsNames"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**SettingsNames** -- список настроек для просмотрщика **PilotWeb3D**.\
Для задания настроек используейте класс <a href="../Viewer3DConfiguration/">Viewer3DConfiguration</a>.

```js
class SettingsNames {
  static TELEMETRY = "telemetry";
  static ANTI_ALIASING = "antiAliasing";
  static HIDE_EDGES_WHEN_NAVIGATING = "hideEdgesWhenNavigation";
  static DISPLAY_MODE = "displayMode";
  static NAVIGATION_CUBE = "navigationCube";
}
```

### TELEMETRY
Свойство для отображения отладочную информацию в просмотрщике. Настройка может иметь значения `true/false/undefined`.

```js
static TELEMETRY = "telemetry"; 
```

### ANTI_ALIASING
Свойство для настроек сглаживания 3D модели.
Настройка может иметь значения `true/false/undefined`.

```js
static ANTI_ALIASING = "antiAliasing";
```

### HIDE_EDGES_WHEN_NAVIGATING
Свойство для указания настройки скрытия ребер при навигации по 3D модели.
Настройка может иметь занчения `true/false/undefined`.

```js
static HIDE_EDGES_WHEN_NAVIGATING = "hideEdgesWhenNavigation";
```

### DISPLAY_MODE
Свойство для указания настройки отображения моделей в просмотрщике.
Настройка может иметь значения `DisplayMode.FACES_AND_EDGES` / `DisplayMode.FACES` или `undefined`. Подробнее: <a href="../../DisplayMode">DisplayMode</a>.

```js
static DISPLAY_MODE = "displayMode";
```

### NAVIGATION_CUBE
Свойство для указания настройки скрытия навигационного куба.
Настройка может иметь занчения `true/false/undefined`.

```js
static NAVIGATION_CUBE = "navigationCube";
```
