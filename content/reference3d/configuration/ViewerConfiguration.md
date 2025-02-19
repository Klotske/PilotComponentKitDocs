---
title: "ViewerConfiguration"
date: 2022-12-04T14:44:03+03:00
draft: false
---

**ViewerConfiguration** -- базовый класс, описывающий настройки компонентов **PilotWeb2D** и **PilotWeb3D**.

```js
class ViewerConfiguration {
  settingsPrefix: string;
  appearance: ViewerSettings = {
    [BaseSettingsNames.TOOLBAR] : {
      direction: ToolbarDirection.TOP_FLUENT,
      content: ToolbarContentAlignment.CENTER
    } as ToolbarStyle
  };
  extensionsOptions: Array<{ name: string, options: ViewerSettings }>;
}
```

## Свойства

### appearance
Свойство для изменения внешнего вида просмотрщика.

```js
appearance: ViewerSettings;
```

### direction
Свойство управляет положением панели инструментов.

```js
direction: string;
```

```js
export enum ToolbarDirection {
  TOP_FIXED = 'ascn-toolbar-fixed-top',
  TOP_FLUENT = 'ascn-toolbar-top',
  BOTTOM_FIXED = 'ascn-toolbar-fixed-bottom',
  BOTTOM_FLUENT = 'ascn-toolbar-bottom',
}
```

### content
Свойство управляет расположением кнопок на панели инструментов.

```js
content: string;
```

```js
export enum ToolbarContentAlignment {
  CENTER = 'ascn-toolbar-content-center',
  START = 'ascn-toolbar-content-start',
  END = 'ascn-toolbar-content-end'
}
```


### settingsPrefix
Свойство задает префикс для настроек, хранящихся в браузере клиента.

```js
settingsPrefix: string;
```

### extensionsOptions
С помощью этого свойства можно передать расширениям начальные настройки. Также для встроенных расширений есть возможность указать настройку - не загружать встроенное расширение.

```js
extensionsOptions: Array<{ name: string, options: ViewerSettings }>;
```

пример задания настройки отключения загрузки для встроенного расширения PilotWeb3D.ViewCube:

```js

const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.ViewCube': {
    disabled: true
  },
}
const htmlDiv = document.getElementById("viewer");
this._viewer = PilotWeb3D.CreateViewer(htmlDiv, configuration);
await this._viewer.start();
...

```





