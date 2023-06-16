---
title: "ViewerConfiguration"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**ViewerConfiguration** - Базовый класс описывающий настройки компонентов **PilotWeb2D** и **PilotWeb3D**.

```js
class ViewerConfiguration {
  appearance: ViewerSettings = {
    [BaseSettingsNames.TOOLBAR] : {
      direction: ToolbarDirection.TOP_FLUENT,
      content: ToolbarContent.CENTER
    } as ToolbarStyle
  };
}
```

## Свойства

### appearance
```js
appearance: ViewerSettings;
```
Свойство для изменения внешнего вида просмотрщика.

### direction
```js
direction: string;
```
Управляет положение панели инструментов.

```js
export enum ToolbarDirection {
  TOP_FIXED = 'ascn-toolbar-fixed-top',
  TOP_FLUENT = 'ascn-toolbar-top',
  BOTTOM_FIXED = 'ascn-toolbar-fixed-bottom',
  BOTTOM_FLUENT = 'ascn-toolbar-bottom',
}
```


### content
```js
content: string;
```
Управляет расположением кнопок на панели инструментов.

```js
export enum ToolbarContent {
  CENTER = 'ascn-toolbar-content-center',
  START = 'ascn-toolbar-content-start',
  END = 'ascn-toolbar-content-end'
}
```



