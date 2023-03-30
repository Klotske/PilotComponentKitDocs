---
title: "SettingsNames"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**SettingsNames** - список настроек для просмотрщика **PilotWeb3D**
Для задания настроек используейте класс <a href="../Viewer3DConfiguration">Viewer3DConfiguration</a>

```js
class SettingsNames {
  static TELEMETRY = "telemetry";
  static ANTI_ALIASING = "antiAliasing";
  static HIDE_EDGES_WHEN_NAVIGATING = "hideEdgesNavigation";
  static DISPLAY_MODE = "displayMode";
  static NAVIGATION_CUBE = "navigationCube";
}
```

### TELEMETRY
```js
static TELEMETRY = "telemetry"; 
```
Свойство указывающее отображать отладочную информацию в просмотрщике. Настройка может иметь занчения `true/false/undefined`

### ANTI_ALIASING
```js
static ANTI_ALIASING = "antiAliasing";
```
Свойство для настроек сглаживания 3D модели
Настройка может иметь занчения `true/false/undefined`

### HIDE_EDGES_WHEN_NAVIGATING
```js
static HIDE_EDGES_WHEN_NAVIGATING = "hideEdgesNavigation";
```
Свойство для указания настройки скрытия ребер при навигации по 3D модели
Настройка может иметь занчения `true/false/undefined`

### DISPLAY_MODE
```js
static DISPLAY_MODE = "displayMode";
```
Свойство для указания настройки отображение моделей в просмотрщике
Настройка может иметь занчения `DisplayMode.FACES_AND_EDGES` / `DisplayMode.FACES` или `undefined`. Подробнее: <a href="../../DisplayMode">DisplayMode</a>

### NAVIGATION_CUBE
```js
static NAVIGATION_CUBE = "navigationCube";
```
Свойство для указания настройки скрытия навигационного куба
Настройка может иметь занчения `true/false/undefined`