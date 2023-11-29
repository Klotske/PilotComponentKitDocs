---
title: "RemarksUIExtension"
draft: false
weight: 1
---

**RemarksUIExtension** -- пример расширения, которое использует API расширения [RemarksExtension](../../extensions2d/RemarkExtension) для добавления и редактирования точек замечаний на сцене.
Расширение имеет имя `RemarksUIExtensionSample`.

Пример подключения в `html`:
```html
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/23.0.10/samples/RemarksUIExtension2D/RemarksUIExtension.css">
<script src="https://pilotcloud.ascon.net/components/23.0.10/samples/RemarksUIExtension2D/RemarksUIExtension.js"></script>
```

Пример подключения в `javascript`:
```js
const htmlDiv = document.getElementById('pilotViewer');
const configuration = new PilotWeb2D.Viewer2DConfiguration();
const viewer = PilotWeb2D.CreateViewer(htmlDiv, configuration);
await viewer.start();
await viewer.extensionsLoader.loadExtension("Remarks2D.UIExtensionSample");
```