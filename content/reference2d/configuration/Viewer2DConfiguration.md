---
title: "Viewer2DConfiguration"
date: 2023-05-04T14:44:03+03:00
draft: false
---

**Viewer2DConfiguration** - класс описывающий настройки компонента **PilotWeb2D**. Этот класс наследуется от базового класса настроек <a href="../ViewerConfiguration">ViewerConfiguration</a> 

```js
class Viewer2DConfiguration extends ViewerConfiguration {
  settings?: ViewerSettings;
}
```

## Свойства

### settings
```js
settings?: ViewerSettings;
```
Необязательное поле для задания настроек отображения просмотрщика 2D документов. Подробнее: <a href="../ViewerSettings">ViewerSettings</a> 
