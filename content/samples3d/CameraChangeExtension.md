---
title: "CameraChangeExtension"
draft: false
---

**CameraChangeExtension** -- пример расширения, которое обрабатывает события перемещения камеры.
Расширение имеет имя `CameraChangeExtensionSample`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/samples/CameraChangeExtension/CameraChangeExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("CameraChangeExtensionSample");
```