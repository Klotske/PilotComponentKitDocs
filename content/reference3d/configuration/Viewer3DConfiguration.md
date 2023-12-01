---
title: "Viewer3DConfiguration"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**Viewer3DConfiguration** -- класс, описывающий настройки компонента **PilotWeb3D**. Этот класс наследуется от базового класса настроек <a href="../ViewerConfiguration">ViewerConfiguration</a>. 

```js
class Viewer3DConfiguration extends ViewerConfiguration {
  settings?: ViewerSettings;
}
```

## Свойства

### settings
Необязательное поле для задания настроек отображения просмотрщика 3D моделей. Подробнее: <a href="../ViewerSettings">ViewerSettings</a>.

```js
settings?: ViewerSettings;
```

