---
title: "SetPivotPositionExtension"
draft: false
---

**SetPivotPositionExtension** -- пример расширения, которое показывает возможности работы с опорной точкой камеры.
Расширение имеет имя `SetPivotPositionExtensionSample`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/samples/SetPivotPositionExtension/SetPivotPositionExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("SetPivotPositionExtensionSample");
```