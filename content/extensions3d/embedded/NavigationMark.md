---
title: "NavigationMarkExtension"
date: 2025-02-19
draft: false
---

**NavigationMarkExtension** -- расширение отображает точку, вокруг которой вращается камера.

Расширение имеет имя `PilotWeb3D.NavigationMark`.

Чтобы отключить загрузку этого расширения установите в настройках вьювера параметр `disabled` в `true` для этого модуля расширения.


```js
const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.NavigationMark': {
    disabled: true
  },
};
```