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
  static CAMERA_MODE = "cameraMode";
  static NAVIGATION_CUBE = "navigationCube";
  static HIDE_SMALL_ELEMENTS = "hideSmallElements";
  static SMALL_ELEMENT_SIZE = "smallElementSize";
}
```

### TELEMETRY
Свойство для отображения отладочной информации в просмотрщике. Настройка может иметь значения `true/false/undefined`.

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
Настройка может иметь значения `true/false/undefined`.

```js
static HIDE_EDGES_WHEN_NAVIGATING = "hideEdgesWhenNavigation";
```

### DISPLAY_MODE
Свойство для указания настройки отображения моделей в просмотрщике.
Настройка может иметь значения `DisplayMode.FACES_AND_EDGES` / `DisplayMode.FACES` или `undefined`. Подробнее: [DisplayMode](../../DisplayMode).

```js
static DISPLAY_MODE = "displayMode";
```

### CAMERA_MODE
Свойство для указания настройки типа проекции камеры в просмотрщике.
Настройка может иметь значения `CAMERA_MODE.ORTHOGRAPHIC` / `CAMERA_MODE.PERSPECTIVE` или `undefined`. Подробнее: [CAMERA_MODE](../../navigation/CameraNavigationMode#CameraMode).

```js
static CAMERA_MODE = "cameraMode";
```

### NAVIGATION_CUBE
Свойство для указания настройки скрытия навигационного куба.
Настройка может иметь значения `true/false/undefined`.

```js
static NAVIGATION_CUBE = "navigationCube";
```

### HIDE_SMALL_ELEMENTS
Свойство для указания настройки скрытия маленьких объектов.
Настройка может иметь значения `true/false/undefined`.
```js
static HIDE_SMALL_ELEMENTS = "hideSmallElements";
```

### SMALL_ELEMENT_SIZE
Свойство для указания размера скрываемых объектов в пикселях.
Настройка может иметь числовое значение или `undefined`.
```js
static SMALL_ELEMENT_SIZE = "smallElementSize";
```