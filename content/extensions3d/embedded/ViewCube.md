---
title: "ViewCubeExtension"
date: 2025-02-19
draft: false
---

**ViewCubeExtension** -- расширение, которое отображает навигационный куб на сцене.

Расширение имеет имя `PilotWeb3D.ViewCube`.

Чтобы отключить загрузку этого расширения, установите в настройках просмотрщика параметр `disabled` в `true` для этого модуля расширения.


```js
const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.ViewCube': {
    disabled: true
  },
};
```