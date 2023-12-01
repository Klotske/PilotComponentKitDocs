---
title: "RemarksUIExtension"
draft: false
---

**RemarksUIExtension** -- пример расширения, которое использует API расширения [RemarksExtension](../../extensions3d/RemarkExtension) для добавления и редактирования точек замечаний на сцене.
Расширение имеет имя `RemarksUIExtensionSample`.

Пример подключения в `html`:
```html
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/samples/RemarksUIExtension/RemarksUIExtension.css">
<script src="https://pilotcloud.ascon.net/components/@VERSION@/samples/RemarksUIExtension/RemarksUIExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
await viewer.extensionsLoader.loadExtension("RemarksUIExtensionSample");
```